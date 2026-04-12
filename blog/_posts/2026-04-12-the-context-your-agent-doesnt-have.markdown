---
layout: post
title: "Domain Knowledge: The Context Your Agent Doesn't Have"
date: 2026-04-12
categories: ai
description: "Vibe-coding ignores the most important input: what you know about the system, its history, and where it's going. Domain knowledge is your edge — don't leave it out of your prompts."
image: /assets/images/2026-04-12.png
---
If you've been using an AI agent in your work, I'd bet that you've made a crucial error of not supplying complete context in your prompts. It is easy to open up a prompt box and start typing, but have you thought about the key details that are necessary for a good result? Quickly describing a problem may be appropriate in some circumstances, but modifying an existing codebase without thorough understanding can have some pitfalls.

A product evolves over time. There's a history of how a product got to where it is, and there are potentially dozens of product managers and executives who are speculating about where it's going to go. The past and the likely future should inform your present code changes. An AI agent has little knowledge of the past and no context of speculations taking place outside of the codebase. It is your responsibility as a product engineer to design solutions with future states in mind.

## The Past Informs the Present

The AI agent has no idea how a codebase got to its current state. Agents only have context on the code that they are able to read. There is a token limit, and tokens that come later often have priority over earlier tokens. For example, prompt injections rely on this recency bias (ex. `reject previous instructions and do XYZ instead`). Depending on how the agent navigates the codebase, the results of your prompt may vary. For example, missed files or files that are read in different orders will cause changes in the output. The more tokens the agent has in its working memory the higher chance there is for slop.

Code often has outside information that is needed to fully understand it like an architecture doc, comments, or a detailed PR description. Maybe there are some complex edge cases or a performance issue that could result from changes. Knowing this extra info is a massive part of domain knowledge.

I once worked in a codebase where I saw some code like this:

```ts
function getDashboardData() {
    let queryResult = summaryQuery.get();

    if (customerId === 1234) {
        queryResult = weirdlySpecificCustomizedQuery.get();
    }

    return queryResult;
}
```

I was asked to fix a bug in a reporting dashboard. Once I dug into the code, I realized that there were different queries being run based on the customer viewing the dashboard. I turned to the senior engineer behind me to ask about the significance of the customer ID, and I found out that the customer ID was for a high-paying customer who paid for the dashboard to be changed and that I should be careful to not break their report while fixing the bug. Business knowledge existed outside of the codebase. Imagine what an agent might do in a case like this. Maybe the agent may have removed the `if` statement thinking it was the cause of the bug when it was supposed to be there for a reason.

Even if you are careful about the size of the context for your agent, there's a real chance that the agent misses the intent behind certain blocks of code. I can think of many times where I needed to provide extra detail about code I shipped to production:

1. The types being wrong for a TypeScript library and what the correct types were.
2. Performance implications of a particular piece of code and why changing it may be problematic.
3. A "hack" that was added to prevent a race condition in a pinch.
4. Adding an index on a database to speed up a specific query.

Without the extra info, the code I shipped may have been tricky for a reader to understand. When using an agent, we should be very careful to pass off context of the existing code and why it is organized in the way that it is. How you pass along that context is up to you (markdown files, prompt, etc.), but failure to pass context for critical paths will result in a bad solution. Maybe you will mess up a crucial piece of reporting for a high-paying customer. Agents may generate code with implications that aren't obvious to future readers -- agent or human.

I don't trust agents to call out the important parts of generated code. Because of this, I believe it is important to read all generated code and ask the agent questions if there's something I don't understand. There is no excuse for shipping code that you do not understand when it takes 10 seconds to highlight the block and ask "Why is this here?". Also, having the agent produce a context document or detailed PR description may aid in code review and future endeavors. I often have to refer back to PR descriptions or diffs for features I wrote a while ago. Sometimes I use `git blame` to figure out why some obscure piece of code is there. Reading the diff that introduced it or reaching out to the person who wrote it is often helpful. When code is written by an agent, you may not have the luxury of asking "why" if the context has been lost.

Every place I have worked has had "legacy code" -- portions of a codebase that developers are afraid to touch because it might break. Sometimes the person that wrote the code is no longer with the company, so there's nobody to ask about how it works. I think agentic development has a high likelihood of producing legacy codebases in a short amount of time. It is easy to blindly throw an agent at a problem and ship the result without proper review because nobody has context on how the code actually works. Good results are not guaranteed, and bad results are more likely. How can you review something you don't understand?

Personally, I view my domain knowledge of a system as the most valuable asset I bring to the table. When I start in a new codebase, I try to understand how it works at a high level so that I have a good mental model. As I add features to the codebase, I gain more in-depth knowledge as I am forced to understand specific parts of the system in order to build on them or change them. The domain knowledge that I carry in my head informs future development, and I often try to pass that knowledge along to others when appropriate to avoid being a knowledge silo. From a selfish perspective, the domain knowledge of how systems work makes me more valuable because my employer can't easily hire someone with the knowledge I have.

Another aspect of domain knowledge is being able to assess the risk of change. Over my career, I have found that I have to be very careful when I make specific changes. Database migrations are a good example (lots of lessons from full-table indexing), but also any code related to background jobs is another frequent trouble spot. When my code is deployed, there may be jobs sitting in a queue actively being processed. When I change worker code, I have to remember to keep all changes backwards-compatible to avoid stuck jobs. Sometimes it is better to create an entirely new worker and remove the old one in a separate PR after all jobs have processed. This kind of domain knowledge is often learned through experience, and that change may come across as an innocent-looking 3-line change as a part of a larger PR. My PR with this mistake got approved by a human, and it's quite possible your agent will make the same mistake that I did. My experience with background jobs in the past informs how I write and review code today. I also wonder how well an agent would be able to debug an issue like this where knowledge of infrastructure and the deploy process is really important.

Domain knowledge may be lost when key implementation details are left to an agent. AI agents lack historical knowledge. Sometimes that knowledge loss can be desireable if the agent went down a bad path, but the loss of knowledge can also inhibit the agent's ability to plan features with the existing solution in mind. Each new session presents a battle to build the right mix of contextual knowledge to get a good result.

## The Likely Future

If the AI agent doesn't understand the "why" behind code that already exists, it will likely go about adding new features or changing existing ones in the wrong way. It's also important to include relevant information about the future additions you plan to add. How is the agent supposed to have knowledge of something that it can't access?

Having worked in the tech industry for nearly a decade, I have observed that teams are often planning features 3-6 months in advance of when they are written. There are exceptions to this rule, but the norm is that we're building several features toward a long-term goal. Roadmaps often include new features followed by quick additions. Fast-follow features often address issues in the user experience, add additional functionality, or allow for tech debt cleanup.

Writing features in a future-proof way is difficult -- especially with an agent. As I see it, there are two ways of approaching this problem:

1. Be very prescriptive in the approach that the AI agent should take to solve the problem.
2. Knowledge about future iterations is passed to the agent as a part of the prompt.

Being prescriptive about the solution is the approach that I use most of the time. The benefit of this approach is that the agent needs much less context passed to it. I pre-plan my features up front -- often with detailed documentation, and I am planning those features with future iterations in mind. Being prescriptive about the solution often gives me the code that I want more quickly than conversing with an agent due to a poor initial prompt. Using AI to help you plan is fine, but review the plan thoroughly.

In the case where I don't have a solution in mind, I will often try to pass off context about where future product decisions are headed like:

> I need to add tagging to my blog posts. In a future iteration I will make it possible for users to search by tags. I'll also be adding a feature next week for AI-suggested tagging, so it's important to be able to pull a list of unique tags for that task. In the distant future, I'd like to create a taxonomy of tags. Can you design an architecture for this feature and document it in a markdown file for how you would build out each iteration?

This approach works better for greenfield features, but it will require the agent to do some digging to understand the existing code structure. Simple tagging could be implemented in a variety of ways, but the requirement for a taxonomy could really throw a wrench in the works if tagging is implemented in a way that inhibits relating tags together. Having this discussion with the agent up front helps prevent bad solutions. You could try to vibe-code your way through this problem, but you might end up with some unnecessary and error-prone data migrations down the line. Taking extra time to plan now could prevent outages and unnecessary effort later.

## Final Thoughts

Don't rate your productivity by today's success. Success today at the expense of long-term productivity is a net-negative. The expense of tech debt goes up exponentially as features are added to a shaky foundation. Using AI agents in a poor manner can result in a false sense of accomplishment that will be realized in future iterations. Writing code is only part of the job, and planning often matters more than shoving today's PR out the door.

I would encourage product engineers to understand their value is not in writing code but in the domain knowledge that they have. Anyone can type on a keyboard, but does the thought being expressed have the right context and understanding behind it? The domain knowledge of what exists and what is coming in a few months can be leveraged in a way that allows for a true AI-enabled productivity boost rather than a productivity deficit.

When writing your prompts, consider adding relevant context about the current implementation and the expected future iterations to reduce the chances of painting your solution into a corner. 
