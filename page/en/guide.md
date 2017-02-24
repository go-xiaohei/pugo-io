```toml
title = "快速入门"
desc = "PuGo 的快速入门"
author = "pugo"
hover = "guide"
template = "guide.html"
```

本文将带您快速上手 `PuGo`。如果您在操作过程中遇到问题，请查看 [疑难问题](#) 中的解答，或者在 GitHub、Google Group 上提问。

# 安装

安装 `PuGo` 非常简单。您访问 [官网](http://pugo.io) 下载对应系统的压缩 Zip 文件，解压就可以使用。Windows 下执行文件为 `pugo.exe`，Linux 和 MacOS 下执行文件为 `pugo`。

### 创建站点

`PuGo` 可以创建默认的站点框架，在终端运行：

    pugo init

`PuGo` 会在当前目录创建内容。

### 站点结构

新创建的站点目录结构如下：

    ▸ post/             文章的目录
    ▸ page/             页面的目录
    ▸ theme/            主题的目录
    ▸ media/            媒体文件的目录
    ▸ lang/             语言文件的目录
    meta.toml           配置文件

当前的站点有一篇文章和一个页面，并进行默认的配置。

# 创建内容

`PuGo` 是用 `markdown` 作为内容文件，后缀 `.md`。在 `post` 目录中创建 `my-first-post.md` 文件。文件开头填入 `Front-Meta` 注明文章的基本信息。

```toml
# 文章标题，必填
title = "我的第一篇文章"

# 文章的访问链接，注意 URL 的字符规则，必填
slug = "my-first-blog"

# 文章的一句话介绍
desc = "这是我的第一篇文章"

# 文章的撰写时间，格式支持如：
# 2015-11-28, 2015-11-28 12:28, 2015-11-28 12:28:38
date = "2017-01-01 12:20:20"

# 文章的修改时间，可选
# if null, use created time
# update_date = "2016-01-01 12:20:20"

# 文章的作者称呼，与 meta.toml 中对应
author = "pugo"

# 文章的缩略图地址
thumb = ""

# 文章的标签，都是字符串
tags = ["post","first","pugo"]

# 草稿状态；如果 true ，将不处理这篇文章
draft = false
```

`Front-Meta` 内容包括在 ```toml 的 markdown 语法块中。之后就是文章的正文，支持任意 markdown 内容。

# 运行站点

在终端运行：

    pugo server

`PuGo` 将处理所有内容到静态 HTML 文件，输出到 `dest` 目录，并启动 HTTP 服务。使用浏览器访问 `http://localhost:9899` 可以预览刚刚添加的文章。

# 下一步

您可能还需要了解更多 `PuGo` 的使用。可以查询详细的文档帮助您操作：

- [添加一个页面](#)
- [修改站点配置](#)
- [修改模板文件](#)

# 疑难问题

- too many open files

- fsnotify
