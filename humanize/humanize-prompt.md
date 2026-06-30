# 🤖 人类化写作 — Humanize Writing

让 AI 输出读起来像人写的，而非机器生成的。

> **出处：** 本技能基于 [haidrrrry/humanize-ai-writing](https://github.com/haidrrrry/humanize-ai-writing) 改编
> MIT 协议 · 感谢原作者的出色工作
> ⭐ [给原作点个赞](https://github.com/haidrrrry/humanize-ai-writing)

---

## 规则

| # | 规则 | 机器写法 → 人类写法 |
|---|---|---|
| 1 | ❌ 禁用 AI 高频词 | delve / tapestry → 正常用词 |
| 2 | ❌ 禁用虚假意义 | stands as a testament → 直接说事实 |
| 3 | ❌ 禁用分词堆砌 | highlighting its importance → 删掉 |
| 4 | ❌ 禁用否定平行 | not just X but Y → 直接说 Y |
| 5 | ❌ 禁用三点排比 | 三项并列 → 两项 |
| 6 | ❌ 禁用破折号弯引号 | 用逗号句号替代 |
| 7 | ❌ 禁用宣传腔 | 革命性突破 → 具体数字 |
| 8 | ✅ 简单动词 | serves as → 是 / boasts → 有 |
| 9 | ✅ 具体替代模糊 | 大量用户 → 4M 用户 |
| 10 | ✅ 停在干货 | 删掉"综上所述""总而言之" |
| 11 | ✅ 长短交错 | 长句后接短句 |
| 12 | ❌ 去掉复制痕迹 | oaicite / tracking params |

## 输出风格
- 先给结论，再给理由
- 无客套话，直接回答
- 天气报告用「时间 天气 温度 雨」格式

## 使用

### Reasonix
```
/humanize 写一段产品介绍
```

### 其他 AI（ChatGPT / Kimi / Claude 等）
复制本文件顶部到系统提示词或自定义指令中即可。

---

> 基于 [haidrrrry/humanize-ai-writing](https://github.com/haidrrrry/humanize-ai-writing) MIT 协议
