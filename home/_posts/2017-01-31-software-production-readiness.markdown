---
layout: post
title:  "Software production readiness"
date:   2017-01-31 21:00:00 +1300
categories: software engineering development production environment deployment testing release releng
---
**Where to start?**
I’ve been asked a few times recently about how to ensure a new software component is ready to enter production.

Typically I suggest the developer follow whichever release guidelines are available, but sometimes there are none.

Here’s a list of questions in no specific order that should prompt consideration.

- Check the unit test coverage. Is there any? Does it give you confidence?
- Has the code and unit test coverage been peer reviewed? Do you want it to be 100%? Did you check your coverage is non-trivial coverage?
- Has QA signed off the component in a production-like environment? (n.b. Docker is production-like if you’re running Docker in production)
- Have the business performed any acceptance testing (or has a demo been conducted)?
- Is there a rollback strategy in place?
- Is there a mechanism for raising alerts when the system encounters an error?
- Do you have a log store? (perhaps more importantly, does it rotate?)
- Have you documented the source code? (e.g. Javadoc or similar)
- Have you performance tested? (note: a short Jmeter load test can give false confidence, be careful here!)
- Do you need to communicate the change to any operations or support staff? Has documentation been prepared?
- Do you have a tagged copy of the source code in your source code repository?

  **Wait, what?** You might think this one above is too easy to even mention, but more than one team I’ve worked with has been stuck with a binary and no copy of the source code due to developer error – failing to push and deleting their copy.
- Have you integrated your component with your organisation’s CI or CD tool?
- Did you set the configuration correctly? (Check: Environment variables, ports, hostnames, firewall rules)
- Did you check for vulnerabilities in your software dependencies? (**Yes, do scan that docker image**, it's only as good as its layers!)
- Are there any authentication/authorisation or privacy concerns that may mean you should have your component security tested?
- I’m certain that there are points I’ve omitted that you can think of, but this should be enough to begin forming your software production readiness checklist.

If you’ve got burning questions or wish to add more to this list I’m keen to hear from you – get in touch with me on Twitter.
