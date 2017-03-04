```toml
title = "静态文件"
desc = "媒体文件和静态文件"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 4
lang = "zh-cn"
```

## 媒体文件

媒体文件存放在 `media/` 目录。编译内容时，`PuGo` 会拷贝 `media/` 目录的内容到站点。您在文章或页面的 `markdown` 内容中引用：

```markdown
![image](/media/image.png)
```

#### 相对地址

在全局配置 `meta.toml` 中，可以设置站点的根地址。如果您设置的根地址有子目录，会影响资源目录的引用地址。如 `meta.toml` 中：

```toml
root = "http://pugo.io/blog"
```

在文章或页面中引用的时候，您需要填写正确的相对地址，即：

```markdown
![image](/blog/media/image.jpg)
```

## 静态资源

另一部分的静态资源是主题依赖的静态资源，在 `theme/static/` 目录中。编译内容时，`theme/static/` 会展开子目录到输出的根目录。因此有些如 `robots.txt` 等需要在根目录访问的内容，您可以放在这个目录。

如 `theme/static/robots.txt` 输出到 `dest/robots.txt`。
