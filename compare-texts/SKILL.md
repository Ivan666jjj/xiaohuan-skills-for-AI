---
name: compare-texts
description: 文献版本对读/校勘，并排对比差异高亮
---

# 文献对读（校勘辅助）

并排对比两个文本，高亮差异——古籍校勘/版本比对利器。

## 触发
`/compare-texts <文本A> <文本B> [--mode 逐行|逐段|逐句]`

## 工作流程

### 并排对比
```bash
/tmp/pdfenv/bin/python3 -c "
import difflib, sys
a = open('<FILE_A>').readlines()
b = open('<FILE_B>').readlines()
differ = difflib.HtmlDiff()
html = differ.make_file(a, b, '<NAME_A>', '<NAME_B>')
open('/tmp/diff.html', 'w').write(html)
print('✅ 对比结果: /tmp/diff.html')
"
```

### 差异统计
```bash
/tmp/pdfenv/bin/python3 -c "
import difflib
a = open('<FILE_A>').readlines()
b = open('<FILE_B>').readlines()
matcher = difflib.SequenceMatcher(None, a, b)
print(f'相似度: {matcher.ratio()*100:.1f}%')
for tag, i1, i2, j1, j2 in matcher.get_opcodes():
    if tag != 'equal':
        print(f'[{tag}] A行{i1}-{i2} ↔ B行{j1}-{j2}')
        if tag == 'replace':
            print(f'  A: {\" \".join(a[i1:i2])[:100]}')
            print(f'  B: {\" \".join(b[j1:j2])[:100]}')
"
```

### 校勘标记
输出带校勘记的合并文本，用符号标记：
- `[+]` 新增内容
- `[-]` 删除内容  
- `[*]` 修改内容

## 输出格式
```
📋 <版本A> vs <版本B> 校勘报告
━━━━━━━━━━━━━━━━━━━━
相似度: 94.2%
差异数: 23 处
  新增: 5 | 删除: 3 | 修改: 15
━━━━━━━━━━━━━━━━━━━━
[replace] 行12: 
  版本A: 学而时习之，不亦说乎
  版本B: 学而时习之，不亦乐乎
━━━━━━━━━━━━━━━━━━━━
详细对比: /tmp/diff.html (浏览器打开)
```

## 规则
1. 支持 TXT/Markdown，PDF 先提取文字
2. 输出 HTML 可视对比（浏览器打开）/ 纯文本校勘记
3. 相似度 >95% 提示可能是同源版本
