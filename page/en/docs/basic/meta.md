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

参数 | 描述 | 默认值
--- | --- | ---
title | 站点的标题，必填 | 
subtitle | 站点的副标题，可选 |
keyword | 站点的关键字，可选 | 
desc | 站点的描述，可选 | 
root | 站点的根地址，必填 | http://localhost:9899
lang | 站点的默认语言，可选；如果不设置，不开启国际化支持 | 空

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

参数 | 描述 | 默认值
--- | --- | ---
link | 导航的链接，必填；建议设置确定的 html 文件，目录可以设置 index.html | 
title | 导航的标题，必填 |
i18n | 导航国际化的关键字，可选 | 
hover | 导航选中状态关键字，可选 | 
blank | 导航是否打开新的浏览器标签页 | false

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

参数 | 描述 | 默认值
--- | --- | ---
name | 作者的称呼，必填 | 
email | 作者的联系邮箱，可选 |
url | 作者的联系网址，可选 | 
avatar | 作者的头像，可选；如果为空时 email 存在，使用同 email 的 Gravatar 头像 | 
bio | 作者的个人说明，可选 | 

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
[config]
# 文章的目录
post_dir = "post"
# 页面的目录
page_dir = "page"
# 媒体文件的目录
media_dir = "media"
# 主题的目录
theme_dir = "theme"
# 国际化语言的目录
lang_dir = "lang"
# 输出的目录
output_dir = "dest"
# 文章列表中单页文章的数量
post_pagesize = 4
```