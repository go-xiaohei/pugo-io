```toml
title = "Add a page"
desc = "how to add a page"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 2
lang = "en"
```

You can add a new `.md` file in the `page` directory as a new page. Page and post are very similar and same in `markdown` format. You need add `Front-Meta` to define basic information.

## Front-Meta

`Front-Meta` is similar to post but some fields are slightly different.

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

Description:

parameter | description | default value
--- | --- | ---
title | title of page, required | 
slug | unique slug of page, required |
date | created time; if empty, use file modified time | 
update_date | updated time; if empty, same to created time | 
author | author's name, optional | 
draft | draft status | false
hover | selected status keyword for navigation, optional | 
template | template file name, optional | page.html
sort | order number, optional | 0
node | node status | false
json | related json file data, optional | 

#### Generating HTML

There are two ways to generate HTML file:

- if `slug` is set，generate as `[slug].html`.
- if `slug` is **not** set，use relate path between `.md` file and `page` directory to generate.

For example, `/page/docs/index.md` generates html to `/docs/index.html`. HTML file's name is same to `.md` file.

#### Templaate

The default template for page is `page.html`。You can set `template = "docs.html"` to use `docs.html` as template file. The template file must be existed in theme directory.

#### Order number

Order number is used to set order of pages when generating node tree. More less, more important.

#### Node mode

When you set `node = true`，it will not be compiled to html, but read `Front-Meta` and generate node into tree.

#### JSON data

If you want to import extra data into page, set `json = "about.json"` to load extra json file. JSON file need save in `page` directory and use value of related path by `page` directory ( `/page/about.json`). Only support to load one json file.

## Naming

Because the name of the page is related to the generated HTML address, it is recommended to use legal symbols in the URL (for example, `#`is not available) as filename. And the level of the directory is the address level, so the pages' addresses structure is same of the file directory.

## Media files

Same to post, media files save in `media` directory.


