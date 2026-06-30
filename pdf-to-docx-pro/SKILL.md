---
name: pdf-to-docx-pro
description: PDF→DOCX 智能双版处理。版A原文+首页分析，版B断句翻译+首页分析。适配 DeepSeek/ChatGPT/Claude 等任意 AI。
---

# PDF → DOCX 智能双版处理（通用版）

直接把 PDF 拖进来，生成两份排版好的 DOCX。

## 使用方法

**DeepSeek / Reasonix：** 直接拖入 PDF，说"用 pdf-to-docx-pro 处理"

**ChatGPT / Claude / Kimi / 豆包：** 复制这段话发给 AI，并上传 PDF：

```
请处理这个 PDF。生成两份 DOCX：
版A（原文版）：首页分析报告（标题/字数/难字/主题/建议）+ 原文 + 页码
版B（精读版）：首页分析报告 + 断句 + 白话翻译 + 页码
```

## 输出

- `版A.docx` — 原文对照版
- `版B.docx` — 断句翻译版

## 终端命令

完成后我会提供类似这样的命令，复制到终端就能放到桌面：

```bash
cp /tmp/版A.docx ~/Desktop/
```

## 说明

不用会编程，不用装软件。告诉 AI 你想处理 PDF，剩下的交给它。
