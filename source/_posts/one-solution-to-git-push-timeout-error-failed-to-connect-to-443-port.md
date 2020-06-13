---
title: One Solution to Git Push Timeout Error Failed to connect to 443 port
author: Jun Hu
tags:
  - Git
date: 2020-06-13 18:11:48
---

When I tried to push a new post to the Github, I received below error message.
`Failed to connect to github.com port 443: Timed out`


<!-- more -->

So I tried to fix it with updating the proxy setting within the git config.

>http.proxy
Override the HTTP proxy, normally configured using the http_proxy, https_proxy, and all_proxy environment variables (see curl(1)). In addition to the syntax understood by curl, it is possible to specify a proxy string with a user name but no password, in which case git will attempt to acquire one in the same way it does for other credentials. See gitcredentials(7) for more information. The syntax thus is [protocol://][user[:password]@]proxyhost[:port]. This can be overridden on a per-remote basis; see remote.<name>.proxy

For me, it's as simple as `git config --global http.proxy 127.0.0.1:8087`.

---


Reference:


*- [Some discussions on the stack overflow](https://stackoverflow.com/questions/18356502/github-failed-to-connect-to-github-443-windows-failed-to-connect-to-github)*

