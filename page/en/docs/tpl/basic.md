```toml
title = "Basic Structure"
desc = "PuGo basic structure"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 1
lang = "en"
```

You can create a new theme for `PuGo` easily by reference from default theme in `theme/` directory. The basic structure of theme is :

    ▸ static/                   directory of static file, css, js files 

    ▸ post.html                 template for a post
    ▸ posts.html                template for list of posts
    ▸ archive.html              template for archive of posts
    ▸ page.html                 template for a page

    ▸ embed/meta.html           HTML header meta
    ▸ embed/header.html         page header with title and navigation
    ▸ embed/footer.html         page footer
    ▸ embed/comment.html        template for comment system, optional embbeded
    ▸ embed/analytics.html      template for analytics system. optional embbeded
    
    ▸ theme.toml                description of theme

Such as `post.html` , a whole webpage created by several template files：

```html
{{template "meta.html" .}}
{{template "header.html" .}}
<section id="main">
    <div class="container">
        the content of HTML 
        {{template "embed/comment.html" .}}
    </div>
</section>
{{template "footer.html" .}}
```

## Template Syntax

`PuGo` use `html/template` syntax in Go. You should read official documentation and following articles to learn:

- [Golang Template](http://www.jianshu.com/p/bee02c18b221)
- [golang 模板(template)的常用基本语法](http://studygolang.com/articles/8023)

There are some advices:

#### Do not use define

Do not use `{{define "sub-template"}}......{{end}}`.

It's better to save in template file as `sub-template.html`, and import it as `{{template "sub-template.html" .}}`. Be careful about the ending `.` that means passing current data to the template file.

#### Scopes

When using `{{range .Value}}{{end}}` and `{{with .Value}}{{end}}`, the data in `range` and `with` block are reference to loop data, not root data. You need use `{{$.TopValue}}` to read data out of loop block:

```html
<ul class="nav navbar-nav">{{range .Nav}}
    <li class="{{if eq .Hover $.Hover}}active{{end}}">
        {{.Title}}
    </li>{{end}}
</ul>
```

## Static files

Static files are saved in `theme/static/` directory. You can link them in `meta.html` and `footer.html` page:

```html
<link rel="stylesheet" href="{{.Base}}/css/bootstrap.min.css"/>
<link rel="stylesheet" href="{{.Base}}/css/prism.css"/>
<link rel="stylesheet" href="{{.Base}}/css/style.css"/>
```

The local file `theme/static/css/style.css` is linked as `css/style.css`.