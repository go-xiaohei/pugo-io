```toml
title = "Server"
desc = "PuGo server starts http server"
author = "pugo"
hover = "docs"
template = "docs.html"
sort = 1
lang = "en"
```

Use `server` command to start HTTP server：

    pugo server

When run `server`, `PuGo` compiles contents then starts HTTP server. You can preview the site in browser by visiting `http://localhost:9899/`.

## Address

Change HTTP server address and port by  `--addr` flag:

    pugo server --addr="0.0.0.0:9099" 

When address is `127.0.0.1:9899`, it only can be visited in local network. You should set `0.0.0.0:9099` to grant access for public.

## Debug

If something wrong happens when running `server`, You can add `--debug` flag to print more debug information for feedback.

    pugo server --debug