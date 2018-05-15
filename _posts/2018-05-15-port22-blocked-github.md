---
layout: post
title:  "Port 22 is blocked, how can I push to Git with SSH?"
date:   2018-05-15 14:00:00 +1300
categories: git github
---
# Problem

You know the drill, you're working on a network and you push/pull from git.

```
git push -u origin master
ssh: connect to host github.com port 22: Operation timed out
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

You see the dreaded timeout and realise...

> They've blocked port 22?

Fear not.

# Solution

Use port 443 instead. _for ssh?_ Yes!

edit `~/.ssh/config` and append the following

```
Host github.com
  Hostname ssh.github.com
  Port 443
```

Save, exit and retry.

If port 443 is blocked. Fetch coffee.
