---
layout: post
title:  "Ruby with rbenv on Ubuntu 15.10"
date:   2016-03-13 21:00:00 +1300
categories: ruby rbenv development software environment ubuntu linux
---

Hey, so you want to install Ruby with rbenv, lets jump in.

To follow this guide you need:

- Ubuntu  (I’m using 15.10)
- a user account with sudo privileges

First lets update the apt packages:

`~$ sudo apt-get update`

next lets install git  because we’ll be using git repositories for ruby build and rbenv

`~$ sudo apt-get install git gitk git-gui`

we’ll also need some build tools to compile the ruby versions

`~$ sudo apt-get install gcc build-essential libpq-dev libssl-dev libreadline-dev libsqlite3-dev zlib1g-dev`

now, we’ll start in the home directory of the current user

`~$ cd`

the next step is getting rbenv from github

`~$ git clone git://github.com/sstephenson/rbenv.git .rbenv`

And then we’ll add rbenv bin directory to the PATH so that we can use rbenv as a command

`~$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc`

We probably want this to take effect in our current session, so lets use the source command to reload the bash environment variables

`~$ source ~/.bashrc`

Now check it worked:

`~$ rbenv`

Note: If this step doesn’t work, you’ve missed something. Assuming you get some help output from rbenv, proceed…

Ok, we’ll also want some autocompletion for our rbenv… lets enable this:

`~$ echo 'eval "$(rbenv init -)"' >> ~/.bashrc`

Now lets get ruby build from github

`~$ git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build`

and we’ll add the ruby build bin directory to the path

`~$ echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc`

and reload the bashrc

`~$ source ~/.bashrc`

Now we can install a ruby version.

`~$ rbenv install -v 2.2.3`

**Note:**
This step takes a **few minutes** (maybe long enough to make coffee, maybe long enough to drink it too) depending on your computer.

It’s compiling the Ruby version from scratch so it is somewhat processor intensive. Hold tight!

...Finally, the last step before we can type ruby in the terminal is setting the version

`~$ rbenv global 2.2.3`

Great. Now try it:

`~$ ruby -v`

Optional final step; save yourself disk space and time by telling your gems not to generate documentation.


`~$ echo "gem: --no-document" > ~/.gemrc`

Sweet – you’re all set with Ruby installed and rbenv setup. Enjoy!
