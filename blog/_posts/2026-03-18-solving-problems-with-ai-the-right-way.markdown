---
layout: post
title: "Solving Problems with AI the Right Way"
date:  2026-03-18
categories: ai
---
There's a lot of buzz about AI and how it can make our lives as software engineers better, easier, and faster. Leadership at some companies are fantasizing about how non-technical employees will finally be able to code, and companies have already taken steps to reduce their headcount! It's really easy to buy into the hype train, but every benefit that AI brings also has a downside. Personally, I wonder how many great problem solvers were let go during these company downsizings in the name of profit and efficiency.

I have been a software engineer for the last 10 years or so. During my tenure at different companies, we would often have conversations about modelling solutions to problems. We had these conversations because _how_ you solve a problem _actually matters_. I'm going to use version control (VC) as an example.

Today, VC is taken for granted, and most people probably see it as a "solved problem". Most rational people just use git as their program of choice for VC; however, it was designed to solve the VC problem in a very specific way. The original constraint was that git would be good enough to manage contributions to the Linux kernel. By happenstance, git also works pretty well for 95% of other projects.

Once a repo gets large with a lot of commit history, git starts to break. Facebook and Google invented their own proprietary VC systems to solve their specific needs. The way they solved VC had specific design constraints and scale in mind at the beginning of the project. I've never worked at Facebook or Google, so I have no idea how they solved the problem, but they ship a lot of code every day. Their solutions seem to work well for their needs.

What would have happened if Facebook or Google did not design their VC solutions with the end goal in mind? One does not simply wake up one day and say "I am going to build my own version control system". There's probably a story like this:

> We were using git. Git started running really slowly, and we started wondering why. The problem got so bad that nobody could work. We realized that git could no longer handle the size of our codebase, so we looked into making git faster. We found it would take nearly a complete rewrite to serve our needs, so we also looked at alternative programs. Our testing showed that these alternate programs couldn't support our needs either, so now we need to build our own software.
> 
> \- Hypothetical software engineer

The folks who built these proprietary VC systems had to build domain knowledge. They probably went through these steps:

1. They had to understand why git or whatever VC system they were using was slow or not fit for their needs.
2. They had to brainstorm solutions to how they were going to build a VC system that could scale.
3. The best solutions were probably discussed at length by some really smart people.
4. One solution eventually won and was implemented.

In our programs, each line of code is part of a much larger story. Bigger stories require a lot more thought to be cohesive and enjoyable. If you're writing a quick bash script that you'll throw away next week, you may not need to think much about your problem domain or the prompt that you give to your AI robot to solve that problem. If you're trying to ship a complex application that needs 24/7 uptime, you should probably think through the problems that you're solving and how you're handing those off to the robots you employ.

Even though AI is capable of writing a VC system, I'd bet my next paycheck that a good majority of software engineering teams haven't even thought of replacing git. Git is good enough to solve the VC problem for most people, and it's got some sticking power because of _how_ it solves the problem.  Git is such a great program that entire companies have been built around it, and git is still updated nearly 21 years after its inception. In my 10+ years of using git, I don't think I've ever experienced a bug.  Git is the gold standard of great software, and it was invented by someone who understood the problem they were solving very well.

With most AI programs, it is so easy to just start typing and not really think about the problem you're trying to solve. Because it is so easy to get something that "works", my fear is that most people in the tech industry will just blindly trust AI with crucial decisions that may end up breaking their company. I have already seen horror stories of production databases that were deleted with no backups thanks to an AI agent running Terraform commands. What we haven't seen yet is truly great software that was produced with AI that withstood the test of time.

I think the companies that will survive the next decade will have the software that solves problems really well, and that software will be written by people who have a fantastic understanding of the problem that they are trying to solve. In order to withstand the test of time, the software has to be so well-architected that it can't be easily replicated by someone else with AI or that it solves the problem so well that there is no incentive to build an alternative.

If you are in the business of building software, my challenge to you is to build the next git in whatever space you're competing. Build the software that people want to use because of how it solves the problem in a quality way where most people don't even think about switching to a competitor or building their own solution. Use AI to help you brainstorm the best way to solve the problem that still aligns with the business and customer needs.

In my next blog post, I'll be talking about different ways of using AI to understand and solve problems.
