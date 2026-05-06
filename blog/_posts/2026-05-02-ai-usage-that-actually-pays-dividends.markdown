---
layout: post
title: "AI Usage that Actually Pays Dividends"
date: 2026-05-02
categories: ai
description: "Stop using AI as a magic answer box. Use it to build code, scripts, and tooling that pays dividends — things that keep working long after the conversation ends."
image: /assets/images/2026-05-02.png
---
I have observed a concerning trend on social media where AI agents are viewed as magic boxes. Code snippets, spreadsheets, and other bits of relevant context are shared and then the LLM is tasked with performing some operation.

Have you ever asked an LLM the same question and gotten different responses?

Do you get the same response if you change the model?

Depending on a non-deterministic tool is risky. It can be difficult to verify if an LLM did the right thing, and output only degrades as context grows. Conversations are ticking timebombs, and results are not guaranteed to be correct.

LLMs are far from magic boxes and it's important to evaluate how you use these tools. Conversations are liabilities, but there are ways to use LLMs productively.

## Assets vs Liabilities

While talking to Claude or ChatGPT might feel productive, time spent conversing with an agent isn't real productivity if the result is not reproducible. Non-determinism makes LLMs inherently untrustworthy for tasks that require deterministic results. Even if you're able to create perfect context, that work will be lost in the next session and you probably can't transfer that context to a coworker's machine.

Instead of handing problems directly to an LLM, think about how you can use AI to produce static artifacts like code, tests, and tooling. Investments in these areas will improve your future productivity rather than being lost in a conversation. If you can codify the solution, you are insulated from future model changes and context degradation.

While code is often the focus of AI outputs, you can "codify" your outputs in other ways. Non-technical people may be better off using AI to produce spreadsheets rather than code. While most people aren't Excel wizards, most people understand how spreadsheets work and would be able to evaluate an agent's solution to their prompt. This allows a faster feedback loop of build -> inspect -> refine -> repeat.

## Example Assets

Recently, I worked on a project for my grandmother's funeral. My grandmother wrote a memoir that documented her travels all over the continental USA, and I needed to mark all of the locations she mentioned on a map. Handing this problem off to Claude did not work well, so I used Claude in a few different ways:

1. To reconcile differences between different OCR solutions.
2. To pull out locations from the memoir -- it did surprisingly well for this.
3. To grab the latitude and longitude for each location and put it in a JSON file.
4. To build a Python script to generate the map.

After a few hours of work, I had a nice-looking map. Because I have a script, I can modify it if I need to resize the map or render it at a different resolution. I also saved the code in a GitHub repo that I shared with my family so they can access it as well.

A few years ago, I probably wouldn't have written a script for a project like this. I probably would have printed a map of the US and drawn the labels by hand. I don't really write Python, and I am not familiar with GeoPandas and some of the other dependencies that Claude used. I was surprised by the conciseness of the output, and I was able to understand the ~150 lines of Python code.

While I did hand a few smaller problems off to Claude, I was very intentional with the scope of those problems and aggressively cleared the context. The end result though was that I had a clean data set and a nice script to regenerate the map until I was happy with the results. My takeaway from this project was that tooling has never been easier to write than it is now. If you know how to code, you can easily build great tooling to solve problems in your personal life and at work.

In my role at Moneygram, I recently used Claude to write a custom lint rule in a few minutes. I found myself repeatedly giving the same feedback in code reviews, so I decided to write a lint rule to save my time giving the same feedback over and over again.

As a part of the rule implementation, I used Claude to write a markdown file to describe the rule, why it existed, and the proper way to modify the code that violated the rule. When the lint rule fails, it provides the location of the markdown file in the error output. If an agent (or human) writes code that violates the lint rule, the fix will be obvious after reading the markdown file. The goal is to provide immediate actionable feedback before the code is ever committed -- the best kind of code review.

By writing this lint rule, I also have a tool at my disposal to find and fix problematic code. When I implemented the rule in the codebase, I applied the rule to new code while grandfathering some old violations. I used Claude to fix some of the old violations in batches by removing them from the ignore list and letting Claude work on the implementation. This tool also provides instant feedback for others writing new code. I can't review every PR, but I can write lint rules that summarize the feedback I would give. This saves me time and amplifies my impact -- code that pays dividends.

## Conclusion

The best use of AI isn't to solve problems directly — it's to build tools that last beyond a conversation. The bar for "worth automating" has dropped significantly, and AI has made it cheap enough to build that tooling that it's worth doing even for one-off projects. 

Conversations end, but tools remain relevant long after they are created. Think about the expertise you apply manually every day: the feedback you give in code review, the calculations you run by hand, the repetitive judgments you make. Those are candidates for tooling. Incremental gains will add up over time and you will reap the benefits of those dividends.

What routine task can you automate that will give you extra time with your family or a less stressful day? Start there and earn those dividends.
