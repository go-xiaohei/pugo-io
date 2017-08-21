```toml
title = "Template functions"
desc = "helper functions in PuGo templates"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 3
lang = "en"
```

`PuGo` provides some helper function for templating:

#### HTML

`HTML([]byte/string)` converts bytes to HTML type, avoid safe escaping：

```html
<div class="content">{{HTML .Post.Content}}</div>
```

    PS: {{.Post.ContentHTML}} had beed converted.

#### FullURL

`FullURL(string)` concats URL and {{.Base}} to full url:

```html
<a href="{{FullURL .Post.URL}}">{{.Post.Title}}</a>
```

You must use FullURL to build safe and correct url.