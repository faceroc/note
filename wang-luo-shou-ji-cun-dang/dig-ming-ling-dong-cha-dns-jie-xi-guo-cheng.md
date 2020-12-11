# dig 命令洞察 DNS 解析过程

在[上一篇](https://cloud.tencent.com/developer/article/1365761?from=10680)文章，我们介绍了域名解析的过程，本章我们将介绍一个实用的工具---dig命令，通过dig命令我们可以查看 DNS 解析的过程，以便我们更好的理解 DNS 解析过程。

**dig** 命令全称域信息搜索器，是一个用于查询 DNS 域名服务器信息的命令行工具。因为dig命令灵活，容易使用，多数DNS管理员使用dig命令来诊断 DNS 问题。

**dig 常用命令格式**

dig \[@server\] \[-p port\] \[-t type\] \[-4\] \[-6\] \[+trace\] name

* @ 指定 DNS 查询使用的服务器名称或 IP ，IP 地址可以是用点分隔的 IPv4 地址也可以是冒号分隔的 IPv6 地址。当参数指定的值是服务器的主机名时，dig 命令会在查询该域名服务器前先解析该主机名；
* -p 指定 DNS 查询使用的端口号，默认情况下 DNS 查询使用标准的53端口，若使用非端口则需要通过 -p 参数指定，可使用此选项来测试已配置为侦听非标准端口号上的 DNS 服务器；
* -t 指定 DNS 查询的记录类型，常用的类型包括：A/AAAA/NS/MX/CNAME 等，缺省查询类型是 A ；
* -4 指定 dig 命令仅使用 IPv4 查询传输；
* -6 指定 dig 命令仅使用 IPv6 查询传输；
* +trace 跟踪从根名称服务器开始的迭代查询过程，缺省情况不使用跟踪。启用跟踪时，dig 命令会执行迭代查询以解析要查询的名称，显示来自用于解析查询的每个服务器的应答。

**dig 命令的输出格式**

```text
; <<>> DiG 9.10.6 <<>> www.qq.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 33603
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.qq.com.			IN	A

;; ANSWER SECTION:
www.qq.com.		93	IN	CNAME	a.https.qq.com.
a.https.qq.com.		219	IN	A	14.18.180.206

;; Query time: 60 msec
;; SERVER: 192.168.50.1#53(192.168.50.1)
;; WHEN: Sat Dec 12 01:37:21 CST 2020
;; MSG SIZE  rcvd: 66

```

以 dig www.qq.com 命令返回内容为例各字段说明如下：

* status 表示查询状态，取值为 NOERROR 表示查询没什么错误；
* opcode 表示操作码，取值为 QUERY 表示操作为查询操作；
* id 表示查询事务 id；
* QUERY 表示查询内容的条数，ANSEWER 表示回答内容条数，AUTHORITY 表示权威应答内容的条数，ADDITIONAL 表示附加内容的条数；
* QUESTION SECTION：表示需要查询的内容，这里的返回内容表示需要查询域名的 A 记录；
* ANSWER SECTION 表示查询结果，包含了两条记录，一条记录表示 www.qq.com 是 https.qq.com 的别名，第二条返回了 A 记录，表明 https.qq.com 的 IP 地址，其中93和219分别表示本次查询的缓存时间，分别在这些秒数内容本地 DNS 服务器可以直接从缓存返回结果。

**dig 命令查询资源记录**

各类型解析资源记录介绍：

* NS 记录：用来指定域名由哪个 DNS 服务器进行解析；
* CNAME 记录：用来定义域名的别名，方便实现将多个域名解析到同一个 IP 地址；
* A 记录：用来指定主机名对应的 IPv4 地址；
* AAAA 记录：用来指定主机名对应的 IPv4 地址；
* MX 记录：用来指定收件人域名的邮件服务器，SMTP 协议会根据 MX 记录的值来决定邮件的路由过程；
* PTR 记录：常用于反向地址解析，将 IP 地址解析到对应的名称；
* SOA 记录：称为起始授权机构记录，不同于 NS 记录用于标识多台域名解析服务器，SOA 记录用于在多台 NS 记录中哪一台是主 DNS 服务器。

**DNS 服务器的主从架构**

DNS 服务器通常以集群的方式提供服务，一台主服务器和多台从服务器，从服务器启动时从主服务器进行解析库的完全同步，运行时以一定的时间间隔进行增量刷新同步，继而记录的保证一致性，若从服务器超过一定的时间无法与主服务器同步刷新则从服务器记录会过期失效，无法提供解析服务。SOA 记录保存于主服务器，记录字段包括主 DNS 服务器名称，DNS 服务器管理员，序列号，从 DNS 服务器刷新间隔，从 DNS 服务器与主服务器断线后重连的时间间隔，从 DNS 服务器与 主 DNS 服务器断线后的过期时间间隔，记录的缓存生存周期。

到目前为止，我们对 DNS 解析的过程以及 DNS 服务器的架构已经有所了解，下一篇文章我们将讨论一个有趣的问题，[为什么全球只有13台 DNS 服务器](https://cloud.tencent.com/developer/article/1366044?from=10680)？

原文链接：[https://cloud.tencent.com/developer/article/1366027](https://cloud.tencent.com/developer/article/1366027)

