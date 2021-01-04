---
description: 'tag:RT-AC68U,TimeMachineEditor'
---

# TimeMachine备份策略

系统：macOS Big Sur, Version 11.1

## 1.预期中的硬盘故障

原来TimeMachine是放在群晖NAS上的，最近因为NAS中的RAID6阵列有一块硬盘异常经常不稳定，新的硬盘又没到，虽然能工作，但怕坏第二块盘，所以不能再让他承担备份的工作了。而且还考虑到RAID6的特性，即使更换了新硬盘也要花很长时间恢复和效验数据。我之前给TimeMachine文件夹分配了1T空间，所以在RAID重建前，可以把TimeMachine换一台机器，NAS上的TimeMachine备份可以删掉，估计能节约不少时间，所以就关闭了NAS上的TimeMachine功能，删掉了备份。

家里默默的稳定工作好多年的ASUS AC68U路由自带TimeMachine功能，以前对路由器带的这个功能一直不感冒，总觉得单盘容易出故障，会不稳定。但现在组了RAID6的NAS竟然也出故障了，数据恢复还超级费时间，感觉也没有那么靠谱。所以在删除NAS上的TimeMachine前，要先将MBP中的备份磁盘指向了AC68U。

## 2.启用AC68U的TimeMachine

![&#x5728;&#x8DEF;&#x7531;&#x5668;&#x540E;&#x53F0;&#x8FDB;&#x5165;&#x5BF9;&#x5E94;&#x9875;&#x9762;](.gitbook/assets/image%20%2857%29.png)

![&#x5F00;&#x542F;&#x5E76;&#x9009;&#x62E9;&#x8DEF;&#x5F84;&#x548C;&#x78C1;&#x76D8;&#x5BB9;&#x91CF;&#x5E94;&#x7528;&#x5373;&#x53EF;](.gitbook/assets/image%20%2865%29.png)

![&quot;&#x9009;&#x62E9;&#x78C1;&#x76D8;&#x201D;&#x540E;&#x4F1A;&#x663E;&#x793A;Air](.gitbook/assets/image%20%2859%29.png)

## 3.TimeMachineEditor策略

如果按MAC默认的每小时创建一个快照并备份到TimeMachine，怕路由器压力太大，也伤硬盘。所以找了一个第三方工具“TimeMachineEditor"，可以自定义备份策略。

内置三种策略：

* When inactive/当不活跃
* Interval/时间间隔
* **Calendar Intervals/日历时间间隔**_**（我的策略）**_

![When inactive](.gitbook/assets/image%20%2856%29.png)

![Interval](.gitbook/assets/image%20%2860%29.png)

![Calendar Intervals](.gitbook/assets/image%20%2863%29.png)

我设置的是每周三、六凌晨2点开始备份；如果错过了会立即开始备份计划，但会排除早上8点至凌晨1点这个时间段；并且本地每小时会创建一个快照。

设置策略并”应用/Apply“后，会立即生效。再回到TimeMachine界面可以看到已经取消了自动备份，当前由TimeMachineEditor接管。

![](.gitbook/assets/image%20%2861%29.png)

## 4.为什么选择Calendar Intervals策略

考虑到手上这台MBP的稳定性一直都不错，数据也会实时同步到iCloud，TimeMachine更多的是防止系统级的崩溃，但用了这么多年MAC，很少有死机的情况，以后完全崩溃进不了系统的机率估计可以忽略不计，唯有系统大版本升级前可能会检查下TimeMachine是否正常工作。所以在频率上的要求并不高，解决“有/无”问题即可，系统默认的“24小时内的每小时备份”没有必要实时同步到远端TimeMachine上去。

AC68U毕竟性能有限，发热量也很大\(背壳加挂了2个风扇\)，在带了40+设备的情况下，再挂硬盘实时TimeMachine，路由器可能超负荷运转，如果出现卡顿影响网速或死机等情况就得不偿失了。而且外挂的机械硬盘24小时源源不断的写入数据也容易损坏，如果真坏了就失去备份的意义了。

当前的策略完美的避开了使用MBP的时间段以及平衡了备份的频率，最适合我。

Perfect!

## 5.路由器状态图

TimeMachine工作时的CPU占用确实挺高的。

![&#x5DE6;&#xFF1A;&#x6B63;&#x5E38;&#x5DE5;&#x4F5C;&#x3002;&#x53F3;&#xFF1A;TimeMachine&#x5907;&#x4EFD;&#x65F6;](.gitbook/assets/image%20%2858%29.png)

