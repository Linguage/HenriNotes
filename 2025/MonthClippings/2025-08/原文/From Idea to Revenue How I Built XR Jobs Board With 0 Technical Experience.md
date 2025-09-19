---
title: "🐴 From Idea to Revenue: How I Built XR Jobs Board With 0 Technical Experience"
source: "https://designwithai.substack.com/p/from-idea-to-revenue-how-i-built?utm_source=post-email-title&publication_id=2297988&post_id=169737381&utm_campaign=email-post-title&isFreemail=true&r=53wl0h&triedRedirect=true&utm_medium=email"
author:
  - "[[Xinran Ma]]"
published: 2025-08-01
created: 2025-08-26
description: "Discover how Krystian Zun built a end-to-end digital product using AI and made money. Learn how he leveraged AI for research, scraping, automation, and more."
tags:
  - "clippings"
---
### A guest post by Krystian Zun

*Today’s newsletter features a guest post by Krystian.*

*He is a product designer and maker in love with building and shipping products that provide value. He’s spent the last 7+ years building 0–1 products for startups in web, mobile, and XR.*

*Outside of work, Krystian spends his time launching side projects, testing ideas in public, and running small experiments — from building XR Jobs Board and AI workflows to growing online and in-person communities from scratch. All of it is driven by his belief that trying lots of small things is the best way to uncover big ideas.*

*You can find him on [LinkedIn](https://www.linkedin.com/in/krystianzun/?originalSubdomain=uk) and [X](https://x.com/krystianzun?lang=en).*

*Hope his sharing today sparks some ideas for you.*

---

I’ve always been passionate about entrepreneurship and building things — that’s what led me into design in the first place.

But over time, “just designing” wasn’t enough. I wanted to ship actual products. From start to finish. On my own.

There was just one problem: I couldn’t code.

I’d tried learning to code many times, but I’d always stall out, get stuck, or never stick with it long enough.

I completed a few HTML/CSS courses, dabbled in JavaScript just enough to understand how things work, but I couldn't sit down and build a full product end-to-end.

Then I came across AI tools and everything changed.

For the first time, building solo actually felt possible for me.

This is how I used AI to take XR Jobs Board from an idea to a functioning product… and eventually, to revenue. Without any technical background.

XR Jobs Board is a website that essentially curates all sorts of jobs from extended reality industry in one place.

![](https://substackcdn.com/image/fetch/$s_!Hmhb!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fbab59672-40cb-4115-a712-9085445aeece_2160x1200.png)

---

## My philosophy: solving real problems, not building the next unicorn

Before diving into the details, let me share my approach.

I’m not trying to build the next Facebook or something wildly complex that’s never existed before.

My goal is simple: solve real, everyday problems with products that can become sustainable and profitable — things I can build and ship myself.

AI helps me bridge that gap. It lets me combine my design and product experience with the ability to actually get things live.

I'm not a developer, and I probably don't even use AI most efficiently. But I've learned how to steer AI tools, structure problems effectively, and get to results that work.

---

## How I work with AI

So how do I actually work with AI to build? Here's my high-level approach:

![](https://substackcdn.com/image/fetch/$s_!LwTP!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F90a85c3e-073a-4897-be17-51331dd8b783_2160x1103.png)

### 1\. Research like crazy

Before I build anything, I research obsessively: What stack should I use? Which approach makes sense? Why this solution over that one?

One of the best pieces of advice I ever got was from Stack Overflow's guide: "How do I ask a good question?" It changed everything for me. Good research and good questions are half the battle, maybe even more. AI isn't magic; it reflects what you feed it.

### 2\. Never rely on just one tool

I don't stick to just one model or provider. I ask the same question across ChatGPT, Claude, and Perplexity. Each gives me different angles, catches different gaps, and helps me sense-check my approach. It's like asking multiple people for advice. You rarely listen to just one person.

![](https://substackcdn.com/image/fetch/$s_!eW6G!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Feb0cf8a8-8057-4679-b76f-3801efb6b1e3_2160x1103.png)

### 3\. Work block-by-block

I don’t think I’m very good at prompting and rarely looked for in-depth resources on that. But somehow despite that I manage to do everything I want.

My main strategy is creating a very specific, step-by-step plan based on my research. Then I focus on executing each block rather than trying to do everything in one massive prompt. This approach keeps me from getting overwhelmed and makes debugging much easier.

---

## Validating the idea: from problem to 400 signups in 48 hours

The idea for XR Jobs Board came from simply observing my environment and listening to friends, then recognizing a clear need.

Before I got into playing around with AI, I’d been exploring XR stuff for a while — in-person meetups, digital guides, social media content. In all those convos, the same question kept popping up:

**“Where do I find XR jobs?”**

There were many job boards for all sorts of niche jobs and industries but nothing for XR. As I was looking for an excuse to use more AI for coding, I thought this is a perfect opportunity.

The reason is that a job board isn’t rocket science, it has pretty well defined solution and problem space but it also has just enough technical moving parts to learn from: scraping, databases, automation, a bit of design, and (most importantly) a clear, real audience.

It felt to me like the perfect sandbox project to learn, test, and maybe even monetize.

![](https://substackcdn.com/image/fetch/$s_!m7Mb!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F18492b47-58fd-4725-ac7d-282185c415fc_2880x1470.png)

### Starting with the MVP: email first

Before building the full platform, I focused on validation and creating an MVP. I asked myself: what's the core value of XR Jobs Board? I settled on the ability to deliver jobs directly to people, essentially, a newsletter.

So, I decided to start with a simple waitlist landing page explaining the idea and allowing people to sign up:

- **Clear value prop**: "Stop wasting time searching job portals. Get XR roles straight to your inbox."
- **Email as the core feature:** easier to build than a full platform, more valuable than page views, and I could start delivering value immediately by sending jobs via email before building anything else
- **Simple but fun, engaging design** including a rotating Spline logo and a demo video with static mockup designs

I shared it across social media, and the response was incredible.

48 hours later, I had over 400 signups, 120 survey responses, 1.5k page views and a lot of positive responses from community.

This validation was extremely motivating and helped build momentum and excitement around the project.

More importantly, it proved there was real demand before I invested time in building.

---

## Building the platform: starting simple, staying focused

Job boards are deceptively simple on the surface, can be easily overcomplicated with "nice to have" features instead of focusing on "must haves."

I knew that as someone new to coding, I needed to be *realistic* about what I could handle. So I stayed disciplined.

Instead of building based on assumptions, I decided to gather real data on what mattered most to my target audiences: job seekers and hiring managers.

### Research first, build second

I created a short survey using Tally and shared it everywhere I could — social media posts, newsletter emails, community forums. I also conducted 10-12 moderated interviews with job seekers and potential business clients.

The result? 200+ survey responses and several hours of recorded conversations.

Here's where AI became invaluable: analyzing all that feedback would have taken me hours and hours. Instead, I fed everything into AI to help spot patterns I'd miss on my own.

**The results were surprising.** What people actually cared about was completely different from my initial idea. I scrapped my initial approach and pivoted to focus on what users actually wanted.

### Choosing the right tech stack

After further research, I settled on Next.js for three key reasons:

1. **Massive documentation** and tons of beginner-friendly tutorials, including actual job board examples
2. **AI coding tools** seemed exceptionally well-trained on Next.js patterns
3. **Vercel made deploying simple** — I didn't want to waste time setting up hosting when I wasn't even sure how long this project would survive

My goal was simple: ship something fast, then improve in small loops.

![](https://substackcdn.com/image/fetch/$s_!1GSe!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc2728c86-eda7-4a3a-b64d-2b72005fc39e_2880x1194.png)

**Version 1: intentionally bare-bones**

The first version of XR Jobs Board was deliberately minimal:

- **Core functionality**: Read database → display jobs
- **Simple interface**: Just a list pulling data from Supabase, showing job info with links to actual postings

To many, this might sound trivial. But for me, databases and backends were completely foreign. Keeping the scope tiny was perfect — it forced me to actually learn how things work without drowning in complexity.

I’d prompt AI for exactly what I needed, block by block, debug with it, and tweak until it worked.

After a few days, I had the basic version live.

![](https://substackcdn.com/image/fetch/$s_!6eMZ!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4562ca16-1855-48de-aae5-86c4bd72f9da_2880x1452.png)

**Next step?** A simple dynamic job details page so each job had its own unique URL. That meant learning routing in Next.js — another tiny, manageable skill.

And that became my approach throughout: **one small feature at a time.**

- Keep it clear
- Keep it simple
- Ship it, learn, repeat

Staying small made it much easier to use AI effectively, too. Instead of overwhelming it with huge, vague requests, I gave it focused tasks and learned just enough to connect the dots myself.

---

## Automation

The platform was live and functional. It could display jobs, link them out, and capture emails.

But there was still one big problem: **the content.**

For the first few weeks, I was manually adding every single job to the database. It worked, but it was incredibly time-consuming and repetitive.

My next goal became clear: figure out how to automate this process.

![](https://substackcdn.com/image/fetch/$s_!tndo!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2ca6cbf5-e561-4f2c-8692-def5d3259c7b_2160x1103.png)

### Building my first automation script

I started by documenting my own workflow:

1. Search for jobs across different sites
2. Capture information from each listing
3. Add that info to the database
4. Make it live on the site

Simple in theory, tedious in practice. I needed to identify which parts I could automate immediately without creating an overly complex pipeline.

I decided to focus on **bulk job uploads** first. That's what was eating most of my time.

I chose to use a Node.js script because I'd done something similar while following a YouTube tutorial to populate databases with dummy data. At the time, I thought it was the most amazing thing in the world.

The thing is that, I had no clue how to write Node.js from scratch.

I decided to do this completely with AI.

I'd describe what I wanted, AI would generate the code, and I'd troubleshoot errors until it worked the way I wanted.

But then I got ambitious. I thought: *If I can upload jobs, why not “download” them too?*

I made a few quick attempts at large-scale web scraping but quickly realized it's **really, really hard** to do properly.

So I asked myself: *What's the smallest version of this that could still help me?*

I wrote a script that could scrape specific job URLs I provided — not entire sites.

![](https://substackcdn.com/image/fetch/$s_!Nskn!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F14170bba-97e7-437c-a128-6da702fa3cb1_2160x1089.png)

### AI Magic

Here's where it got interesting. Many job listings don't structure data cleanly. The location might be buried in a paragraph rather than in a tidy "Location" field.

So I connected AI directly to my scraping script:

1. **The script visits the page** and extracts raw content
2. **AI analyzes and interprets** the unstructured data (Same as I would do, as a human)
3. **AI maps it to my database schema** correctly

Even if "New York" only appeared deep in a job description, the AI would still populate the "Location" field accurately.

This took considerable tweaking — lots of trial and error to get clean, consistent output. But I built that entire pipeline using Windsurf and the Claude API.

**For someone who couldn't write code from scratch, seeing that automated loop run — from scraping messy web pages to clean, structured database rows, was absolutely wild.**

![](https://substackcdn.com/image/fetch/$s_!ednQ!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F74bdd6fd-9704-4d1a-980c-bcbb51d91be2_2160x1089.png)

---

## Why building the platform was the easiest part

Here's something that surprised me: **building the platform with AI was actually the easiest part of creating a successful product.**

Many people get lost in the rabbit hole of building, thinking that shipping the next feature will solve all of their problems. But that's actually backwards.

The real work of making XR Jobs Board semi-successful was all the unsexy stuff that happens after you ship:

**Optimising the platform for SEO.** Writing pages and job descriptions that Google picks up. Understanding how people actually search for XR jobs — and making sure they find me first. Tuning headlines, meta descriptions

**Figuring distribution.** Initially, I heavily relied on my personal brand — posting updates and marketing content across social media. But that only gets you so far. So I test a lot of different channels, reach out to other XR projects and communities.

**Working out monetization.** Having visitors is one thing. Getting them to pull out a credit card is entirely different. I had experimented with multiple approaches: Should I charge companies to post jobs? Should I charge job seekers for premium access? Should I run a paid newsletter? etc. Most of my actual sales came from me personally reaching out to hiring managers and founders, even when they'd already visited the website and shown interest. The platform got them interested, but human connection closed the deals.

![](https://substackcdn.com/image/fetch/$s_!keEw!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F3e63eec1-0b88-4ec9-9c9b-d5a9865e34de_2160x1089.png)

### The designer’s paradox

This experience was also fascinating from a designer's perspective. I always thought that "good design" could solve “all the problems”.

But when I actually built a product myself, I realized that success depends on much more than just design, and I often had to prioritize many other elements to make the whole thing work.

It's difficult to truly understand this until you try building something yourself, and suddenly you're spending 80% of your time on things that have nothing to do with design or development.

---

## Building in public

I'd spent *years* dreading social media — overthinking my personal brand, trying to write the perfect bio, worrying about what to post.

But with this project, I decided to do something completely the opposite.

No more polishing every post or strategizing every word. Instead, I'd just *share everything*:

- The rough initial idea
- The first scrappy landing page
- Early waitlist signups rolling in
- Sneak peeks of Figma mockups
- Little wins, mistakes, lessons learned, behind-the-scenes snapshots

**And it worked.**

People gave feedback. They cheered me on. They shared it with friends.

That's how I got my first 400 signups *before* the platform even existed — just by showing up consistently for a few weeks and letting people follow along for the ride.

![](https://substackcdn.com/image/fetch/$s_!bRua!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2a5ab42d-f3b4-4afb-ae62-b10b5d563a42_2880x1470.png)

### What actually worked

- **Being brutally honest.** I didn't pretend XR Jobs Board was a polished product. I just said: *Hey, I'm figuring this out as I go, on top of my full-time job and other life commitments.* Turns out, a lot of people relate, they could see themselves in the process and they appreciate the effort I was putting in.
- **Showing rough drafts.** Instead of waiting until something was "perfect," I'd share work-in-progress. Some of my most popular posts were the quick ones I almost didn't publish.
- **Stopping trying to "build an audience."** This sounds counterintuitive, but hear me out. When you go to a party, you don't stand in the middle bragging about your CV. You mingle, talk to people, make friends, etc. I realised that social media works the same way — it's about making friends and getting to know people. Post stuff that actually sounds like *you*, and people will connect with it naturally.

### What didn’t work

- **Going quiet during the messy parts.** When I got stuck, I'd sometimes disappear, and I could feel the momentum drop immediately. Every time coming back was a struggle.
- **Only posting "Look at me!" updates.** The posts that performed best weren't announcements. They were moments where I asked for help, showed the messy bits, or invited people into the process.

I had no idea what I was doing half the time. But there were people out there willing to share their knowledge and give me their time, simply because I was open about the journey and vulnerabilities.

By the time I launched, I wasn't starting from zero. There was already a small community who genuinely cared. Some even offered to help source jobs or spread the word, just because they'd watched the story unfold and wanted to see it succeed.

XR Jobs Board connected me with people I'd never have met otherwise — other builders, potential collaborators, even job opportunities for myself.

All because I decided to put myself out there and see what happens.

---

## Your moment is now

I’ve talked about a lot of stuff here, and I think all of it matters on different levels. But if you only remember one thing, let it be this:

**We live in an incredible time.** You don't have to be a developer to build and launch a product anymore. But you do have to know enough to steer AI and have grit, perseverance and curiosity to push through when it gets things wrong.

The technical barriers that once kept non-developers like me on the sidelines disappear. But success still requires the same fundamentals it always has: understanding your users, solving real problems, and showing up consistently.

**So this is your moment.** Be curious. Learn just enough technical basics to understand what's possible. Ask good questions. Guide the machine. Get your thing out there.

And when you do — **don't hide it**. Even if it's tiny. Even if it's messy. Share the work. Share the lessons. Share the journey. Build loudly, not quietly. The community you build along the way might just be the most valuable thing you create.

You never know who's watching, or what it might lead to.

---

*Thanks a lot for sharing, Krystian.*

*What inspired me most about Krystian was his immense curiosity to figure things out. I know how frustrating debugging can be without technical experience, but he didn’t let that stop him. He’s also a great example of building in public—learning, asking, and documenting as he goes.*

*See you next time,*

*Xinran*

\-

*P.S. Today is a special day for me. The end of an era.*

*I step into the unknown to chase the dream that calls me.*