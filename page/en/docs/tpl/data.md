```toml
title = "Data in Template"
desc = "major data in template files"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 2
lang = "en"
```

The data on a single template are divided into global and single-page data. Global data are accessible to all templates. The single-page data are based on the rendering purpose of the current theme page.

## Global Data

parameter | type | description | default value
--- | --- | --- | ---
Title | string | the title of site | title in [meta] from meta.toml
Keyword | string | the keyword of site | keyword in [meta] from meta.toml
Desc | string | the description of site | desc in [meta] from meta.toml
Now | time.Time | current time when generating the template |  
Base | string | relative path | url without hostname in [meta] from meta.toml
Nav | nav.Group | navigation data | array data of [[nav]] from meta.toml
Tree | tree.Node | tree nodes data | 
Comment | third.Comment | third-party comment data | [comment] from meta.toml
Analytics | third.Analytics | third-party analytics | [analytics] from meta.toml 
I18n | *i18n.I18n | internationlization  | maybe nil
Meta | *base.Meta | meta data | all data as a map in [meta] from meta.toml

For example, use global data in template `meta.html`:

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

## Single-page data

Single-page data overwrite some values from global data.

#### post.html

parameter | type | description | default value
--- | --- | --- | ---
Post | *post.Post | post data | 
Title | string | title of the post | post title - site name

Use post data in template `post.html`:

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

Values in `*post.Post`:

parameter | type | description 
--- | --- | --- 
Title | string | title of post
Desc | string | description of post
Tags | []*post.Tag | tags of post, maybe nil
Author | *author.Author | author of post, maybe nil
CreateTime | time.Time | created time of post
UpdateTime | time.Time | latest updated time of post
Content | []byte | content bytes
ContentHTML | template.HTML | content bytes as html string
Brief | []byte | brief bytes of content
BriefHTML | template.HTML | brief byts as html string
URL | string | url of post, join with {{.Base}}
Index | *index.Index | index of post, maybe nil

#### posts.html

parameter | type | description | default value
--- | --- | --- | ---
Pager | *pager.Pager | current pager data | 
Posts | []*post.Post | posts list in current pager | 
Title | string | pager current number - site name

Use in `posts.html`:

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

Use {{.Pager}}:

```html
<div class="article-pager text-center">
    {{if .Pager.Prev}}<a class="btn btn-lg btn-info" href="{{FullURL .Pager.PrevURL}}">Prev</a>{{end}}
    {{if .Pager.Next}}<a class="btn btn-lg btn-info" href="{{FullURL .Pager.NextURL}}">Next</a>{{end}}
</div>
```

#### archive.html

parameter | type | description | default value
--- | --- | --- | ---
Archives | []*archive.Archive | list of archive posts | 
Hover | string | hover keyword of archive page | archive 
Title | string | Archive - site title

Sampe of `archive.html`:

```html
<div id="archive-list">
    {{range .Archives}}
    <div class="archive">
        <h3>{{.Period}}</h3>
        <hr/>
        {{range .Posts}}
        <h4>
            <span class="date">{{printf "%02d" .CreateTime.Month}}.{{printf "%02d" .CreateTime.Day}}</span>
            <a href="{{FullURL .URL}}">{{.Title}}</a>
        </h4>
        {{end}}
    </div>
    {{end}}
</div>
```

#### page.html

parameter | type | description | default value
--- | --- | --- | ---
Page | *page.Page | page data | 
Title | string | title of the page | page title - site title
Hover | string | hover keyword of this page | .Page.Hover

Sample of `page.html`, familiar to post template:

```html
<header class="header">
        <div class="meta">
            <span class="date">
                <span class="month">{{printf "%02d" .Page.CreateTime.Month}}</span>
                <span class="day">{{printf "%02d" .Page.CreateTime.Day}}</span>
            </span>
        </div>
        <h3 class="title">
            <a href="{{.Page.URL}}">{{.Page.Title}}</a>
        </h3>
    </header>
    {{if .Page.Author}}<aside class="aside clearfix">
        <a class="stat label label-default pull-right"{{if .Page.Author.URL}} href="{{.Page.Author.URL}}" target="_blank"{{end}}>{{.Page.Author.Name}}</a>
    </aside>{{end}}
    <section class="brief">{{.Page.ContentHTML}}</section>
</div>
```

`*page.Page` fields:

parameter | type | description 
--- | --- | --- 
Title | string | title of the page
Desc | string | description of the page
Author | *author.Author | author of the page, maybe nil
CreateTime | time.Time | created time of the page
UpdateTime | time.Time | modifed time of the page
Content | []byte | content of the page
ContentHTML | template.HTML | content of the page as HTML type
URL | string | visited url, concated with Base url
Index | *index.Index | index of the page, maybe nil
JSON | *page.JSON | extra JSON of the page, maybe nil