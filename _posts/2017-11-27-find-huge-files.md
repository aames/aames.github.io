---
layout: post
title:  "Huge files are eating my disk, where are they?"
date:   2017-11-27 21:00:00 +1300
categories: du disk software file size
---

# Problem

Recently I have had some concerns about the amount of disk being used by my macbook pro; at times it'll range from 40Gb total disk used to 100Gb total disk used.

I'm not keen on investing in a proprietary tool to do something fairly straightforward, so I decided to use a built-in function: `du`.

# Finding all large files for a given directory

This solution uses `du`, a disk usage utility packaged with macos.

Example for finding all files greater than 1G: `du -h ~/ | grep 'G       '`

If the above command doesn't limit your results to only files greater than 1G and instead gives all results with G in the file path, simply change the amount of space after G (it could be variable depending on your OS).

# Find all files in a tree structure greater than a certain size

You can also use `tree` (on macos just `brew install tree`), with a `-h` flag to show file sizes in a tree structure.

Example for finding all files greater than 1G: `tree -h | grep G]`

# More

Need to find smaller files? Use B, K or M instead of G.

Tip: `-h` also works for `ls`. For example, try: `ls -Shl` (`-S` provides order of largest at top).

These methods will work for linux too, but you'll need to use your own package manager to get tree.
