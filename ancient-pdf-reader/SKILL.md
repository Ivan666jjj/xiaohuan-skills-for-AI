---
name: ancient-pdf-reader
description: 古籍 PDF 阅读器：自动判断文字/扫描版，繁体/竖排/生僻字 OCR，分块展示，任意对话可用
---

# 古籍 PDF 阅读器（全局）

专门处理汉语言文学专业需要的 PDF —— 古籍扫描、繁体竖排、生僻字、文字课件。无论 PDF 是文字型还是图片型，自动选择最佳提取方案。

## 触发条件（任意对话中均可调用）
- 用户拖入/提到 PDF 文件路径
- 用户说"读一下这个 PDF""扫这个""识别这个"
- 用户发来截图/图片需要识别文字
- 任何涉及 PDF 或图片文字提取的需求

**调用方式：** `/ancient-pdf-reader <任务描述>`

## 核心引擎

| 引擎 | 位置 | 用途 |
|------|------|------|
| PyMuPDF (fitz) | `/tmp/pdfenv/bin/python3` | 文字型 PDF 秒级提取 |
| macOS Vision OCR | `~/Library/Application Support/reasonix/global-workspace/ocr_helper` | 图片/扫描件 OCR（M4 加速，支持繁简中文、竖排） |
| RapidOCR | `~/.reasonix/packages/` | 备用 OCR（支持生僻字） |

## 工作流程

### Step 1: 检测 PDF 类型
```bash
/tmp/pdfenv/bin/python3 -c "
import fitz
doc = fitz.open('<PDF_PATH>')
chars = sum(len(page.get_text('text', sort=True).strip()) for page in doc[:3])
print(f'页数:{doc.page_count} 前3页字符:{chars} 类型:{\"文字版\" if chars > 200 else \"扫描版\"}')"
doc.close()
"
```

### Step 2a: 文字型 PDF → 直接提取
```bash
/tmp/pdfenv/bin/python3 -c "
import fitz, os
doc = fitz.open('<PDF_PATH>')
outdir = '/tmp/pdfchunks'; os.makedirs(outdir, exist_ok=True)
chunk, idx, size = '', 0, 6000
for i in range(doc.page_count):
    text = doc[i].get_text('text', sort=True)
    chunk += f'\n---第{i+1}页---\n{text}'
    while len(chunk) >= size:
        with open(f'{outdir}/c{idx:04d}.txt','w') as f: f.write(chunk[:size])
        chunk = chunk[size:]; idx += 1
if chunk:
    with open(f'{outdir}/c{idx:04d}.txt','w') as f: f.write(chunk); idx += 1
print(f'{idx}个块 → {outdir}')
doc.close()
"
```
然后用 `read_file` 逐块读取回答用户。

### Step 2b: 扫描版 PDF → OCR 提取
```bash
/tmp/pdfenv/bin/python3 -c "
import fitz, os, subprocess
doc = fitz.open('<PDF_PATH>')
ocr = os.path.expanduser('~/Library/Application Support/reasonix/global-workspace/ocr_helper')
outdir = '/tmp/pdfocr'; os.makedirs(outdir, exist_ok=True)
for i in range(doc.page_count):
    pix = doc[i].get_pixmap(dpi=250)
    img = f'{outdir}/p{i:04d}.png'; pix.save(img)
    r = subprocess.run([ocr, img], capture_output=True, text=True, timeout=60)
    with open(f'{outdir}/p{i:04d}.txt','w') as f: f.write(r.stdout)
    print(f'OCR: {i+1}/{doc.page_count}')
doc.close()
print(f'完成 → {outdir}')
"
```

### Step 3: 图片直接 OCR
用户发来截图/图片时：
```bash
~/Library/Application\ Support/reasonix/global-workspace/ocr_helper '<IMAGE_PATH>'
```

## 重要规则

1. **永远不要用 read_file 直接读 PDF 或图片**——它们是二进制格式
2. **自动判断类型**：文字版用 PyMuPDF，扫描版/图片用 Vision OCR
3. **古文优化**：OCR 设 `dpi=300`，识别语言包含繁简中文
4. **分块输出**：大文件自动切成 6000 字/块，用完 read_file 逐块读
5. **优先看目录**：如果 PDF 有大纲/目录，先展示给用户
6. **繁体竖排**：Vision OCR 原生支持竖排文字识别
7. **生僻字**：如果 Vision OCR 识别不准，尝试 RapidOCR 备用引擎

## 辅助功能
- `pymupdf4llm.to_markdown()` → 提取为 Markdown（保留表格）
- `page.get_images()` → 提取嵌入图片
- `page.find_tables()` → 提取表格数据
- 合并分块：`cat /tmp/pdfocr/p*.txt > /tmp/full.txt`
