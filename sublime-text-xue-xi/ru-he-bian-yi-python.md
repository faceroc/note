---
description: 其他编程语言可参考本文
---

# 如何编译Python

## 1.设置语法

![](../.gitbook/assets/image%20%2825%29.png)

## 2.修改编译语言

![](../.gitbook/assets/image%20%2814%29.png)

## 3.查看编译快捷键

sublime默认编译快捷键是⌘\(Command\)+B

![](../.gitbook/assets/image%20%2824%29.png)

## 4.遇到的问题

对于含input函数的交互型代码，输入数据后无法执行并输出结果

### 4.1 报错界面

![](../.gitbook/assets/image%20%2823%29.png)

### 4.2 IDLE下执行后正常输入输出

![](../.gitbook/assets/image%20%2820%29.png)

## 5. 解决方案

#### 5.1 安装sublimeREPL插件

安装教程见 [1.Package Control教程](1.package-control-an-zhuang-shi-yong-ji-xie-zai.md#2-tong-guo-package-control-an-zhuang-xin-cha-jian)）

![](../.gitbook/assets/image%20%286%29.png)

#### 5.2 编辑自定义快捷键

在菜单栏选择【Preferences】--&gt;【Key Blinding - User】，在出现的页面中编辑自定义快捷键的内容。

![1](../.gitbook/assets/image%20%2826%29.png)

![2](../.gitbook/assets/image%20%2822%29.png)

因为sublime默认的编译快捷键是 ⌘\(command\)+B，为了方便我设置为 ⌘\(commad\)+G （可以根据各人习惯修改）。

代码文本如下

```text
[
    { "keys": ["command+g"], "caption": "SublimeREPL:Python", 
                      "command": "run_existing_window_command", "args":
                      {
                           "id": "repl_python_run",
                           "file": "config/Python/Main.sublime-menu"
                      } 
    }
]
```

#### 5.3 编译测试

通过⌘\(command\)+G快捷键可正常编译并输入输出正常数值。

update:2020-12-28

![](../.gitbook/assets/image%20%285%29.png)

