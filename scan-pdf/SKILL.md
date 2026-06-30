---
name: scan-pdf
description: 扫描古籍 PDF（繁体/竖排/生僻字），拖入 PDF 自动识别文字
---

# 古籍 PDF 扫描技能

## 自动触发
当你看到用户发送/拖入 `.pdf` 文件路径，或说"扫一下这个 PDF"之类的话时，**立即自动调用**本技能提取文字。

## 调用方式
```bash
PYTHONPATH=/Users/Admin/Library/Application\ Support/reasonix/global-workspace/.reasonix/packages python3 /Users/Admin/Library/Application\ Support/reasonix/global-workspace/.reasonix/scripts/guji_ocr/scan_pdf.py <path> [参数]
```

## 常用参数
| 参数 | 默认 | 说明 |
|------|------|------|
| `--format` | `text` | `text`/`json`/`markdown` |
| `--pages` | 0(全部) | 只扫前 N 页 |
| `--dpi` | 300 | 古籍建议 300-400 |
| `--verbose` | 否 | 显示进度 |

## 推荐用法
**快速查看：** `--format text --pages 5 --verbose`
**完整导出：** `--format markdown --output result.md`

## 技术说明
- OCR 引擎：RapidOCR (ONNX) — 基于 PP-OCRv4，支持繁/简中文
- PDF 渲染：PyMuPDF (fitz)
- 所有依赖在工作区 `.reasonix/packages/` 内，持久化可用
