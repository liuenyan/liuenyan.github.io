---
layout: post
title:  "kramdown 使用技巧"
date:   2016-07-31 19:30:00 +0800
categories: markdown
---

kramdown 已经成为 github pages 的 jekyll 静态网站生成器目前唯一支持的 markdown 引擎，参见 [Updating your Markdown processor to kramdown](https://help.github.com/articles/updating-your-markdown-processor-to-kramdown/)。

下面是一些使用karmdown 的小技巧，仅供参考。

<!--break-->

## 列表中的代码块

当在一个列表内部插入代码块时，需要根据列表项内容的开始位置决定代码块缩进的字符数量。

### 无序列表列表项内部的代码块：

<pre><code>
- 项目1

  ```python
  print("Hello world!")
  ```

- 项目2
</code></pre>

### 有序列表列表项内部的代码块：

<pre><code>
1. 项目1

   ```python
   print("Hello world!")
   ```

2. 项目2
</code></pre>

## 目录列表 ( table of content )

使用下面的语法创建目录列表

```
* toc
{:toc}
```
