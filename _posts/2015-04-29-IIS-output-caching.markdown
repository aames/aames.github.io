---
layout: post
title:  "IIS Output caching to reduce CPU utilisation on static web sites"
date:   2015-04-29 21:00:00 +1300
categories: iis performance software work asp .net cache perfmon testing
---
Recently I’ve been working with a client whose website is built using dynamic image resizing and page generation. The site serves around 1,000,000 hits a day and copes well under load, given the amount of processing that is actually required to deliver pages to a single user. The downside though, for all of its dynamic processing the site actually serves up static content most of the time.


At peak times the client has had a few issues with process queueing, which is unsurprising given that there are sometimes tens or hundreds of requests for fairly average browsing activities (i.e. page navigation and simple forms) and only basic searching.

The output cache size was sticking relatively low, reaching around 80Mb at it’s peak, with 1-2Gb of available memory on the system at any time. To reduce the overall load and to prevent queueing, it was decided to offset the CPU by filling up some more output cache (this is a ‘cheap’ upgrade option as opposed to investing time and effort in redeploying on stronger infrastructure). As it’s unlikely that this client is going to receive increased users, this is a suitable use of their current resources.

Want to try this yourself? First, be sure to measure your current load using the basic perfmon counters listed below:

Processor:
- Processor time in use
- Processor queue length

Memory:
- available mbytes
- used mbytes

Physical disks:
- % idle time

**IIS specific counters:**

HTTP Service request queues (All instances):
- current queue size
- rejected requests

Web Service Cache
- Current File Cache Memory Usage
- Current Files Cached
- File Cache Hits %

Process (For all W3WP.exe processes):
- % Processor Time
- Virtual Bytes
- Private bytes

APP_POOL_WAS (For all listed Application Pools):
- Current Application Pool State
- Current Application Pool Uptime

You'll want to pay particular attention to the following counters:

- Processor Queue Length
- Current File Cache Memory Usage
- Current Files Cached
- File Cache Hits %

The intention is to increase the **cache hits %**, **files cached** and the **memory** usage, without overloading the overall memory usage (tip: keep an eye on the available MBytes counter at load).
It is expected that if your site is mostly static, then there will be a reduction in processor time and queueing.

We balance the following values to increase cached responses.

Two properties determine *cache worthiness*:
- frequentHitTimePeriod
- frequentHitThreshold

Find out more about [IIS7 output caching](https://docs.microsoft.com/en-us/iis/manage/managing-performance-settings/configure-iis-7-output-caching) and find out how to get started with [Perfmon](: https://technet.microsoft.com/en-us/library/dd744567(v=ws.10).aspx).

Method:

1. I suggest you run perfmon before for a period of time (either generate load or monitor at peak time if load generating isn’t practical)
1. Complete the change(s) to output caching as described
1. Run perfmon again over the same load profile (i.e. load generate/peak traffic) to gain comparable results
1. Calculate the difference by looking at the CPU queueing, CPU average loads and the file cache hits
1. Iterate and tweak settings if necessary
