---
layout: post
title: "Solving Problems with AI the Right Way"
date:  2026-03-18
categories: ai
description: "AI can write code fast, but great software still requires deep problem understanding. A case for thinking before you prompt."
image: /assets/images/2026-03-18.png
---
There's a lot of buzz about AI and how it can make our lives as software engineers better, easier, and faster. Some executives leaders are fantasizing about how non-technical employees will finally be able to code, and some of those leaders have already taken steps to reduce headcount at their company! It's really easy to buy into the hype train, but it's important to remember why we write software -- to solve problems. I wonder how many good problem-solvers have been let go in the name of efficiency and profit.

## The Version Control Problem

I have been a software engineer for the last 10 years or so. During my tenure at different companies, we would often have conversations about modelling solutions to problems. We had these conversations because _how_ you solve a problem _actually matters_. I'm going to use version control (VC) as an example.

Today, VC is taken for granted, and most people probably see it as a "solved problem". Most rational people just use git as their program of choice for VC; however, it was designed to solve the VC problem in a very specific way. The original constraint was that git would be good enough to manage contributions to the Linux kernel. By happenstance, git also works pretty well for >90% of other projects.

Once a repo gets large with a lot of commit history, git starts to break. Facebook and Google invented their own proprietary VC systems to solve their specific needs. The way they solved VC had specific design constraints and scale in mind at the beginning of the project. I've never worked at Facebook or Google, so I have no idea how they solved the problem, but they ship a lot of code every day which is a sign of success.

What would have happened if Facebook or Google did not design their VC solutions with the end goal in mind? One does not simply wake up one day and say "I am going to build my own version control system". There's probably a story like this:

> We were using git. Git started running really slowly, and we started wondering why. The problem got so bad that nobody could work. We realized that git could no longer handle the size of our codebase, so we looked into making git faster. We found it would take nearly a complete rewrite to serve our needs, so we also looked at alternative programs. Our testing showed that these alternate programs couldn't support our needs either, so now we need to build our own software.
> 
> \- Hypothetical software engineer

The folks who built these proprietary VC systems had to build domain knowledge. They probably went through these steps:

1. They had to understand why git or whatever VC system they were using was slow or not fit for their needs.
2. They had to brainstorm solutions to how they were going to build a VC system that could scale.
3. The best solutions were probably discussed at length by some really smart people.
4. One solution eventually won and was implemented.

## The Danger of Skipping Deep Thinking

Every line of code is part of a much larger story. Bigger stories require a lot more thought to be cohesive and enjoyable. If you're writing a quick bash script that you'll throw away next week, you may not need to think much about your problem domain or the prompt that you give to your AI robot to solve that problem. If you're trying to ship a complex application that needs 24/7 uptime, you should probably think through the problems that you're solving and how you're handing those off to the robots you employ. Great solutions come from a place of deep understanding of a problem. Good luck if you're trying to vibe code Facebook's VC system.

Even though AI agents are capable of writing a VC system, I'd bet my next paycheck that a good majority of software engineering teams haven't even thought of replacing git. Git is good enough to solve the VC problem for most people, and it's got some sticking power because of _how_ it solves the problem.  Git is such a great program that entire companies have been built around it, and git is still updated nearly 21 years after its inception. In my 10+ years of using git, I don't think I've ever experienced a bug.  Git is the gold standard of great software, and it was invented by someone who understood the problem they were solving very well. It's a great solution to a big problem.

When you have an unhealthy dependence on an AI agent, it is so easy to just start typing and not really think about the problem you're trying to solve. Because it is so easy to get something that (mostly) works, my fear is that most people in the tech industry will just blindly trust AI with crucial decisions that may end up destroying their company. Great solutions to problems have specific qualities that make them valuable. The software that will keep your company around will have a quality like ease of use, speed, consistency, features, or scale that nobody else has in your industry. If someone else can use AI to easily replicate what your company is doing, your company will not survive the future.

The qualities that make git so successful for >90% of repos were its primary drawbacks at Facebook and Google. Git is a distributed version control system where the whole commit history is stored in a directory as a bunch of files. While that approach is great for most codebases, it doesn't work for large repos with long commit histories. _How_ you solve a problem _actually matters_.

## Build the Next Git

I think the companies that will survive the next decade will produce the best software that solves a specific problem really well. That software will be written by people who have a fantastic understanding of the problem that they are trying to solve. In order to withstand the test of time, the software has to be so well-architected that it can't be easily replicated or it has to solve the problem so well that there is no incentive to build an alternative.

If you are in the business of building software, my challenge to you is to build the next git in whatever space you're competing. Get a deep understanding of a problem and then build the software that people want to use. Build such a good solution so that most people don't even think about switching to a competitor or building their own solution. Use AI to accelerate your implementation of that solution.

If you're an executive who is contemplating reducing headcount at your company, you should think very carefully about who you let walk out the door and what knowledge they have. Those employees know what makes your company competitive and what your company's weaknesses are. Those who you let go may join a competitor and use AI to compete with your business.
