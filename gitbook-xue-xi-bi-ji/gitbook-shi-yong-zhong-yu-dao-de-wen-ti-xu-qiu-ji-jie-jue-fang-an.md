# Gitbook使用中遇到的问题\(需求\)及解决方案 ---持续更新

## 1.通过Github授权登陆时报ISP错误 2020-12-16

`环境：Windows 10 2004+最新补丁，Chrome 86+SwitchOmega插件(配置了香港/日本/美国节点)。`

Gitbook登陆时选择“Github授权"后，提示如下错误：

**A network error has occurred. The service may be blocked by your ISP or in your area.**

经排查，是SwitchOmega设置为`Auto Switch`导致的。Auto Switch模式下，SwitchOmega图标一直提醒有XX个链接因网络原因未加载，手动添加几项后，再刷新还是有提示。估计这是导致无法从Github授权登陆的原因。

解决办法：直接选择`香港/日本/美国节点`（全局模式）即可。

## 2.如何更改代码块的黑色背景

用了一年多黑色模式，最近发现还是白色模式好看，怎么改?



