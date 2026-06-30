# 🤖 人类化写作 — Humanize Writing

让 AI 输出读起来像人写的，而不是机器生成的。

基于 `haidrrrry/humanize-ai-writing` 的 12 条规则改编。适用于 Reasonix / ChatGPT / Claude / Kimi / DeepSeek 等。

## 核心规则

| # | 规则 | AI 常见写法 → 人类写法 |
|---|---|---|
| 1 | ❌ 禁用 AI 高频词 | "delve into" → "look at" / "tapestry" → 删掉 |
| 2 | ❌ 禁用虚假意义 | "stands as a testament" → 直接说事实 |
| 3 | ❌ 禁用分词堆砌 | "…, highlighting its importance" → 删掉 |
| 4 | ❌ 禁用否定平行 | "not just X but Y" → 直接说Y |
| 5 | ❌ 禁用三点排比 | 三个并列项改成两个或自然叙述 |
| 6 | ❌ 禁用破折号和弯引号 | — → , 或 . |
| 7 | ❌ 禁用宣传腔 | "革命性突破" → 具体数据 |
| 8 | ✅ 简单动词 | "serves as" → "是" / "boasts" → "有" |
| 9 | ✅ 具体替代模糊 | "大量用户" → "4M 用户" |
| 10 | ✅ 结尾干货 | 不加"综上所述"，停在最后一句 |
| 11 | ✅ 长短交错 | 混合长短句，避免全是长句 |
| 12 | ❌ 去掉复制痕迹 | oaicite, tracking params 等 |

## 使用

```
/humanize 写一段关于这个项目的介绍
→ 输出像人写的自然文本
```

> 本 skill 基于 [haidrrrry/humanize-ai-writing](https://github.com/haidrrrry/humanize-ai-writing) 改编，MIT 协议。
