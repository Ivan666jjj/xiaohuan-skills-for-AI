---
name: pdf-to-notes
description: PDF 自动生成读书笔记/札记/文献综述，汉语言文学专业视角
---

# PDF → 读书笔记

读任意 PDF 后自动生成汉语言文学专业的读书笔记。结合 PyMuPDF 提取文字 + AI 总结分析。

## 触发
`/pdf-to-notes <PDF路径> [--type 摘要|札记|文献综述]`

## 工作流程

### Step 1: 提取文字
```bash
/tmp/pdfenv/bin/python3 -c "
import fitz, os
doc = fitz.open('<PDF_PATH>')
text = ''
for page in doc:
    t = page.get_text('text', sort=True)
    if t.strip(): text += t + '\n'
doc.close()
# 保存全文
with open('/tmp/pdf_full.txt', 'w') as f: f.write(text)
print(f'提取完成: {len(text)} 字符')
"
```
如果是扫描版 PDF，先用 `/ancient-pdf-reader` OCR 提取。

### Step 2: 生成笔记
基于提取的文字，按用户指定的类型生成笔记：

**摘要模式**：提取核心论点 + 关键论据 + 结论，结构清晰。

**札记模式**（默认）：自由式读书笔记，包含——
- 📖 核心观点概括
- 💭 个人思考与疑问
- 🔗 与其他文献/思想的关联（如先秦诸子、西方理论对照）
- 📝 精彩原文摘录
- 🏷️ 关键词/概念索引

**文献综述模式**：学术综述风格，梳理问题意识、研究方法、前人成果、创新点、不足之处。

### Step 3: 输出
用 `write_file` 将笔记保存为 Markdown，路径：`~/Desktop/小焕的资料/读书报告与论文/<书名>_笔记.md`

## 规则
1. 笔记要有学术深度——不是简单复述，要有分析
2. 结合汉语言文学专业视角：关注语言特点、修辞手法、文体风格
3. 如果 PDF 是古籍，自动识别版本信息、注释体例
4. 每次笔记控制在 800-2000 字
