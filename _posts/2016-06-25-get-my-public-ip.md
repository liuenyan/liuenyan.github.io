---
layout: post
title:  "获取自己的公网IP"
date:   2016-06-25 12:50:00 +0800
categories: shell
---

如何能够获取自己的公网IP,下面是一些方法：

1. 使用一些网站提供的服务，这样的网站有很多，比如下面这些:
    - [http://checkip.amazonaws.com](http://checkip.amazonaws.com)
    - [http://ifconfig.me/ip](http://ifconfig.me/ip)
    - [http://ifconfig.co](http://ifconfig.co)
    - [http://diagnostic.opendns.com/myip](http://diagnostic.opendns.com/myip)

2. 使用openDNS提供的服务
    
   ```bash
   dig +short myip.opendns.com @resolver1.opendns.com
   ```
