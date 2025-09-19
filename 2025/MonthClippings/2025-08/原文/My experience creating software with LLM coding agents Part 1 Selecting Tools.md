---
title: "My experience creating software with LLM coding agents - Part 1 (Selecting Tools)"
source: "https://efitz-thoughts.blogspot.com/2025/08/my-experience-creating-software-with.html"
author:
published: 2025-08-22
created: 2025-08-26
description: "My experience creating software with LLM coding agents - Part 1 This post details my experiences creating software with LLM coding agents, e..."
tags:
  - "clippings"
---
## My experience creating software

## with LLM coding agents - Part 1

This post details my experiences creating software with LLM coding agents, emphasizing that what you do with AI agents is ‘creation’, not just 'coding,' and sharing what worked for me. This is not 'The One True Path To AI Success.'

  

tl;dr:

- I’m not a professional developer, just a hobbyist with aspirations
- I wanted to accomplish a coding project beyond my skill level and have been experimenting with agentic coding tools for several months (spoiler: mostly success)
- You should use Anthropic’s Claude Sonnet model for complex coding tasks.
- Experiment with various agents and models; be adaptable as the field evolves quickly. I prefer Claude Code and Roo Code at this time.
- If you are a heavy user, ~~you should use pay-as-you go pricing; TANSTAAFL~~.*I [posted this on Hacker News](https://news.ycombinator.com/item?id=44991884) and was very forcefully corrected that with Anthropic in particular, you can use the [Claude Pro or Claude Max plan and auto-switch to pay-as-you-go](https://support.anthropic.com/en/articles/11145838-using-claude-code-with-your-pro-or-max-plan) if you run out of capacity.*
- If you are a light user, use your favorite free or “comes-with-my-monthly-subscription” chatbot and whatever model it comes with. I expand on what “light” means later but think “not very much at all, bash one-liners, single-file python scripts, etc.”
- [Part 2](https://efitz-thoughts.blogspot.com/2025/08/my-experience-creating-software-with_22.html) of this post has a long list of a lot of tricks/skills I picked up to make software creation easier, more efficient, more accurate, and cheaper, when using agentic AI.

## Commence the Blogging

As a security engineer with a CS/ECE background, I've spent nearly 30 years collaborating with developers and writing personal software, recognizing good and bad design patterns.

  

I am skeptical about LLMs achieving AGI and don’t believe that humans will use AI thoughtfully, but that ship has sailed.

  

In March 2025, I decided to undertake a complex software project that was beyond my skills, by exploring AI coding. My initial 30-hour weekend with Claude Code was revelatory, transforming me from a skeptic to an evangelist.

  

Since then, including refactors and rewrites, I’ve probably used AI Agents to generate over 200k lines of code across several small and two large projects.

  

I have never been an “AI is going to eliminate all the jobs” person. Before my epiphany, I thought that LLMs were just a glorified autocorrect and a swiss army knife for language. Since I started using agents to help me create software, I’ve refined my opinions; here are my current beliefs regarding agentic AI coding:  
  

- LLMs and agents are going to become a critical part of building most software, because they will increase productivity - developer output per unit time.
- Developers will be soon start to be perceived as unproductive if they do not adopt these technologies
- Use of agents in software development can increase productivity, even dramatically, depending on how you choose to use it. By “increase productivity”, I mean, complete most of the tasks that developers do - spec writing, design, coding, and debugging - in much shorter times than those tasks would take without an agent.
- Without oversight, new developers will not be particularly good at authoring nontrivial software with AI agents, and experienced developers will do well with it if they choose to adopt it. The skills needed to be good at agentic coding are skills that come from experience - recognizing and implementing good design patterns, etc., instead of mastering subtleties of syntax.
- Companies will only gain these productivity boosts if they actually allow and pay for their developers to use them effectively. Agent & LLM access will actually become an extra cost per developer, and productivity gains will likely be proportional to spend.
  

Note that I emphatically do not believe that developer jobs are going to go away. I think some crappy companies are going to try to fire their expensive, experienced, skilled employees and replace them with outsourced or entry-level ones augmented by AI. Such companies are going to get really poor results and stop doing that. The rest of the industry will learn that is a bad pattern, by watching the failures. Just my opinion, and I’ve been wrong before, and I’m not saying it’s a good thing or that I want that; it’s just what I think is going to happen because a lot of humans suck.

## Selecting an Agent

Choosing an agent depends on your desired coding assistance, from smart autocomplete to autonomous code generation. Try them all and see what works for you. I wanted the full experience, not just suggestions and autocomplete.

  
- Smart autocomplete in the IDE
- Tooltip-type suggestions in the IDE
- Chat inside or outside the IDE, enabling:
- Ask questions about the codebase
	- Assist in planning
	- Assist in documentation
	- Assist in debugging
- Autonomously debug
- Autonomously write code
  

Then you’ll need to decide which agent, model, and payment structure to use, but you can refine your choices based on your comfort level with the above use cases.

  

I chose to go all in and have the agent write and debug code for me, and I tried a bunch of different agents and models to see what I would like. Here are my experiences and advice based on my choices.

  

Over the last five months, I've used Claude Code, various chatbots (Grok, ChatGPT, Gemini, Google AI Studio), and VS Code plugins (Roo Code, Cline, Copilot, Gemini Code Assist). I avoided custom IDE solutions like Cursor or Windsurf due to personal preference.  
  
I used them in conjunction with direct LLM provider integration (OAuth or API), with OpenRouter (which acts as a gateway to many different LLM providers), and with locally hosting LLMs via Ollama & LM Studio.

### What do I like in an agent?

I like getting good outcomes, where the code the agent generates meets my needs without much need for additional iteration, bugfixing, or refactoring.

  

I like working in my IDE of choice (Visual Studio Code).

  

Claude Code is my favorite standalone tool for its superior results, despite UI quirks and janky integration with VS Code. Roo Code is my preferred VS Code plugin for its customizable prompts and rich use of the VS Code UI, like displaying mermaid graphs or interactively navigating web applications in the UI, though it can be verbose and over-suggest refactoring.

## What don’t I like?

I have avoided the “custom-IDE-integrated-with-our-custom-AI-all-for-one-low-monthly-price” solutions like Cursor and Windsurf. Kiro’s spec-first approach looks interesting and aligns with my experience and work style.

  
- I don't want to pay a subscription for my IDE.
- I don’t want a single-purpose tool. I want a generic vendor-neutral IDE with its own ecosystem, and I want to be able to switch models if I feel like it.
- The landscape is changing so fast that it doesn’t make sense to lock in to a specific IDE that won’t iterate nearly as quickly on IDE features not core to its builder’s vision.
  

I hate the “suggestions in the editor” agents. Sometimes they’re genius but they are relentless and having to constantly reject their suggestions takes me out of flow. It’s annoying AF when one pastes half a page of text because I hit the wrong key and accidentally accepted an unwanted suggestion.

  

I’m ambivalent about the “tooltip in the editor” agents, like light bulb context menu with a “fix this issue with <agent>” menu item, because they tend to give much too generic instructions to the agent, like “fix all issues in the open file”, rather than the specific kinds of information the editor is capable of providing with modern language servers and linting and knowing what is highlighted and where your cursor is.

## Agent selection summary

In summary, I made these choices and they informed my agent preferences and recommendations:

- I want to chat with the agent to develop and fine tune plans, and then have the agent write and debug ALL the code. I am virtually unskilled in the particular languages I’ve chosen, but I am very skilled at precise specification and my specific problem domain.
- I like working in the VS Code IDE

  
Given that, I chose Claude Code and Roo Code (both!) and used them both from the VS Code IDE.  
  
Your adventure is your own, decide what you’re comfortable with and try a lot of things, but don’t sink much money into anything until you get on a path you’re happy with.

  

➤ Try lots of agent patterns to see what works for you; they are NOT all the same.

- Decide how you want the agent to help- autocomplete, small fixes, explaining & planning/documentation, or writing code autonomously.
- Figure out what you like in an agent and what you don’t like.
- Decide if you can live with one IDE or two.
- Decide if you can live with the agent chat window outside the IDE instead of in it.

## Pricing

I’ve experimented with the pay-per-month and the pay-as-you-go pricing models. A lot of people are upset now that Anthropic is capping usage with their monthly plans. From the beginning, I was suspicious of caps and rate limiting so I have always just used pay-as-you-go for API usage.

  

Spoiler alert: If you are an extremely light user, just use the free LLM that comes with your X or Google One or ChatGPT subscription. If you are a heavy user, you need to suck it up and pay-as-you-go. There is no free lunch anymore, the model providers cannot absorb the titanic costs of running massive fleets of GPU-enabled hosts and give you more value than you’re willing to pay for.

  

Then you will never be rate limited and you will never be capped, but you will need to watch your bills. All the agents I used did a reasonable job of tracking and reporting costs.

  

If you are unable or unwilling to pay as you go, then host your own locally and deal with the slow, older, open-weight models. The token generation rate on my M4 Mac literally reminds me of the 1980s BBS days; it makes me nostalgic for Xmodem and Kermit. Get ready to “Press Play On Tape” and go get lunch.

  
I saw this web site go by on Hacker News the other day and I’m excited to be able to compare model pricing this way: [https://pricepertoken.com](https://pricepertoken.com/). However since then, I’ve found that there are lots of such sites so choose your own adventure.  
  
Oh, and how much have I spent on AI? As of this writing, Anthropic says that I have spent $2,445.58 since March 29. I also spent about $40 on Google One AI Pro for a couple of months, $50 on OpenRouter, and $84 on X premium which includes Grok. I consider that a bargain given how much working code I’ve gotten out of it; in previous projects I spent far more hiring contractors from UpWork. Currently I’m paying Anthropic between $100 and $200 per week, depending on how much work I do, but I’m coding with the agent 4 hours per day most days.

## Selecting a Model (or more than one)

There’s really not much of a choice here, at least for me. For non-trivial coding, Claude Sonnet (3.5, 3.7, then 4.0) consistently delivered the best results in understanding module interactions and generating correct, readable code, often outperforming Opus for coding tasks. I only engage deep thinking occasionally as I’ll discuss later.

  

For simpler tasks like scripts or toy games, any chatbot or subscription-bundled LLM is usually adequate. All models excel at Python and shell scripts. “Trivial” is relative; I’ve used Grok to create [1000+ line Python programs](https://github.com/ericfitz/scan-namer/blob/main/scan_namer.py) and I’ve used Gemini to make very complex SQL queries (Gemini is very good at SQL). None of the chatbots particularly stood out to me as being better than the rest.

  

While open-weight models like Deepseek R1 and Qwen 2.5-Coder (now Qwen 3-Coder) show high benchmarks, self-hosting them is costly in local resources and slow, making Sonnet a better option for me. By “slow” I mean “between 1-3 orders of magnitude slower, per token generated”. I don’t think self-hosting non-quantized R1 is even possible for most people given the model size.

  

Yes I know you are going to tell me “you can get Bill and Ted’s Most Excellent quantized version from [HuggingFace.co](http://huggingface.co/) blah blah blah”<nods off>. Local LLM hosting is slow. You do you.

  

“Quantized” means something like “we made it smaller by rounding off the numbers, which reduces accuracy a bit; it will run on smaller systems but won’t be as good.” Mathematicians will tell you some gobbledygook about matrices and floating point precision, just say “that’s really interesting” and then act surprised and point behind them and say “look, is that a tensor?” and then run away when they turn their back to you.

## Mad AI Skillz

This post turned out to be much longer (20+ pages) than I thought it would be; all my tips for agentic coding are in [part 2](https://efitz-thoughts.blogspot.com/2025/08/my-experience-creating-software-with_22.html).