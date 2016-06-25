---
layout: post
title:  "获取自己的公网IP"
date:   2016-06-25 12:50:00 +0800
categories: shell
---

如何能够获取自己的公网IP,下面是一些方法：

- 使用一些网站提供的服务，这样的网站有很多，比如下面这些:

{% highlight shell %}
curl checkip.amazonaws.com
curl ifconfig.me/ip
curl ifconfig.co
curl diagnostic.opendns.com/myip
{% endhighlight %}

- 使用openDNS提供的服务

{% highlight shell %}
dig +short myip.opendns.com @resolver1.opendns.com
{% endhighlight %}
