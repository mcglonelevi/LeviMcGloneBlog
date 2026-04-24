---
layout: post
title: "The Tech Buffet Problem"
date: 2026-04-16
categories: product-dev
description: "Why building more features usually means delivering less value."
image: /assets/images/2026-04-16.png
---
Have you noticed that many tech companies treat their product like a buffet? The core product was really good and built the company. Then, the business decided to expand quickly by adding new features or building new products. When businesses grow too quickly, the results are often mediocre -- kinda like a buffet with one good dish and a bunch of bad ones. I've seen a few examples of this over my career.

## Example Tech Buffet

In my opinion, DataDog is an example of a technology buffet. Need error monitoring, logging, user monitoring? DataDog's got it. Do you need reporting, charts, and alerts? DataDog's got it. Do you need a solution for ordering a pizza over SSH? DataDog doesn't do that yet but it probably will soon!

All jokes aside, DataDog advertises 50+ features on their website. DataDog built their business around great features like logging, monitoring, reporting, and alerting. These features work well. Over the last 3 years or so, DataDog has bolted on many other features like security analysis, feature flagging, and CI tools. While the core offering is good, the recent additions often seem incomplete when compared to the products they compete with.

I have found that DataDog's overall package is great for understanding system health at a high level but I find it hard to drill down into specifics. When I need to fix a specific issue or error, I find Fullstory and Sentry to be much more useful than DataDog's RUM or error monitoring features. Another issue is that DataDog does so much it can be difficult to find what I need.

I have spoken to DataDog sales reps, and they use a tactic where they try to get you in the door and then cross-sell a bunch of features. Sometimes the new features are a little pricey for what they offer. Datadog seems to have a model of monetizing new features quickly to fund future development, but many engineering leaders are often hesitant to spend the money at DataDog when their competitors often have a better value proposition.

I have also found DataDog's web app loads slowly. I have a beefy MacBook Pro and a large network connection, so I doubt the issue is my hardware. I think the time and attention going to 50 different features means that less time is spent improving the speed and responsiveness of the application. To be fair, DataDog's service does _a lot_, but I wish DataDog gave me more value and speed in the features I use rather than bloating the entire experience.

DataDog's rapid expansion of features has come with real tradeoffs -- immature newer products, a cluttered UI, and an app that has gotten noticeably slower.

## I Built a Tech Buffet

I can only imagine what is going on behind the scenes at DataDog. I read some GlassDoor reviews that talked about a high-pressure environment, and I reflected on my career. At a prior employer, I worked on a team that built several different applications. My team built a few consumer-focused mobile apps, a B2B mobile application, and an API for partners. This team built a tech buffet -- a suite of mostly-mediocre apps.

The team would spend months working on a project only to be redirected a few months later. The constant redirection was a frustrating experience. We would get really excited about a new application and then the direction would change or the partnership would fall through. The apps we built were not profitable, and my entire team's output was basically thrown in the trash for a year. Between salaries and operational costs, the financial cost to the business was probably around $1 million.

The team had 4 engineers, a product manager, a designer, and an engineering manager. The engineers on the team were often simultaneously working on 3 different applications, and our scope was massive for the number of people on the team. We were under-resourced and always struggling to stay afloat. From my perspective, the apps we built were half-baked and lacking major functionality because we didn't have the necessary time to build.

The team was getting pressure about how quickly we needed to turn around PoC's and new features. There was often a concern about being quick-to-market. The company was also preparing for an IPO, and I think there was a hope that we would strike gold with a partner integration or a viral app. In the pursuit of a Michelin-star dish, we delivered a bunch of mediocre offerings.

## The Costs of Tech Buffets

![kylo ren more!](/assets/images/2026-04-16-kylo.jpg)

Building a tech buffet changed my perspective on tech companies and how features and products should be managed. My team was building the wrong thing instead of improving the features that added value. The dev time and money could have been invested in productive features rather than wasted in speculative ventures. In addition to financial costs, there's also an opportunity cost to building the wrong thing. We could have built something that paid dividends instead of wasting time and resources.

After I left the tech buffet team, I started a team to improve developer experience. We made substantial progress to speed up CI and builds with only 3 people. CI efficiency and fast builds save money, and the monthly AWS bill for my employer was 6 digits at the time. With a larger team and more time, I could have made so many improvements that would have sped up shipping and reduced costs across all of engineering. I had 2-year roadmap planned out in a spreadsheet.

The buffet mentality of "more = better" just doesn't hold up long-term. If quality is not present, customers won't use the product or feature. The entire experience will feel bad when some features work well and others do not. Sometimes "more" means more things to load, bigger payloads, and slower response times. Spreading teams thin in order to speed up time-to-market really doesn't pay off that often. Time-to-market for a new feature has to be weighed against time-to-maturity for existing features.

In addition to a bad UX, pushing out poorly-built features on tight timelines is exhausting to individual contributors. Product managers get frustrated because their asks are often not feasible with the allocated time, and the company blows up roadmaps when they change direction. Software devs are constantly stressed and feel like they have to cut corners to meet expectations. The drowning sensation only gets worse over time as corners are continually cut and tech debt accumulates. Performance and efficiency are thrown out the window, and designers are frustrated when UI niceties are the first item to be cut when figuring out how to make the deadline. Engineering managers get pinched between upper-management expectations and the realities of what it takes to build a good product.

When timelines are perpetually unrealistic, corners are repeatedly cut. Cutting corners leads to mediocre products. Customers know when a product is immature, and it is hard to market a half-baked application. Sometimes 80% of the investment is required for the last 20% of the work, and I have often witnessed decision-makers give up on the investment to re-allocate resources to a shiny new idea. This change in direction only continues the money-wasting cycle.

## Conclusions

Shipping mediocre features and products is like serving a bunch of mediocre food in a buffet. Before shipping a feature, take the time to get the recipe right. Does it work well? More importantly, does it integrate well with existing features? Time-to-market also has to be weighed against time-to-maturity for other work in flight. I'd rather eat at a buffet with fewer options that taste good rather than a buffet with a million bowls of slop. I'd also rather wait an extra month for a great beta feature than be the guinea pig for an alpha feature that doesn't work well.

There is often an unspoken belief that tech companies should always keep growing user count and features. While a bunch of new features and a bigger audience may sound great on an earnings call, this mindset can lead to a tech buffet. Product maturity is a feature that customers like, and it is OK to recognize when product is feature-complete.

There's a strong business case to be made for slowing down, focusing, and shipping with quality. A mature product provides funding for the next big thing. Listen to your customers about which improvements would provide the most value and carry those features to completion.
