# 🧠 小焕的 AI 技能仓库 — XiaoHuan Skills for AI

> 可复用的 AI 技能集合，适用于 **Reasonix / Kimi / ChatGPT / Claude / DeepSeek** 等任意 AI 平台。
> 每个技能都是一个独立 prompt，复制粘贴即可使用。

[![GitHub stars](https://img.shields.io/badge/daily--life-8%20skills-brightgreen)]()
[![License](https://img.shields.io/badge/license-MIT-blue)]()

---

## 👤 关于作者

> **严小焕** · 中国人民大学 汉语言文学专业
> 热爱生活，喜欢折腾 AI 的文科生。这些技能都是我日常学习生活中真实在用的工具，希望能帮到同样需要它们的人。
>
> 📧 1416578309@qq.com
> 🔗 [GitHub](https://github.com/Ivan666jjj)

---

## 📦 技能总览

### 🌤 天气 & 出行
| 技能 | 标签 | 简介 |
|---|---|---|
| **Smart Weather** | `#天气` `#旅行` `#预算` | 多模型交叉校准天气预报 + 自动预算估算 |
| **Clouds Fire** | `#天气` `#晚霞` `#摄影` `#日落` | 火烧云晚霞概率预测器 |
| **Beijing Weather Pro** | `#天气` `#北京` `#本地校准` | 实测数据校准的北京专精天气 |

### 📚 学习 & 文件
| 技能 | 标签 | 简介 |
|---|---|---|
| **Note-to-Quiz** 🆕 | `#学习` `#考试` `#笔记` `#Anki` | 笔记自动转考题，支持DOCX/Anki导出 |
| **File Reader** 🆕 | `#文件` `#阅读` `#OCR` `#摘要` | PDF/DOCX/MD智能阅读+摘要+古籍OCR |
| **File Sorter** 🆕 | `#文件管理` `#归类` `#整理` | 桌面文件自动归类+去重+批量重命名 |

### 🍳 日常生活
| 技能 | 标签 | 简介 |
|---|---|---|
| **Life Assistant** 🆕 | `#菜谱` `#购物` `#健康` `#省钱` | 菜谱推荐/购物清单/健康提醒 |

### 🏛 省钱
| 技能 | 标签 | 简介 |
|---|---|---|
| **Token Saver** | `#省钱` `#优化` | 全自动 token 压缩，省40-60% |

---

## 🚀 快速安装

### Reasonix 用户
```bash
/smart-weather 今晚圆明园天气
/clouds-fire 今晚火烧云概率
/note-to-quiz 从这段笔记出题
/file-reader path=~/笔记.pdf
/file-sorter path=~/Desktop
/life-assistant 冰箱有鸡蛋番茄
```

### 其他 AI 用户
复制对应技能文件夹内的 `.md` 文件全部内容，粘贴到对话框即可。

---

## 📁 仓库结构
```
📁 xiaohuan-skills/
├── README.md                    # 本文件
├── smart-weather/
│   ├── smart-weather-prompt.md  # 通用prompt
│   └── README.md                # GitHub项目页
├── clouds-fire/
│   └── SKILL.md
├── note-to-quiz/
│   └── SKILL.md                 # 🆕 笔记转考题
├── file-reader/
│   └── SKILL.md                 # 🆕 文件阅读器
├── file-sorter/
│   └── SKILL.md                 # 🆕 文件归类器
├── life-assistant/
│   └── SKILL.md                 # 🆕 生活助手
└── beijing-weather-pro/
    └── SKILL.md
```

---

## 📄 协议
MIT — 自由使用、修改、分发。
