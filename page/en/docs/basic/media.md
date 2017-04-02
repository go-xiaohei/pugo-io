```toml
title = "Media files"
desc = "media files ans static files"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 4
lang = "en"
```

## Media Files

The media files are saved in `media/` direcotry. When compiling, `PuGo` copies `media/` to destination directory. You can add them into `markdown` content:

```markdown
![image](/media/image.png)
```

#### Relative path

You can set global url path for the site in `meta.toml` (root = "http://localhost:9899"). But if set a url with sub-directory:

```toml
root = "http://pugo.io/blog"
```

You need change your reference in markdown:

```markdown
![image](/blog/media/image.jpg)
```

## Statis assets

Some statis assets are used by theme in `theme/static/` directory. `PuGo` copies `theme/static/` and extracts to top level in destination directory. Some files can store in this directory if it need be visisted in root url, such as `robots.txt`.

For example: `theme/static/robots.txt` is copied to `dest/robots.txt`。
