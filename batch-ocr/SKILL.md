---
name: batch-ocr
description: 批量扫描文件夹PDF/图片，自动OCR输出到小焕的资料
---

# 批量 OCR 处理器

批量扫描整个文件夹的 PDF/图片，全部转文字，输出到小焕的资料目录。

## 触发
`/batch-ocr <文件夹路径> [--type pdf|image|all]`

## 工作流程

### Step 1: 扫描文件夹
```bash
/tmp/pdfenv/bin/python3 -c "
import os, sys
folder = '<文件夹路径>'
files = []
for f in os.listdir(folder):
    ext = f.lower().split('.')[-1]
    if ext in ['pdf', 'png', 'jpg', 'jpeg', 'gif', 'bmp']:
        files.append(f)
print(f'找到 {len(files)} 个文件:')
for f in files:
    print(f'  {f}')
"
```

### Step 2: 逐文件处理
对每个文件自动判断类型：

**PDF**：
```bash
/tmp/pdfenv/bin/python3 -c "
import fitz, os, subprocess
doc = fitz.open('<FILE>')
ocr = os.path.expanduser('~/Library/Application Support/reasonix/global-workspace/ocr_helper')
outdir = os.path.expanduser('~/Desktop/小焕的资料/OCR输出')
os.makedirs(outdir, exist_ok=True)
name = os.path.splitext(os.path.basename('<FILE>'))[0]
# 判断类型
chars = sum(len(page.get_text('text',sort=True).strip()) for page in doc[:3])
if chars > 200:
    # 文字版：直接提取
    text = ''
    for page in doc: text += page.get_text('text', sort=True) + '\n'
    with open(f'{outdir}/{name}.txt', 'w') as f: f.write(text)
    print(f'✅ {name} (文字提取)')
else:
    # 扫描版：OCR
    txt = ''
    for i in range(doc.page_count):
        pix = doc[i].get_pixmap(dpi=250)
        img = f'/tmp/_batch_{i}.png'; pix.save(img)
        r = subprocess.run([ocr, img], capture_output=True, text=True, timeout=60)
        txt += f'[第{i+1}页]\n{r.stdout}\n'
    with open(f'{outdir}/{name}_OCR.txt', 'w') as f: f.write(txt)
    print(f'✅ {name} (OCR {doc.page_count}页)')
doc.close()
"
```

**图片**：
```bash
python3 -c "
import subprocess, os
ocr = os.path.expanduser('~/Library/Application Support/reasonix/global-workspace/ocr_helper')
outdir = os.path.expanduser('~/Desktop/小焕的资料/OCR输出')
os.makedirs(outdir, exist_ok=True)
name = os.path.splitext(os.path.basename('<FILE>'))[0]
r = subprocess.run([ocr, '<FILE>'], capture_output=True, text=True, timeout=60)
with open(f'{outdir}/{name}_OCR.txt', 'w') as f: f.write(r.stdout)
print(f'✅ {name}')
"
```

### Step 3: 汇总报告
处理完成后输出汇总：
- 总文件数 / 成功 / 失败
- 每个文件的处理方式（文字提取 / OCR / 跳过）
- 所有输出保存在 `~/Desktop/小焕的资料/OCR输出/`

## 规则
1. 自动创建输出目录
2. 同名文件不覆盖（加 `_1` 后缀）
3. 处理中断可重试（自动跳过已存在的输出）
4. 支持子文件夹递归（默认关闭，加 `--recursive` 开启）
