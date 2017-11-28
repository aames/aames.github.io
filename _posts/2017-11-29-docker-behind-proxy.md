---
layout: post
title:  "Docker proxy config for centos 7 (or any systemd based distro)"
date:   2017-11-29 21:00:00 +1300
categories: docker container proxy configuration dockerhub hub pull systemd centos centos7
---
# Problem
You're running behind a corporate proxy server and you need docker to be able to pull images on CentOS 7 (or any other systemd based distro).

Setting the environment variable `http_proxy` or `https_proxy` isn't working.

# Solution for systemd based Linux distributions
CentOS changed their init system to `systemd` in version 7 and that means to solve this problem you need to make a new file at:
`/etc/systemd/system/docker.service.d/http-proxy.conf`

The contents should contain your proxy server details. Here's mine:

```
[Service]
Environment="HTTP_PROXY=http://127.0.0.1:8000/"
Environment="HTTPS_PROXY=https://127.0.0.1:8000/"
```

# More

Full docs from Docker are currently available at [https://docs.docker.com/engine/admin/systemd/](https://docs.docker.com/engine/admin/systemd/)
