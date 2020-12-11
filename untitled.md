---
description: 将域名CNAME到github后遇到的一些情况记录下
---

# CNAME记录遇到的问题及解析生效时间

## CNAME记录遇到的问题及解析生效时间

将域名CNAME到github后遇到的一些情况记录下

## 遇到的问题

在faceroc.com域名注册商"1API 官方DNS后台"设置CNAME至 faceroc.github.io时报错。  
 共设置了2条:

1. @.faceroc.com CNAME faceroc.github.io
2. [www.faceroc.com](http://www.faceroc.com/) CNAME faceroc.github.io  其中1报错：Invalid attribute value; cannot create CNAME record - CNAME in root level not allowed  2设置成功。

尝试几次后，为了不浪费时间，果断转到dnspod.com。  
 即发现早几年前被腾讯收购的dnspod海外版也迁移到腾讯云，并要提供海外手机验证码。幸好有备用海外号，拿到验证码后，下一步竟然要求绑卡,what?

```text
Please complete your information
Your account email address: aaxxbb@gmail.com
DNSPod has upgraded to Tencent Cloud account. To ensure that you can use the service normally, please complete your information.
接下来就要我填写信用卡认证身份。
```

还好下面有个灰色不起眼的小按钮“go to console”  
 遂在dnspod.com后台配置好CNAME。  
 大约30分钟后还是未生效？用后台工具查一下。

## DNS地址检测

该域名更新的DNS地址没有超过72小时, 请耐心等待（最多等待58小时）  
 a.dnspod.com  
 b.dnspod.com  
 c.dnspod.com

## DNS生效检测

该域名解析正常，详情如下：  
 ; &lt;&lt;&gt;&gt; DiG 9.9.4-RedHat-9.9.4-29.el7\_2.2 &lt;&lt;&gt;&gt; faceroc.com  
 ;; global options: +cmd  
 ;; Got answer:  
 ;; -&gt;&gt;HEADER&lt;&lt;- opcode: QUERY, status: NOERROR, id: 37547  
 ;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:  
 ; EDNS: version: 0, flags:; udp: 4096  
 ;; QUESTION SECTION:  
 ;faceroc.com. IN A

;; ANSWER SECTION:  
 faceroc.com. 424 IN CNAME faceroc.github.io.  
 faceroc.github.io. 38400 IN A 127.0.0.1

;; Query time: 2 msec  
 ;; SERVER: 114.114.114.114\#53\(114.114.114.114\)  
 ;; WHEN: Thu Dec 10 16:06:53 CST 2020  
 ;; MSG SIZE rcvd: 87

## 打开网站还是跳转到原来阿里云服务器上的BT面板提示页：

### 没有找到站点

您的请求在Web服务器中没有找到对应的站点！

### 可能原因：

您没有将此域名或IP绑定到对应站点!  
 配置文件未生效!

### 如何解决：

检查是否已经绑定到对应站点，若确认已绑定，请尝试重载Web服务；  
 检查端口是否正确；  
 若您使用了CDN产品，请尝试清除CDN缓存；  
 普通网站访客，请联系网站管理员；

这时候才想起来，原来我之前的DNS是在阿里云上配置的,不是在域名商那。那正好，放弃dnspod.com，跑到阿里云后台设置好。  
 不过悲剧的是，在阿里云设置2小时后，还是无法正常用自己的域名访问，这个CNAME解析时间比A记录要慢很多呀。

update:20小时后，CNAME解析终于生效。

update:创建gitbook后用了一个新的子域名note.faceroc.com，CNAME记录：hosting.gitbook.io，大概1小时后解析即生效。

