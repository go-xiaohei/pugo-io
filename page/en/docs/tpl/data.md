```toml
title = "页面数据"
desc = "PuGo 主题中的页面里的数据"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 2
```

主题单个页面上的数据分为全局数据和单页数据两部分。全局数据是所有页面都可以访问的。而单页数据根据当前主题页面的渲染用途提供数据。

## 全局数据

参数 | 类型 | 描述 | 默认值
--- | --- | --- | ---
Title | string | 站点的标题 | meta.toml 中 [meta] 的 title
Keyword | string | 站点的关键字 | meta.toml 中 [meta] 的 keyword
Desc | string | 站点的描述 | meta.toml 中 [meta] 的 desc 
Now | time.Time | 当前时间 |  
Base | string | 根目录的相对地址 | meta.toml 中 [meta] 的 url，去掉域名部分
Nav | nav.Group | 导航对象 | meta.toml 中 [[nav]] 数组
Tree | tree.Node | 网站结构对象 | 
Comment | third.Comment | 第三方评论对象 | meta.toml 中 [comment] 
Analytics | third.Analytics | 第三方统计对象 | meta.toml 中 [analytics]
I18n | *i18n.I18n | 国际化对象 | 可能 nil
Meta | *base.Meta | Meta 对象 | meta.toml 中 [meta] 完整数据

例如主题 `meta.html` 的全局数据渲染：

```html
<head>
    <meta charset="UTF-8">
    <title>{{.Title}}</title>
    <meta name="keywords" content="{{.Meta.Keyword}}"/>
    <meta name="description" content="{{.Desc}}"/>
    <link rel="alternate" type="application/rss+xml" title="{{.Title}}" href="{{.Base}}/feed.xml" />
    <link rel="stylesheet" href="{{.Base}}/css/bootstrap.min.css"/>
    <link rel="stylesheet" href="{{.Base}}/css/prism.css"/>
    <link rel="stylesheet" href="{{.Base}}/css/style.css"/>
</head>
```

## 单页数据

单页数据可能会覆盖一些全局数据。

#### post.html

参数 | 类型 | 描述 | 默认值
--- | --- | --- | ---
Post | *post.Post | 文章数据 | 
Title | string | 文章页的标题 | 文章标题 - 站点标题

主题 `post.html` 中使用页面数据：

```html
<article class="article">
    <header class="header">
        <div class="meta">
    <span class="date">
        <span class="month">{{printf "%02d" .Post.CreateTime.Month}}</span>
        <span class="day">{{printf "%02d" .Post.CreateTime.Day}}</span>
    </span>
        </div>
        <h3 class="title">
            <a href="{{FullURL .Post.URL}}">{{.Post.Title}}</a>
        </h3>
    </header>
    <aside class="aside clearfix">
        {{range .Post.Tags}}
        <a class="tag label label-info" href="{{FullURL .URL}}">{{.Name}}</a>
        {{end}}
        {{if .Post.Author}}
        <a class="stat label label-default pull-right"{{if .Post.Author.URL}} href="{{.Post.Author.URL}}" target="_blank"{{end}}>{{.Post.Author.Name}}</a>{{end}}
    </aside>
    <section class="brief">{{.Post.ContentHTML}}</section>
</article>
```

`*post.Post` 的详细说明：

参数 | 类型 | 描述 
--- | --- | --- 
Title | string | 文章的标题
Desc | string | 文章的介绍
Tags | []*post.Tag | 文章的标签列表，可能 nil
Author | *author.Author | 文章的作者，可能 nil
CreateTime | time.Time | 文章的创建时间
UpdateTime | time.Time | 文章的修改时间
Content | []byte | 文章的内容数据
ContentHTML | template.HTML | 文章内容 HTML 类型
Brief | []byte | 文章摘要内容数据
BriefHTML | template.HTML | 文章摘要 HTML 类型
URL | string | 文章的访问链接，需要和 Base 拼接
Index | *index.Index | 文章的目录，可能 nil

#### posts.html

参数 | 类型 | 描述 | 默认值
--- | --- | --- | ---
Pager | *pager.Pager | 当前分页数据 | 
Posts | []*post.Post | 分页列表的文章数组 | 
Title | string | 页面页码 - 站点标题

主题 `posts.html` 中的使用：

```html
{{range .Posts}}
<article class="article">
    <header class="header">
        <div class="meta">
            <span class="date">
                <span class="month">{{printf "%02d" .CreateTime.Month}}</span>
                <span class="day">{{printf "%02d" .CreateTime.Day}}</span>
            </span>
        </div>
        <h3 class="title">
            <a href="{{FullURL .URL}}">{{.Title}}</a>
        </h3>
    </header>
    <section class="brief">{{.BriefHTML}}</section>
    <aside class="aside clearfix">
        <a class="btn btn-primary btn-lg pull-right" href="{{FullURL .URL}}">Read More</a>
    </aside>
</article>
{{end}}
```

分页数据的使用：

```html
<div class="article-pager text-center">
    {{if .Pager.Prev}}<a class="btn btn-lg btn-info" href="{{FullURL .Pager.PrevURL}}">Prev</a>{{end}}
    {{if .Pager.Next}}<a class="btn btn-lg btn-info" href="{{FullURL .Pager.NextURL}}">Next</a>{{end}}
</div>
```

#### archive.html

#### page.html