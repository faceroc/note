# 热门插件

## 网上推荐的一些热门插件，有部分试用后觉得没必要就删掉了

```text
OmniMarkupPreviewer    在用
ChineseLocalizations    没装
AdvanceNewFile    没装
Evernote    没装。直接编辑Evernote文章，感觉多此一举，我喜欢直接在Evernote中直接编辑。
GitGutter    没装。在左边显示新建的行和修改的
Markdown Editing    在用,Markdown编辑支持
Material Theme    没装。主题插件，支持代码高亮显示
Package Control    在用
Side Bar    没装。默认的Tab方式已经很好用了
ConvertToUTF8    在用，解决txt文档中文乱码问题
Codecs33    在用，配合ConvertToUTF8
Markdown TOC    给markdown文件生成目录，且监听自动更新目录变更，可设置目录深度
```

## 部分插件简介

> 点标题可直接访问插件主页

### 1. [OmniMarkupPreviewer](https://github.com/timonwong/OmniMarkupPreviewer)

可在浏览器中实时预览Markdown，快捷键⌃\(command\)+⌥\(alt\)+O。

自定义配置：菜单栏 Preferences - Packages Settings - OmniMarkdownPreviwer - Setting-Default 我直接在默认配置文件上改了，你可以自己复制一份到Setting-user，然后修改对应项。

PS:配置文件有Setting-Default 和Setting-user两个，为防止出错，可以将Setting-Default中的内容复制到Setting-user中来，然后在Setting-user中修改。因为系统会优先读取Setting-user中的配置。

网上看到比较多的配置如下：

```text
"server_host": "127.0.0.1",
//可改为本机IP，局域网其他设备可通过浏览器访问实时预览。例如有时候用iPad当副屏。
    "server_port": 51004,

"renderer_options-MarkdownRenderer": {
        "extensions": ["tables", "fenced_code", "codehilite"]
    }
//解决打开了浏览器但是不能够预览markdown页面的问题,我没遇到所以没用
   

```

### 10. [ConvertToUTF8](https://github.com/seanliang/ConvertToUTF8/blob/master/README.zh_CN.md) &[3](https://github.com/seanliang/Codecs33/blob/master/README.zh_CN.md)

通过本插件，您可以编辑并保存目前编码不被 Sublime Text 支持的文件，特别是中日韩用户使用的 GB2312，GBK，BIG5，EUC-KR，EUC-JP 等。ConvertToUTF8 同时支持 Sublime Text 2 和 3。

### 11. [Codecs3](https://github.com/seanliang/Codecs33/blob/master/README.zh_CN.md)

由于 Sublime Text 3 内嵌的 Python 限制，[ConvertToUTF8](https://github.com/seanliang/ConvertToUTF8) 可能无法正常工作。你可以安装本插件来解决这一问题。

### 12. [Markdown TOC](https://github.com/naokazuterada/MarkdownTOC#usage)

给markdown文件生成目录，且监听自动更新目录变更，可设置目录深度







## 其他需求



