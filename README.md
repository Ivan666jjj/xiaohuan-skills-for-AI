<p align="center">
  <h1 align="center">🧠 Xiaohuan Skills for AI</h1>
  <p align="center">
    古籍 OCR / 智能天气 / PDF 处理 / 文件归类 / Token 优化
    <br>
    作者：<b>严小焕</b> · 中国人民大学文学院强基古文字方向
  </p>
  <p align="center">
    <img src="https://img.shields.io/badge/Reasonix-技能-blue" alt="Reasonix">
    <img src="https://img.shields.io/badge/通用-任意AI-green" alt="通用">
    <img src="https://img.shields.io/badge/许可证-MIT-orange" alt="License">
  </p>
</p>

---

## 📦 技能清单

| 技能 | 说明 | 分类 |
|:----|:-----|:----:|
| **scan-pdf** | 古籍 PDF 扫描 OCR（繁体/竖排/生僻字） | 🏛️ 古籍 |
| **ancient-pdf-reader** | 古籍 PDF 阅读器 | 🏛️ 古籍 |
| **batch-ocr** | 批量 OCR 处理 | 🏛️ 古籍 |
| **smart-weather** | 智能天气校准（多模型交叉验证） | 🌤️ 天气 |
| **beijing-weather-pro** | 北京海淀天气校准版（动态偏差校准） | 🌤️ 天气 |
| **pdf-to-docx-pro** | PDF→DOCX 智能双版处理（原文版+断句翻译版） | 📄 文档 |
| **text-stats** | 古典文献字频/词频分析 | 📊 分析 |
| **compare-texts** | 文献版本对读/校勘 | 📖 汉语言 |
| **convert-text** | 繁简转换/竖排转横排/文言断句 | 📖 汉语言 |
| **paper-outline** | 论文大纲自动生成 | 📖 汉语言 |
| **pdf-to-notes** | PDF → 读书笔记 | 📖 汉语言 |
| **token-saver** | DeepSeek v4 Token 优化方案 | ⚡ 效率 |

---

## 📥 安装 & 使用说明（小白版）

### 方式一：Reasonix（最推荐）

**下载地址：** [github.com/Ivan666jjj/reasonix](https://github.com/Ivan666jjj/reasonix)（暂未公开，可直接用本仓库的配置）

**安装步骤：**
1. 打开 Reasonix
2. 把这个仓库下载或克隆到本地
3. 将各技能的 `SKILL.md` 放入 Reasonix 的 skills 目录
4. 重启 Reasonix，输入 `/[技能名]` 即可

**示例：**
```
/scan-pdf 帮我识别这本古籍
/smart-weather 北京今天天气如何
/pdf-to-docx-pro 处理这个 PDF
```

---

### 方式二：DeepSeek（免费·国产）

**访问地址：** [chat.deepseek.com](https://chat.deepseek.com) 或下载 App（应用商店搜"DeepSeek"）

**使用步骤：**
1. 打开 DeepSeek 网页或 App
2. 在输入框粘贴以下文字：

```
请处理这个 PDF。生成两份 DOCX：
版A（原文版）：首页分析报告（标题/字数/难字/主题/建议）+ 原文 + 页码
版B（精读版）：首页分析报告 + 断句 + 白话翻译 + 页码
```

3. 上传你的 PDF 文件（点击输入框旁的 📎）
4. 按回车发送，等待处理完成

**特点：** 免费、支持文件上传、适合古籍和学术文档

---

### 方式三：ChatGPT（国际·需科学上网）

**访问地址：** [chat.openai.com](https://chat.openai.com) 或下载 App（美区 Apple ID）

**使用步骤：**
1. 打开 ChatGPT
2. 在输入框粘贴以下文字：

```
请处理这个 PDF。生成两份 DOCX：
版A（原文版）：首页分析报告（标题/字数/难字/主题/建议）+ 原文 + 页码
版B（精读版）：首页分析报告 + 断句 + 白话翻译 + 页码
```

3. 点击 📎 上传 PDF 文件
4. 按回车等待处理

**特点：** 能力强、支持文件上传、适合复杂任务

---

### 方式四：Claude（国外·需科学上网）

**访问地址：** [claude.ai](https://claude.ai) 或下载 App

**使用步骤：**
1. 打开 Claude
2. 上传 PDF，然后说：
   "用 pdf-to-docx-pro 方式处理这个文件"
3. 或粘贴方式二中的提示词

**特点：** 长上下文、擅长处理古籍文本

---

### 方式五：Kimi（免费·国产）

**访问地址：** [kimi.moonshot.cn](https://kimi.moonshot.cn) 或下载 App

**使用步骤：** 同上，上传 PDF + 粘贴提示词即可。

---

### 方式六：豆包（免费·国产·字节跳动）

**访问地址：** 应用商店搜"豆包"下载 App，或网页版 [doubao.com](https://www.doubao.com)

**使用步骤：** 同上，上传 PDF + 粘贴提示词。

---

### 方式七：通义千问（免费·国产·阿里巴巴）

**访问地址：** [tongyi.aliyun.com](https://tongyi.aliyun.com) 或下载 App

**使用步骤：** 同上。

---

## 💡 小白一句话总结

**不用安装任何东西。** 打开上面任何一个 AI 网站或 App → 上传 PDF → 粘贴提示词 → 等它处理完。就这么简单。

---

## 📄 许可证

MIT © 2026 严小焕

有问题或建议：**1416578309@qq.com**
