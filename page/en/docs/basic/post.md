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

Front-Meta is at the beginning of the `.md` file wrapped with ```toml, which is used to describe the basic information of the post. For example:

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

Description:

parameter | description | default value
--- | --- | ---
title | the title of the post, required | 
slug | the unique link of the post, required |
desc | the description, optional | 
date | created time; if empty, use file modified time | 
update_date | updated time; if empty, same to created time | 
author | author's name, optional | 
thumb | thumb image, optional | 
tags | tags, options; must be string |
draft | draft status | false

#### Generating HTML

Post generates HTML file with created time and slug value, as  `YYYY/M/D/slug.html` (like `/2017/1/1/welcomd.html`). **Can not** change the rule now.

#### Tags

Tags is only available for post. According tag, `PuGo` can generated posts list with same tag (case-insensitive) order by later created time.

## Nameing

The `.md` filename has nothing to HTML filename。You need manage filenames in order to avoid maddness. There is a useful way:

    ▸ post/2017/1-welcome.md            
    ▸ post/2017/2-new-in-Go18.md           
    ▸ post/2016/1-go-http-server.md

You can create directory by year, add md file by number and name it with simple words in the post.

## Media Files

You may need to add to media files in `markdown` content in the post. `PuGo` only deals with posts in the` post` directory, so save the images and other resources in the `media` directory. And nameing the file according to the post using the file. Such as:
          
    ▸ post/2017/2-new-in-Go18.md           
    ▸ media/2017/2-http-shutdown.png
    ▸ media/2017/2-http2-push.png

markdown code:

```markdown
![http2-push](/media/2017/2-http2-push.png)
```


