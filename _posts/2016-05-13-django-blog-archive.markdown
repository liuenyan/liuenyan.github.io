---
layout: post
title:  "django博客存档的实现"
date:   2016-05-13 19:51:00 +0800
categories: python django
---
最近我正在学习Django写一个个人博客，其中要实现一个按照年和月生成博客归档的功能。查询资料后实现如下：
在`blog.models`中定义博客模型如下：

{% highlight python %}
class Post(models.Model):
    title = models.CharField(max_length=128)
    body = models.TextField()
    timestamp = models.DateTimeField(auto_now_add=True)
    author = models.ForeignKey('auth.User')
    tags = models.ManyToManyField(Tag)
    
    def __str__(self):
        return self.title
{% endhighlight %}

<!--break-->

一种最简单的方法是使用[dates]函数。

{% highlight python %}
archives = Post.objects.dates('timestamp', 'month', 'DESC')
{% endhighlight %}

另外一种方法是使用聚合。这种方法不仅可以获取生成归档，还能得到相应月份的文章的数量。

首先处理时间字段，查询得到含年和月的结果集。然后使用`values()`和`annotate(Count('id'))`分组统计年和月中文章的数量。

{% highlight python %}
archives = Post.objects.extra(select={
            'year': 'strftime("%Y", timestamp)',
            'month': 'strftime("%m", timestamp)',
        }).values('year', 'month').annotate(Count('id'))
{% endhighlight %}

注意不同的数据库从datetime中获取年和月的方法有所不同。本例中使用的数据库是sqlite3，使用的是sqlite的[strftime]。如果是oracle数据库你可能需要[extract]。

[dates]: https://docs.djangoproject.com/en/1.10/ref/models/querysets/#dates
[strftime]: https://www.sqlite.org/lang_datefunc.html
[extract]: http://docs.oracle.com/cd/B19306_01/server.102/b14200/functions050.htm
