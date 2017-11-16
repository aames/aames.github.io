---
layout: post
title:  "Fixing the Apple pay wallet infinite loop"
date:   2017-11-17 11:00:00 +1300
categories: apple mac software wallet applepay
---

# Problem
You restored from your time machine backup and your apple pay needs to reset.

But it can't! As a result, you end up in an infinite loop of requests for elevated permissions.

> Apple Pay is already configured on this disk for another Mac.

# Solution
The solution (from Apple) after several levels of elevation to senior engineers is reported to be:
> reinstall osx and _don't_ use a time machine backup

Unfortunately I just don't have the time or inclination to do that, particularly when Time Machine exists to prevent that necessity!

Here's how to reset your apple pay on your Mac. I'm running High Sierra, it should work for Sierra too.


The commands below do the following:
1. Change to the private database directory.
1. Move the applepay folder into another folder (you could move it back later, that way).
1. Kill the seld (secure enclave) daemon process.
1. Kill the nfc daemon that apple pay uses.

```
cd /private/var/db
sudo mv -i applepay applepay.old
sudo pkill seld
sudo pkill nfcd
```

No restart needed, go back to System preferences -> Wallet and you should be able to set it up now.
