---
layout: post
title:  "Docker proxy config for centos 7"
date:   2017-11-29 21:00:00 +1300
categories: docker container proxy configuration dockerhub hub pull centos centos7
---
# Problem
You're running behind a corporate proxy server and you need docker to be able to pull images on CentOS 7.

Setting the environment variable `http_proxy` or `https_proxy` isn't working.

# Solution
CentOS changed their init system to `systemd` in version 7 and that means to solve this problem you need to make a new file at:
`/etc/systemd/system/docker.service.d/http-proxy.conf`

The contents should contain your proxy server details. Here's mine:

```
[Service]
Environment="HTTP_PROXY=http://127.0.0.1:8000/"
Environment="HTTPS_PROXY=https://127.0.0.1:8000/"
```
