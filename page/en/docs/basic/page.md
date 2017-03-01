```toml
title = "添加页面"
desc = "如果添加页面"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 2
```

您可以在 `page` 目录添加新的 `.md` 文件，作为一篇新的页面。页面和文章很相似，使用 `markdown` 格式，需要 `Front-Meta` 定义基本信息。

## Front-Meta

`Front-Meta` 和文章的类似，字段略有不同。例如：

    ```toml
    title = "About PuGo"
    slug = ""
    desc = "about pugo project"
    date = "2017-01-01 12:20:20"
    # update_date = "2016-01-01 12:20:50"
    author = "pugo"
    draft = false
    hover = "about"
    template = "page.html"
    sort = 2
    node = false
    json = "about.json"
    ```

这些参数的说明：

参数 | 描述 | 默认值
--- | --- | ---
title | 页面的标题，必填 | 
slug | 页面的唯一链接，可选 |
date | 页面的创建时间，可选；如果不设置，读取文件的最新修改时间 | 
update_date | 页面的更新时间，可选；如果不设置，同创建时间 | 
author | 页面作者的名称，可选 | 
draft | 是否是草稿 | false
hover | 页面的选中状态关键字，可选 | 
template | 页面的模板文件，可选 | page.html
sort | 页面的排序数，可选 | 0
node | 是否是节点 | false
json | 页面引入的 JSON 数据文件，可选 | 

#### 生成 HTML

页面生成 HTML 有两种规则。

- 页面的 `slug` 存在时，以 `[slug].html` 生成。
- 页面的 `slug` 不存在时，以 `.md` 文件相对于 `page` 目录的地址，生成 HTML文件。

如 `/page/docs/index.md` 生成的 HTML 文件是 `/docs/index.html`。 HTML 的文件名和 `.md` 相同。

#### 页面模板

页面默认的模板文件是 `page.html`。您可以修改 `template = "docs.html"` 指定别的模板文件 `docs.html` 作为此页面的渲染模板。指定的模板必须在主题中存在。

#### 排序数

排序数使用与生成全站节点时，为了同一层次的节点排序使用的。值越小权重越高，位置越前。

#### 节点模式

您如果设置为页面设置 `node = true`，页面就不会被认为需要渲染，只用读取 `Front-Meta`。

#### JSON 数据

如果您需要给页面添加额外的数据，可以设置 `json = "about.json"` 加载 JSON 数据文件。JSON 文件保存在 `page` 目录中，地址相对于 `page` 目录（如 `/page/about.json`），而不是页面文件。只支持加载一个 JSON 文件。

## 页面的文件命名

因为页面文章的名称和生成 HTML 的地址相关，所以文件名称推荐使用 URL 中合法的符号（如 `#` 是不行的)。而且目录的层级就是地址的层级，所以您规划好页面的网络，就是文件目录的结构了。

## 页面的媒体文件

页面中的媒体文件和文章一样，都存放在 `media` 目录中。


