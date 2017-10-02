---
layout: post
title:  "Developing your agile test strategy"
date:   2017-08-25 21:00:00 +1300
categories: agile software development engineering testing
---
> Agile testing doesn’t need a test strategy, does it?

# Why should you?

Let’s be clear, you probably don’t need a dogmatic 300 page document describing every facet of testing for the organisation, but it is useful to have a document for reference and to enable shared understanding.

The alternative to documenting team goals and processes (how we work) is to have an informal policy that the team shares; however, this relies upon the team collectively governing the policy and accurately sharing the information when group members change. In my experience, informal policy also makes it increasingly hard to bring new team members up to speed.

Imagine joining a team and being told:
>“We have some things we do, but they’re not written anywhere… Please remember them.”

Not an ideal start – now you have an obligation to remember and to comply with an informal policy that you can’t refer to. That doesn’t sound like a sound engineering practice, does it?

To be truly agile is to adapt and improve; storing this knowledge in a shared document means you can iterate and modify your goals to meet the needs of your team, even when there is a change in direction.

My suggestion is to include the first attempt at your agile test strategy when you’re developing team working agreements and revisit it at your first retrospective. If you start with a clear, concise outline of your intentions then you’ll have a good foundation on which you can build your organisational maturity.

If you’re already in a working team – introduce the idea at your next planning session and perhaps bring along a first draft that the team can review and contribute to.

# What might be in an agile test strategy?

There’s no strict rule here – write down whatever you need to tell a newcomer about your process. Here are some prompts that will help you to begin:

- An outline of your broad goals with respect to quality.
- A description of the terms you use to describe test types.
- Scope; how will you focus your effort?
- Approach; how will you work?
  - Before the story has been started.
  - After the story has been completed.
  - How will the story be signed off (Done)?
- Environments:
  - Do you have any specific requirements?
  - Do you share it? With whom?
- Risks (known or perceived).
- Clarification of any roles and responsibilities.
- Reporting – automated? version controlled? manual? where?

# Test process improvement

This is part of shifting right (yes, there's more than just *shifting left*); it means focusing on improving your current practice with the benefit of experience and the overarching aim is to deliver better solutions that have fewer defects and improved reliability.

I have no intention of dishing out hard rules here: It’s your journey, but I do have some thoughts that may help:

- Keep track of things that are and aren’t working for your team as you go.
- Evaluate the impact of your testing; collect useful data from monitoring software and understand the end user.
- Don’t underestimate the human impact.
- Regularly question your scope and approach, if you can’t defend it then it may not be working for you.
- Try something new and measure it so you know if it adds value.

# Making it easy: How to start?

Figure out **what you’re trying to achieve** with testing

- Is the software correct?
- Does it meet some standard?
- Is it maintainable?
- Is it bug free?
- Formal verification is a fair goal if you’re working with safety critical systems.

**How** will you meet your goals?

*What kinds of testing will you use?*

- Manual?
- Unit tests?
- TDD?
- Acceptance tests?

...this list could continue for a long time – pick suitable choices that are reasonably achievable

**Clarify any ambiguity** that could reasonably exist. Specifically, you might choose to address the following:

- Terminology
- Approach
- Scope
- Defect management
- Roles and responsibilities
- Environment requirements

# Still not sure where to begin?

Look at the foundation levels of the TMMi model – it may not align with your goals, but I strongly believe that every organisation should be capable of operating at level 2  of the model before beginning to work on optimising its process.

# Presentation matters

Brevity is an art form in itself so I try to maintain a complete version of the strategy (around 3 pages, widely spaced) and a one-page version that I can throw up in a retrospective and the team can immediately see everything in short form.
