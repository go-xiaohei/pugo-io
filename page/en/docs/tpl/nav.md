```toml
title = "Navigation"
desc = "navigation and index data in PuGo template"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 4
lang = "en"
```

There are two parts of navigation data. One is global navigation from `meta.toml`. Another is site pages structure from `{{.Tree}}`.

## Navigation

Global navigation are provided from `{{.Nav}}` and can be visited in all templates. For example, navigation data in `header.html`:

```html
<ul class="nav nav-inverse nav-pills">{{range .Nav}}
    <li role="presentation" class="{{if eq .Hover $.Hover}}active{{end}}">
        <a href="{{FullURL .Link}}" {{if .IsBlank}} target="_blank" {{end}}>{{if .Icon}}
            <i class="{{.Icon}}"></i>{{end}}{{.Title}}
        </a>
    </li>{{end}}
</ul>
```

Fields of one navigation:

parameter | type | description
--- | --- | --- 
Link | string | link of nav
Title | string | title of nav
Hover | string | hover keyword of nav
Icon | string | icon css class of nav

When some templates set `{{.Hover}}`, use `{{if eq .Hover $.Hover}}` to check whether the page's hover should notice global navigation.

## Tree

`{{.Tree}}` is special data. It provides all nodes data as site structure. You can render any navigation for any level by `{{.Tree}}`. For example, sidebar navigation in documentation site:

```html
{{with $w := .Tree.Child "en/docs"}} {{if $w}} {{range $w.Children}}
<li>
    {{if .Is "nil"}}
    <a href="#">{{.Title}}</a> {{else}}
    <a href="{{FullURL .URL}}">{{.Title}}</a> {{end}} {{if .Children}}
    <ul class="nav nav-pills nav-stacked">
        {{range .Children}}
        <li> {{if .Is "nil"}}
            <a href="#">{{.Title}}</a> {{else}}
            <a href="{{FullURL .URL}}">{{.Title}}</a> {{end}}
        </li> {{end}}
    </ul>{{end}}
</li>
{{end}} {{end}} {{end}}
```

Tree Fields:

parameter | type | description
--- | --- | --- 
Child | []*node.Node | children of this node
Title | string | title of node
URL | strig | url of the node, concat with .Base
Is(string) | bool | Check node's type, support post,page,archive,post-list,xml,nil

Root node of `{{.Tree}}` is empty node, without title and url.