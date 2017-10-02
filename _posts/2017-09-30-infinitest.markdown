---
layout: post
title:  "Infinitest: You should be using it"
date:   2017-09-30 21:00:00 +1300
categories: software engineering development testing unit infinitest ncrunch
---
# What is infinitest?
[Infinitest](https://infinitest.github.io/) is a tool that continually runs your unit tests in the background. No more waiting for CI. No more forgetting to run the unit tests before checking in. No more excuses!

# Why?
Save time!

Waiting for CI to tell you about a problem is too late; by the time you've committed the code to a branch, maybe you have a PR underway and moved on to some other task.

# Is this the answer to everything?
No.

You're never going to want your integration tests (such as Spring Boot Test) to run in the background, but having your quick, concurrent unit tests telling you if you're breaking your test code is really valuable.

# What about .NET?
See: [NCrunch](www.ncrunch.net)

Let me know what you think.
