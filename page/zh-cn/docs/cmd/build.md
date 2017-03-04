```toml
title = "生成"
desc = "PuGo build 生成命令"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 1
lang = "zh-cn"
```

使用 `build` 命令可以快速生成静态 HTML 内容：

    pugo build

生成的内容在 `dest/` 目录中，是完整的静态网站内容，可以直接部署。

## 初始化站点

`build` 执行时，需要预先创建好站点的内容。您可以执行 `init` 命令创建默认内容，进行修改，然后生成。

    pugo init

如果当前目录已经有 `meta.toml`，会提示已经存在站点，无法执行 `init`。请您清理好数据后重新 `init`。

## 监听变化

`PuGo` 能监听内容文件的变动并立即生成新的静态文件：

    pugo build --watch

## 开发调试

如果 `build` 过程发生问题，您可以让 `PuGo` 输出更多的调试信息用于检查和反馈：

    pugo build --debug