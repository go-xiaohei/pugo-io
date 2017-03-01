```toml
title = "基本结构"
desc = "PuGo 主题的基本结构"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 1
```

您很容易为 `PuGo` 创建主题。您可以参考默认的 `theme/` 目录，创建自己的主题。主题的基本结构：

    ▸ static/                   静态文件 CSS JS 等的目录            
    ▸ meta.html                 HTML header 头部模板
    ▸ header.html               页面顶部导航模板
    ▸ footer.html               页面底部模板
    ▸ post.html                 文章的模板
    ▸ posts.html                文章列表的模板
    ▸ archive.html              文章归档的模板
    ▸ page.html                 独立页面的模板
    ▸ embed/comment.html        第三方评论的模板，可选嵌入
    ▸ embed/analytics.html      第三方统计的模板，可选嵌入
    ▸ theme.toml                主题的描述文件

以 `post.html` 为例，完整的页面的模板：

```html
{{template "meta.html" .}}
{{template "header.html" .}}
<section id="main">
    <div class="container">
        这里是展示文章内容的 HTML 
        {{template "embed/comment.html" .}}
    </div>
</section>
{{template "footer.html" .}}
```

## 模板语法

`PuGo` 的模板使用 `Go` 语言 `html/template` 模板库的标准语法。如果您对模板的语法不熟悉，可以阅读以下文章，以及 Go 的模板库的官方文档。

- [Golang Template](http://www.jianshu.com/p/bee02c18b221)
- [golang 模板(template)的常用基本语法](http://studygolang.com/articles/8023)

根据 `PuGo` 开发的过程，我提供一些模板语法使用的一些建议：

#### 不要用 define

不要使用 `{{define "sub-template"}}......{{end}}`。

推荐保存为独立的文件如 `sub-template.html`，通过 `{{template "sub-template.html" .}}` 引入。注意结尾的 `.`，将所有数据传递给子模板文件中。

#### 注意作用域

在使用 `{{range .Value}}{{end}}` 和 `{{with .Value}}{{end}}` 的时候，要注意 `range` 和 `with` 之间的部分数据指向当然循环的数据，而不是所有数据。因此需要使用 `{{$.TopValue}}` 来获取外部数据，如：

```html
<ul class="nav navbar-nav">{{range .Nav}}
    <li class="{{if eq .Hover $.Hover}}active{{end}}">
        {{.Title}}
    </li>{{end}}
</ul>
```

## 静态资源

主题需要的静态文件放在 `theme/static/` 目录中，主要在 `meta.html` 和 `footer.html` 中引用，如：

```html
<link rel="stylesheet" href="{{.Base}}/css/bootstrap.min.css"/>
<link rel="stylesheet" href="{{.Base}}/css/prism.css"/>
<link rel="stylesheet" href="{{.Base}}/css/style.css"/>
```

引用时，文件 `theme/static/css/style.css` 在模板中直接 `css/style.css`。