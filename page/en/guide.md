```toml
title = "Quick Start"
desc = "a simple guideline for PuGo"
author = "pugo"
hover = "guide"
template = "guide.html"
lang = "en"
```

This article will take you to get started with `PuGo`. If you're having trouble, check out the answers in [FAQ] (#), or ask questions on GitHub.

# Installataion

It's very simple to installing `PuGo`. You visit the [official website] (http://pugo.io) and download the compression file Zip file. Then extract it and run executable file. The file `pugo.exe` is binary file on Windows. On Linux and MacOS it's `pugo`.

### Create new site

`PuGo` can create default website. Run command in terminal：

    pugo init

`PuGo` will initialize default contents in current directory.

### Site structure

The directories of default website:

    ▸ post/             directory of articles
    ▸ page/             directory of pages
    ▸ theme/            directory of theme
    ▸ media/            directory of media files
    ▸ lang/             directory of language fiels
    meta.toml           configuration file

There are a post, a page and correct configuration file in default website.

# Create new content

The content of `PuGo` is in `markdown` format `.md`。Write a new file `my-first-post.md` in `post` directory. Add `Front-Meta` to define basic infomation of the article.

```toml
# title of the article, required
title = "My first post"

# the visitable link of the article, required
slug = "my-first-blog"

# a sentence describing the article
desc = "this is my first post"

# the creating time of the article, layout as following:
# 2015-11-28, 2015-11-28 12:28, 2015-11-28 12:28:38
date = "2017-01-01 12:20:20"

# the modifying time of the article, optional
# if null, use created time
# update_date = "2016-01-01 12:20:20"

# the author'name of the article, defined in meta.toml
author = "pugo"

# the thumb image of the article
thumb = ""

# the tags of the article
tags = ["post","first","pugo"]

# draft status. If true, the article will not be compiled
draft = false
```

`Front-Meta` is defined in block ```toml in markdown file. Then write real content of the article.

# Run site

Run in command:

    pugo server

`PuGo` compiles contents to HTML files into `dest` directory, and starts HTTP server. Preview contents by visiting `http://localhost:9899` in browser.

# Next

If you want more `PuGo` usage, read following documents:

- [add a new page](#)
- [modify configuration file](#)
- [customize theme](#)

# FAQ

- too many open files

- fsnotify
