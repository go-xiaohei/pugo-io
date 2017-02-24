```toml
title = "全站配置"
desc = "全站 meta 文件的配置信息"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 3
```

`PuGo` 的站点配置信息保存在 `meta.toml` 中，为 `toml` 格式。编译站点内容之前，您需要修改一些配置信息，保证生成正确的页面。

## 基本信息

`PuGo` 的站点基本信息定义在 `[meta]` 内容下，如：

```toml
[meta]
title = "PuGo"
subtitle = "Just for Writing"
keyword = "PuGo,Golang,Static,Website"
desc = "PuGo is a simple static site generator"
root = "http://pugo.io/"
lang = ""
```

具体的说明：

## 导航

全局导航信息定义在 `[[nav]]` 内容中，是一组数据，如：

```toml
[[nav]]
link = "/guide.html"
title = "Guide"
i18n = "guide"
hover = "guide"
blank = false

[[nav]]
link = "/docs/index.html"
title = "Docs"
i18n = "docs"
hover = "docs"
```

具体的说明：

导航只支持一个层级，顺序按照定义的先后。

## 作者

作者信息定义在 `[[author]]` 内容中，是一组数据，如：

```toml
[[author]]
name = "pugo"
email = ""
url = "http://pugo.io"
avatar = "/media/author.png"
bio = "the robot of pugo, who generates all default contents."
```

具体的说明：

作者可以多个。第一个作者为**默认作者**。文章和页面中通过 `author = "pugo"` 来对应某个作者。如果文章和页面不指定作者，将自动设置为**默认作者**。

## 第三方系统

`PuGo` 提供了第三方评论和统计系统的支持，分别定义在 `[comment]` 和 `[analytics]` 内容下，如：

```toml
[comment]
# disqus.com site name
disqus = ""
# duoshuo.com short name
duoshuo = ""

[analytics]
# google analytics, need as UA-XXXXX-Y
google = ""
# baidu analytics, need [hash-code] in hm.js?[hash-code]
baidu = ""
# Tencent Analytics, need your_sid in http://tajs.qq.com/stats?sId?SId=your_sid
tencent = ""
```

`PuGo` 在主题 `theme/embed/comment.html` 和 `theme/embed/analytics.html` 文件提供默认的评论和统计嵌入代码。如果您需要自定义，可以参考主题文件进行修改。

## 编译配置

编译配置可以设置编译过程中依赖的参数。**一般情况下不要修改**。

```toml
# configuration settings
# please do not modify settings
# if need change values, read documentation carefully
[config]
# directory of posts
post_dir = "post"
# directory of pages
page_dir = "page"
# directory of media
media_dir = "media"
# directory of theme
theme_dir = "theme"
# directory of language
lang_dir = "lang"
# directory of static site output files
output_dir = "dest"
# post page size
post_pagesize = 4
```