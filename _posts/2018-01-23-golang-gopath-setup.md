---
layout: post
title:  "Learning Golang: godep unable to find srcroot"
date:   2018-01-23 14:00:00 +1300
categories: golang dependency management godep
---
# Introduction
I consider myself to be a polyglot - I enjoy learning new programming languages and I've recently decided to teach myself some [go](https://golang.org).

# Problem
- You've decided that it's time to get some dependency management in place for your go projects.
- You've selected the popular [godep](https://github.com/tools/godep) tool.
- You navigate to your chosen project folder and...
- Error: `godep unable to find srcroot`

# Solution
Filesystem location matters a lot in Go. You're expected to be running things from a designated 'gopath', but don't confuse _gopath_ with the location of `go` (don't just set it to where go is installed).

Your _gopath_ should be a location that you're happy to put your go source code for the foreseeable future. I've set mine to `/Users/andrew/go`.

```
cat <<END >> ~/.bashrc
export GOPATH=/Users/andrew/go
END
```

This works for *zsh* also, simply change the filename as appropriate (to `~/.zshrc`). Simply `source ~/.zshrc` or `source ~/.bashrc` to update your current terminal.

You can check this worked using `echo $GOPATH`.

# Where to put your projects

Using GOPATH as the root directory, you can now put your source code in:
`$GOPATH/src/<project name here>`.

# Now save your dependencies
- Navigate to `$GOPATH/src/<your project>` (where your `*.go` files are)
- Run `godep save`

Now, when you check what's in the directory below, you should see the following `Godeps` structure.

```
➜  tree
.
├── Godeps
│   ├── Godeps.json
│   └── Readme
...
```

Don't edit the generated files yourself, it's normally a bad idea.
