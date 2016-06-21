---
layout: post
title:  "python中下划线的作用"
date:   2016-06-21 21:03:00 +0800
categories: python
---

下划线在python中有3中常见用法：

1. 在一个python解释器的交互界面中获取上一个执行语句的结果。这个最先是由标准的CPython解释器所设定的，也被其他的python解释器所效仿。
2. 用于i18n的翻译查找（从相关的C语言惯例中引入）。比如代码`raise forms.ValidationError(_("Please enter a correct username"))`。
3. 一般用于在标记在一个函数的返回结果中故意被忽略的无用变量。比如在代码`label, has_label, _ = text.partition(':')`中返回值中的第三个变量被故意忽略。

后两种用法会导致冲突，所以在代码中使用了 `_` 来指示i18n翻译时，有必要**避免使用** `_` 来标记一个故意被抛弃的变量。因为这个原因，很多人喜欢使用双下划线 `__` 来表示故意被抛弃的变量。

参考资料: [What is the purpose of the single underscore variable in Python?](http://stackoverflow.com/questions/5893163/what-is-the-purpose-of-the-single-underscore-variable-in-python)
