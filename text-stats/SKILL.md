---
name: text-stats
description: 古典文献字频/词频/句式量化分析
---

# 文本统计与词频分析

分析古典文献的字频、词频、句式分布——汉语言文学研究的量化工具。

## 触发
`/text-stats <文本路径> [--type 字频|词频|句式]`

## 工作流程

### 字频统计
```bash
/tmp/pdfenv/bin/python3 -c "
import re, collections
text = open('<FILE>').read()
# 去除标点和空白，只留汉字
chars = re.findall(r'[\u4e00-\u9fff]', text)
counter = collections.Counter(chars)
print(f'总字数: {len(chars)}')
print(f'不重复字数: {len(counter)}')
print('前30高频字:')
for char, count in counter.most_common(30):
    pct = count/len(chars)*100
    bar = '█' * int(pct*5)
    print(f'  {char}  {count:5d} ({pct:.2f}%) {bar}')
"
```

### 词频统计（双字词）
```bash
/tmp/pdfenv/bin/python3 -c "
import re, collections
text = open('<FILE>').read()
chars = re.findall(r'[\u4e00-\u9fff]', text)
bigrams = [''.join(chars[i:i+2]) for i in range(len(chars)-1)]
counter = collections.Counter(bigrams)
print('前30高频双字词:')
for word, cnt in counter.most_common(30):
    print(f'  {word}  {cnt}')
"
```

### 句式分析
分析平均句长、句式中位长度、长句/短句比例、骈偶句检测。

## 输出格式
```
📊 <文件名> 文本统计
━━━━━━━━━━━━━━━━━━━━
总字数: 12,345
不重复字: 2,345
字密度: 78.3% (去重率: 81.0%)
━━━━━━━━━━━━━━━━━━━━
Top 10 高频字:
  之  456 (3.69%) ████████████████████
  也  389 (3.15%) ████████████████
  而  312 (2.53%) █████████████
  ...
━━━━━━━━━━━━━━━━━━━━
Top 10 双字词:
  君子  45
  天下  38
  ...
```

## 规则
1. 自动过滤标点、空白、注释标记
2. 支持 TXT/Markdown/PDF（PDF 先提取文字）
3. 高频字排名可用作文献风格分析依据
