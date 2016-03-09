title: domain-cookie
date: 2016-03-03 11:24:49
tags:
---
1. `domain` 表示的是 `cookie` 所在的域，默认为请求的地址，如网址为 `www.qunar.com/xxx`，那么 `domain` 默认为`www.qunarc.com` 。而跨域访问，如域 A 为 `bnb.qunar.com`，域 B 为 `hotel.qunar.com`，那么在域 A 生产一个令域 A 和域 B 都能访问的 `cookie` 就要将该 `cookie` 的 `domain` 设置为 `.qunar.com` ；如果要在域 A 生产一个令域 A 不能访问而域 B 能访问的 `cookie` 就要将该 `cookie` 的 `domain` 设置为 `hotel.qunar.com`。

2. `path` 表示 `cookie` 所在的目录，`qunar.com` 默认为 `/` ，就是根目录。在同一个服务器上有目录如下：`/test/`, `/test/cd/` , `/test/dd/`，现设一个 `cookie1` 的 `path` 为 `/test/`，`cookie2` 的 `path` 为 `/test/cd/`，那么 `test` 下的所有页面都可以访问到 `cookie1`，而 `/test/` 和 `/test/dd/` 的子页面不能访问 `cookie2`。这是因为 `cookie` 能让其 `path` 路径下的页面访问。

3. 浏览器会将 `domain` 和 `path` 都相同的 `cookie` 保存在一个文件里，`cookie` 间用 `*` 隔开。