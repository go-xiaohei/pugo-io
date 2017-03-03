```toml
title = "模板函数"
desc = "PuGo 主题中的模板辅助函数"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 3
```

`PuGo` 在主题中提供了几个辅助函数，简化操作：

#### HTML

`HTML([]byte/string)` 将文本或字节转化为 HTML 类型输出，防止被安全转义到纯文本：

```html
<div class="content">{{HTML .Post.Content}}</div>
```

    PS: {{.Post.ContentHTML}} 就是这个过程。模板可以直接使用。

#### FullURL

`FullURL(string)` 拼接 URL 和 {{.Base}}，生成完整的访问地址：

```html
<a href="{{FullURL .Post.URL}}">{{.Post.Title}}</a>
```

所有数据输出的 URL 都需要用 FullURL 处理来保证正确性。