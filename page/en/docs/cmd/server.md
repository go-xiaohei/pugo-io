```toml
title = "服务器"
desc = "PuGo server 启动服务器的命令"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 1
```

使用 `server` 命令启动 HTTP 服务：

    pugo server

执行时会立刻生成静态内容，然后启动 HTTP 服务。您可以在浏览器访问 `http://localhost:9899/` 浏览内容。

## 服务器地址

如果您需要更改端口，可以设置 `--addr` 指定其他端口。

    pugo server --addr="0.0.0.0:9099" 

端口地址设置为 `127.0.0.1:9099` 时，只能内网访问。指定 IP 地址时，可以设置为如 `192.30.252.12:9099`。

## 开发调试

如果您想查看 `server` 运行时的情况，或者执行 `server` 发生问题，可以添加 `--debug` 输出更多的调试信息用于检查和反馈：

    pugo server --debug