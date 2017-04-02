```toml
title = "Meta file"
desc = "configuration in meta file"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 3
lang = "en"
```

`PuGo` site configuration is stored in `meta.toml`' in `toml` format. Before compiling the site content, you need to modify to ensure that the correct pages are generated.

## Basic Information

`PuGo` basic information is defined in the `[meta]` section :

```toml
[meta]
title = "PuGo"
subtitle = "Just for Writing"
keyword = "PuGo,Golang,Static,Website"
desc = "PuGo is a simple static site generator"
root = "http://pugo.io/"
lang = ""
```

Description:

parameter | descripiton | default value
--- | --- | ---
title | the title of the site, required | 
subtitle | the subtitle of the site, optional |
keyword | the keyword of the site, optional | 
desc | the description, optional | 
root | the root url for the site, required | http://localhost:9899
lang | global language name. If empty, do not run internationlization | empty

## Navigation

Global navigation is stored in `[[nav]]` with an array, such as:

```toml
[[nav]]
link = "/guide.html"
title = "Guide"
i18n = "guide"
hover = "guide"
blank = false

[[nav]]
link = "/docs/index.html"
title = "Docs"
i18n = "docs"
hover = "docs"
```

Description:

parameter | descripiton | default value
--- | --- | ---
link | link of navgiation item. Use specific HTML file url, even index.html | 
title | title of navigation item, required |
i18n | keyword for internationlisation, optional | 
hover | keyword for hover status, optional | 
blank | open page with new browser tab | false

There is only one level for navigations. They are iterated as adding order.

## Author

Authors are an array data saved in `[[author]]` section:

```toml
[[author]]
name = "pugo"
email = ""
url = "http://pugo.io"
avatar = "/media/author.png"
bio = "the robot of pugo, who generates all default contents."
```

Description:

parameter | descripiton | default value
--- | --- | ---
name | author's name, required | 
email | author's email, optionsal |
url | author's persion site url, optional | 
avatar | author's avatar, optional. When empty, try to use Gravatr image by email| 
bio | author's simple profile, optional | 

You can add several authors. The first one is **default author**. In post and page, set `author = "pugo"` to an author by same name. If no author in post and page, use **default author**.

## Third-party

`PuGo` provides support for third-party comments and analytics systems, defined under `[comment]` and `[analytics]` section, such as:

```toml
[comment]
# disqus.com site name
disqus = ""
# duoshuo.com short name
duoshuo = ""

[analytics]
# google analytics, need as UA-XXXXX-Y
google = ""
# baidu analytics, need [hash-code] in hm.js?[hash-code]
baidu = ""
# Tencent Analytics, need your_sid in http://tajs.qq.com/stats?sId?SId=your_sid
tencent = ""
```

In `theme/embed/comment.html` and `theme/embed/analytics.html` file `PuGo` provides default javascript code for third systems. You can customize your code refer to these files.

## Compilation configuration

The compilation configuration sets the parameters to change the compilation behavior. **Do not modify** in general.

```toml
[config]
# directory of posts
post_dir = "post"
# directory of pages
page_dir = "page"
# directory of media files
media_dir = "media"
# directory of theme
theme_dir = "theme"
# directory of language files
lang_dir = "lang"
# directory for compiled HTML files
output_dir = "dest"
# size of posts for a post list page
post_pagesize = 4
```