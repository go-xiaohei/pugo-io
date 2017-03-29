```toml
title = "Write a post"
desc = "how to write a post"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 1
lang = "en"
```

You can add a new `.md` file in the `post` directory as a new post. The contents of the post are in `markdown` format. `.md` file name is nothing to the post itself. You need to add the `Front-Meta` content at the beginning of `.md` file, to declare the basic information of this post.

## Front-Meta

`Front-Meta` 是 `.md` 上方以 ```toml 开头包裹的区域，用于说明文章的基本信息，举例如：

    ```toml
    title = "Welcome to PuGo"
    slug = "welcome"
    desc = "welcome to try PuGo static site generator"
    date = "2017-01-01 12:20:20"
    # update_date = "2016-01-01 12:20:50"
    author = "pugo"
    thumb = ""
    tags = ["pugo"]
    draft = false
    ```

这些参数的说明：

参数 | 描述 | 默认值
--- | --- | ---
title | 文章的标题，必填 | 
slug | 文章的唯一链接，必填 |
desc | 文章的描述，可选 | 
date | 文章的创建时间，可选；如果不填，使用文件的创建时间 | 
update_date | 文章的更新时间，可选；如果不设置，同创建时间 | 
author | 文章作者的名称，可选 | 
thumb | 文章的缩略图，可选 | 
tags | 文章的标签，可选；只能是字符串 |
draft | 是否是草稿 | false

#### 生成 HTML

文章的 `.md` 文件根据文章的创建时间和 `slug` 生成对应的 HTML 文件。格式为 `YYYY/M/D/slug.html`，如 `/2017/1/1/welcomd.html`。格式不支持修改。

#### 标签

只有文章支持标签。根据标签，`PuGo` 会生成相同标签（不区分大小写）的文章列表。文章按照时间新旧顺序排列。

## 文章文件的命名

文章的 `.md` 的文件名对文章的标题和生成 HTML 没有影响。您需要自己比较正确的命名文件，否则会引起 `post` 目录内文件的混乱。推荐的方式如：

    ▸ post/2017/1-welcome.md            
    ▸ post/2017/2-new-in-Go18.md           
    ▸ post/2016/1-go-http-server.md

您可以根据年份创建文件夹，文件夹中的 `.md` 文件按照发布顺序编号 1~n，连接文章的简单说明，作为文章文件的命名。

## 文章内的媒体文件

您可能需要会在文章内的 `markdown` 内容中引用图片等媒体资源。`PuGo` 只会处理 `post` 目录中的文章，因此，请将图片等资源保存在 `post` 同级的 `media` 目录中，然后根据图片的内容和文章的信息命名图片文件。比如：
          
    ▸ post/2017/2-new-in-Go18.md           
    ▸ media/2017/2-http-shutdown.png
    ▸ media/2017/2-http2-push.png

然后在 `markdown` 中引用，如：

```markdown
![http2-push](/media/2017/2-http2-push.png)
```


