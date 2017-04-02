```toml
title = "Build"
desc = "PuGo build command"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 1
lang = "en"
```

Use `build` to compile contents to HTML files：

    pugo build

All HTML files are generated into `dest/` directory. These files are whole website contents. You can start a website in this directory.

## Initial

When run `build`, you need provide contents to build. Run `init` to generate default contents. Then you can mofidy and add more contents by yourself.

    pugo init

If `meta.toml` is existed, can not run `init` to generate new default contents. You should cleanup old data before running `init`.

## Watching

`PuGo` can watch content files and compile immediately when some changes occur.

    pugo build --watch

## Debug

If something wrong happens when running `build`, You can add `--debug` flag to print more debug information for feedback.

    pugo build --debug