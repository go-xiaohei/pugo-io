```toml
title = "导航数据"
desc = "PuGo 主题的导航数据和站点结构数据"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 4
lang = "zh-cn"
```

导航数据分为两个部分。一是 `meta.toml` 中的导航数据；另一是全局数据中 `{{.Tree}}` 站点页面结构生成的导航。

## 导航数据

全局导航数据在 `{{.Nav}}` 中，任何页面都可以访问。在主题 `header.html` 渲染导航的用法：

```html
<ul class="nav nav-inverse nav-pills">{{range .Nav}}
    <li role="presentation" class="{{if eq .Hover $.Hover}}active{{end}}">
        <a href="{{FullURL .Link}}" {{if .IsBlank}} target="_blank" {{end}}>{{if .Icon}}
            <i class="{{.Icon}}"></i>{{end}}{{.Title}}
        </a>
    </li>{{end}}
</ul>
```

单个导航对象的说明：

参数 | 类型 | 描述
--- | --- | --- 
Link | string | 导航的链接
Title | string | 导航的标题
Hover | string | 导航选中状态关键字
Icon | string | 导航图标的 CSS 类

一些模板会提供全局数据 `{{.Hover}}` 如独立页面的模板，您需要与导航对象中的 Hover 对比判断是否是选中状态。

## Tree

`{{.Tree}}` 是特殊的数据。因为保存有全站的页面网络数据，所以可以渲染任意层级的页面节点作为导航列表。例如文档侧边栏导航的渲染：

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

Tree 的详细说明：

参数 | 类型 | 描述
--- | --- | --- 
Child | []*node.Node | 当前节点的子节点列表
Title | string | 当前节点的标题
URL | strig | 当前节点的URL，需要连接 .Base
Is(string) | bool | 判断是某种类型的节点，有 post,page,archive,post-list,xml,nil

全局对象 `{{.Tree}}` 是一个根节点，没有标题。