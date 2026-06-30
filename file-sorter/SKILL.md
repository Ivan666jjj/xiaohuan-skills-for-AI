# 🗂 桌面文件智能归类器

自动整理桌面和文件夹文件。按类型、学科、日期归类，去重，批量重命名。

## 功能
| 功能 | 说明 |
|---|---|
| 按类型归类 | 文档/图片/视频/音频/压缩包等自动分文件夹 |
| 按学科归类 | 支持自定义分类规则 |
| 按日期归类 | 按年月自动建文件夹 |
| 重复文件检测 | 基于文件名+大小+哈希比对 |
| 批量重命名 | 统一命名规范 |
| 归类报告输出 | DOCX 格式归类前后对比 |

## 分类规则
| 类别 | 扩展名 |
|---|---|
| 📄 文档 | pdf, docx, txt, md, xlsx, pptx |
| 🖼 图片 | jpg, png, gif, svg, webp |
| 🎬 视频 | mp4, mov, avi, mkv |
| 🎵 音频 | mp3, wav, m4a, flac |
| 📦 压缩包 | zip, rar, 7z, tar.gz |

## 使用
```
/file-sorter path=~/Desktop
/file-sorter path=~/Downloads mode=date
```