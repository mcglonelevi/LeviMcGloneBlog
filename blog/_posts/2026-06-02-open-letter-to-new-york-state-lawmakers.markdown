---
layout: post
title: "Open Letter to New York State Lawmakers"
date: 2026-06-02
categories: other
description: "New York's 3D printer blocking technology mandate is a well-intentioned law with serious unintended consequences. Here's why I'm asking you to reconsider it."
image: /assets/images/2026-06-02.png
---

To the Members of the New York State Legislature,

I am writing to urge you to reconsider the recently passed law requiring "blocking technology" in all 3D printers and CNC machines sold in the state of New York. I appreciate the attempt to reduce gun violence; however, this law is built on technical misunderstandings.  It will burden or criminalize ordinary New Yorkers while doing essentially nothing to stop the people it targets.

I am a software engineer and a hobbyist maker. I have built open-source tools, repurposed old hardware for creative projects, and followed the maker community closely for years. Please hear me out on three specific problems with this law.

## CNC Machines Are Everywhere, and You Probably Don't Realize It

The law covers not just 3D printers but CNC machines — any device that operates from a digital file to perform subtractive manufacturing. This sounds like a niche category until you think about where CNC machines actually live in the world.

The next time you walk into a Home Depot or Lowe's and use the key-copying kiosk near the front of the store, you are using a CNC machine. That kiosk takes a digital scan of your key and precisely cuts a new one from a metal blank. Under a broad reading of this law, that kiosk could be required to run every key design through a firearms-detection algorithm before producing a copy of your house key.

This is not a hypothetical edge case I'm inventing to be clever. It is a direct consequence of the law's language, and it illustrates how broadly and unpredictably this legislation reaches into everyday commercial life. PCB routers, vinyl cutters, laser engravers, embroidery machines — the category of "device that operates from a digital file to cut or shape material" is enormous. The legislature appears to have written a law targeting a very specific concern while inadvertently sweeping in tens of thousands of legitimate devices and businesses that have nothing to do with firearms.

## I Repurposed My 3D Printer Into a Drawing Machine — Am I a Criminal?

I own an Ender 3 3D printer. A few years ago, I modified it to hold a pen instead of an extruder and used it as a drawing machine — a device called a pen plotter that moves a pen across paper to produce precise, repeatable artwork. I published the design as open-source hardware so that other hobbyists could do the same thing: [PenPlotterToolheadEnder3](https://github.com/mcglonelevi/PenPlotterToolheadEnder3). I was proud enough of it to [enter it into a contest on Instructables](https://www.instructables.com/Ender-3-Pen-Plotter-Toolhead/).

This is a completely benign repurposing of consumer hardware for artistic expression. But under this law, the firmware my printer runs — open-source software maintained by volunteers in the Marlin and Klipper communities — would need to incorporate firearms-detection blocking technology. The people who maintain those projects are unpaid contributors who write code in their spare time. They are not equipped to implement, maintain, and legally certify a government-mandated content filter. If they cannot comply, the firmware becomes illegal to distribute in New York. If my old printer lacks compliant firmware, I may be unable to legally use it for drawing pictures.

To make matters worse, I suspect my design would be flagged by the very algorithm this law relies on. The toolhead uses a spring-loaded mechanism to keep the pen in contact with the paper — a component that, in isolation, bears a functional and visual resemblance to a bolt in a firearm. A detection algorithm trained to catch gun components would have no way to distinguish between the two. My design for drawing pictures could trigger a block. This is exactly the kind of false positive that the law provides no remedy for, and it illustrates why automated detection of mechanical shapes is such an unreliable foundation for public policy.

There is also a First Amendment dimension here that I do not think the legislature has fully considered. A pen plotter is an instrument of artistic expression. So is a 3D printer — artists use them to produce sculptures, jewelry, architectural models, and custom props. The objects these machines produce are creative works. A law that — by design or by false positive — prevents someone from operating these devices is a law that prevents them from creating art. Courts have consistently held that the government cannot impose prior restraints on protected expression without an extraordinarily compelling justification. A broadly written blocking mandate that silences an artist's tools without any mechanism for appeal or remedy does not meet that standard.

I should not have to worry that converting an old printer into an art tool will incriminate myself. That outcome would be absurd, and yet it follows directly from the text of this legislation.

## This Law Will Not Stop Determined Bad Actors

I want to be direct about the hardest part of this conversation: the law's core premise is shaky.

Truly dangerous improvised firearms are not primarily a 3D-printing problem. Metal is stronger, more heat-resistant, and more reliable than plastic. Anyone seriously attempting to build a functional firearm is going to use metal components. Consumer FDM printers — the kind sold at Best Buy for a few hundred dollars — cannot print metal. A fully plastic firearm cannot withstand the pressures generated by the ammunition that a mass shooter would pick — it is more likely to fail catastrophically than to function as intended.

Meanwhile, the knowledge needed to build far more capable improvised weapons from widely available hardware-store materials [is freely accessible](https://www.youtube.com/watch?v=4QJrYMIK-R4). You can find detailed video tutorials on major video platforms showing exactly how to convert standard plumbing pipe into a functional shotgun using tools available at any hardware store. No 3D printer required. No digital file needed. The result is more mechanically reliable and more dangerous than anything printed on a consumer 3D printer.

This is not an argument for doing nothing. It is an argument that blocking technology on 3D printers is the wrong tool for this problem. Bad actors will route around it trivially. Law-abiding hobbyists, small businesses, artists, and educators will bear the compliance burden. The net result is that you will have imposed significant costs on the wrong people while achieving none of your stated goals.

## The Law Is Trivially Circumventable by Anyone It Targets

Even setting aside the scope and effectiveness problems, the blocking technology itself is not hard to defeat. Here is how I expect technically motivated people will bypass it.

The blocking mechanism works by checking print files against a state-maintained database before allowing a print to proceed. That means the printer — or the software driving it — has to make a network call to verify the file. Any device that makes a network call can have that call intercepted.

A determined person would set up a man-in-the-middle proxy on their own home network. They would redirect the printer's verification requests to a local server they control instead of the state database. That local server would return an "approved" response for every request, unconditionally. The printer would proceed with the print, none the wiser.

This is not an exotic technique. It is a standard method used by network administrators, security researchers, and software developers every day for entirely legitimate purposes — intercepting your own traffic to debug an app, blocking ads at the DNS level, or testing how software behaves when a server is unavailable. The tools to do it are free, well-documented, and widely used. A first-year computer science student could implement this in a few minutes.

What this means in practice is that the people most likely to be stopped by this law are the people least likely to be a threat: hobbyists and small businesses who just want to use their equipment without jumping through compliance hoops. The people the law is designed to stop will spend an afternoon configuring their router and never think about it again.

Security through network verification only works when you cannot control your own network. At home, you always can.

Enforcement compounds this problem. A person who bypasses the system can undo every trace of it in minutes — delete the local proxy, flush the DNS cache, restore their router to factory settings — and present a fully compliant setup to any inspector. There is no artifact left behind. Law enforcement would need to catch someone at the exact moment they initiate a print with the bypass active, which is effectively impossible to do at scale. This is not a law that deters bad actors; it is a law that deters people who are not willing to spend an afternoon learning how networks work.

## What I Am Asking

I am asking the legislature to take three steps:

1. **Repeal this law so that innocent people are not criminalized.** Hobbyists, artists, small business owners, and open-source contributors should not be collateral damage in a well-intentioned but technically broken piece of legislation.

2. **Consult broadly before drafting anything new.** The right solution may not be technical at all. It may be stricter enforcement of laws already on the books, harsher penalties for existing violations, or something else entirely. Makers, engineers, security researchers, law enforcement, and legal experts all have relevant perspectives. Bring them in before anything new is written.

3. **Pass any new law with bipartisan support as a standalone bill.** Legislation that affects this many people and this much commerce deserves deliberate, transparent debate — not a quiet attachment to another measure. Get the votes honestly, in the open, and on the merits.

I believe you passed this law because you want to protect people. Good intentions do not make bad policy effective. I urge you to revisit this legislation with the seriousness the subject deserves.

Respectfully,

Levi McGlone
Software Engineer and Maker
