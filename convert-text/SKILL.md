---
name: convert-text
description: 繁简转换、竖排转横排、文言断句
---

# 文本转换工具

繁简转换、竖排转横排、文言断句——汉语言文学日常工具集。

## 触发
`/convert-text <操作> <输入>`

操作类型：
- `繁转简` `简转繁` 
- `竖转横`（竖排文字转横排）
- `断句`（给无标点文言文加标点）

## 繁简转换
直接处理，保持异体字不变（如"羣"不转"群"，保留古籍用字特征）。

```bash
# 繁体转简体
python3 -c "
import sys
text = sys.argv[1]
# 使用 OpenCC 或简单映射
# 繁→简（内置映射表）
map_table = {
    '說':'说', '來':'来', '時':'时', '見':'见', '爲':'为', 
    '書':'书', '國':'国', '學':'学', '門':'门', '萬':'万',
    '會':'会', '過':'过', '開':'开', '關':'关', '對':'对',
    '動':'动', '從':'从', '無':'无', '個':'个', '們':'们',
    '後':'后', '裏':'里', '麼':'么', '體':'体', '點':'点',
}
for t, s in map_table.items():
    text = text.replace(t, s)
print(text)
" '<输入文本>'
```

也可以直接调用 macOS 内建繁简转换（`textutil` 不直接支持，用 Python opencc）：

若需要完整繁简转换，安装：
```bash
/tmp/pdfenv/bin/pip install opencc-python-reimplemented -q
```
然后：
```bash
/tmp/pdfenv/bin/python3 -c "
from opencc import OpenCC
cc = OpenCC('t2s')  # 繁→简，也可 's2t' 简→繁
print(cc.convert('<文本>'))
"
```

## 竖排转横排
古籍竖排排版（右→左，上→下）转成横排阅读格式：

策略：先 OCR 识别竖排文字（Vision OCR 原生支持），然后按竖排→横排重新排列。

```bash
# 竖排识别用 Vision OCR（自带竖排支持）
~/Library/Application\ Support/reasonix/global-workspace/ocr_helper '<竖排图片>'
```

## 文言断句
用本地 qwen2.5:7b 或直接由 AI 对无标点文言文加标点：

1. 先让用户提供需要断句的文言文段落
2. AI 分析语义和语法结构
3. 输出带标点版本，并标注断句依据

格式：原文 → 断句后 → 关键断句处简注

## 规则
1. 繁简转换保留古籍异体字特征
2. 竖排优先用 Vision OCR
3. 断句后标注关键判断依据
