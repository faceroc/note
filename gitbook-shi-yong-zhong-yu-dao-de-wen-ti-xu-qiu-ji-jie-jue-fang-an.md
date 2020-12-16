# Gitbook使用中遇到的问题\(需求\)及解决方案 ---持续更新

#### 1.导入外部链接需要手动修改默认文件名\(SLUG\) 2020-12-13

通过外部链接导入的文章同步到github后默认为名称“untitled.md"，对应网址为”http://xx.com/untitled”

解决方案：在文章标题右边“..."，进入页面编辑，在SLUG处重置即可。Gitbook会自动将中文部分用拼音分词,SAVE后Merge即可。

![&#x5916;&#x90E8;&#x94FE;&#x63A5;&#x5BFC;&#x5165;&#x7684;&#x6587;&#x7AE0;SLUG&#x503C;&#x4E3A;untitled](.gitbook/assets/image%20%287%29.png)

![&#x590D;&#x5236;&#x7C98;&#x8D34;TITLE&#x5230;SLUG&#x6846;&#xFF0C;&#x81EA;&#x52A8;&#x62FC;&#x97F3;&#x5206;&#x8BCD;&#xFF0C;&#x975E;&#x5E38;&#x65B9;&#x4FBF;](.gitbook/assets/image%20%283%29.png)

#### 2.通过Github授权登陆时报ISP错误 2020-12-16

环境：Win 10 2004已更新到最补丁包，中国大陆网络运营商

开启VPN，香港/日本/美国节点，智能路由模式，从Github授权登陆Gitbook时，提示如下错误：

**A network error has occurred. The service may be blocked by your ISP or in your area.**

只要将VPN改为“全局模式”，强制出口为海外线路即可。



