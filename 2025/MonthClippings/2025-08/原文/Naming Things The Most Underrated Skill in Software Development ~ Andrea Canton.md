---
title: "Naming Things: The Most Underrated Skill in Software Development ~ Andrea Canton"
source: "https://andreacanton.dev/posts/2025-08-23-naming-things/"
author:
  - "[[Andrea Canton]]"
published: 2025-08-23
created: 2025-08-26
description: "Website of Andrea Canton a vegetarian fullstack developer based in Verona, Italy."
tags:
  - "clippings"
---
## Naming Things: The Most Underrated Skill in Software Development

As a software developer, product owner, or business analyst, one of the most underrated yet essential skills is naming things. I truly believe it’s the number-one skill every software engineer should master. Scientific research and expert opinions back this up.

Let me start with a personal horror story.

A colleague designed our database structure and named individual product items **“BillOfMaterials.”** He used the Italian term *distinta prodotti*, which technically meant that in his domain. The developer who started coding didn’t question it and just moved forward.

When I joined, I struggled with the cognitive dissonance: every single item was called “BillOfMaterials”—a plural collection name used for individual objects. It was clear to me that **`ProductItem`** would have been a better name. But I hesitated, thinking it was too late to change.

## The Moment of Truth

The problem became glaring when I had to explain our data structure to a new business analyst. She repeatedly made mistakes because she couldn’t grasp why individual items were called “BillOfMaterials.” The confusion wasn’t just in her head—it spread into functions, variables, and documentation across the codebase.

The snowball was rolling.

Finally, we coordinated a massive renaming effort. We changed 72 files and several database tables. All due to one misleading table name.

Bad naming is not just “clean code” perfectionism; it has real costs:

- **Onboarding delays:** New team members struggle to understand the system.
- **Communication breakdowns:** Business stakeholders lose track in technical discussions.
- **Slower development:** Developers waste mental energy translating meanings.
- **More bugs:** Confusion leads to incorrect assumptions and errors.
- **Expensive refactoring:** Fixing naming issues later becomes an ordeal.

Scientific studies confirm that meaningful identifier names significantly improve program comprehension and reduce cognitive load. One study showed programmers understand code faster and more accurately with meaningful names, compared to vague or single-letter ones <sup><a href="https://andreacanton.dev/posts/2025-08-23-naming-things/#user-content-fn-1">1</a></sup>.

## The Cascade Effect

Naming affects more than just one variable or function. One bad name creates a chain reaction. The confusing **“BillOfMaterials”** name infected every related concept, making everything harder to understand.

## What Good Naming Actually Does

Good naming isn’t about being “professional” or following strict conventions—it’s about building a **shared language** that makes complex systems clear.

A well-chosen name acts as **living documentation**. Developers and stakeholders can understand intent without digging into the details. Research shows developers rely on names even more than comments for comprehension <sup><a href="https://andreacanton.dev/posts/2025-08-23-naming-things/#user-content-fn-2">2</a></sup>. Good names reduce [cognitive load](https://en.wikipedia.org/wiki/Cognitive_load), speed up debugging, and smooth collaboration.

## A Simple Framework

After many naming successes and failures, I use this approach:

- Would a new team member understand this name without extra context?
- Does the name describe what it **is** or what it **does**?
- Can I explain the concept clearly to a business stakeholder?
- Will it still make sense if requirements evolve?

Watch out for names that need mental translation, generic words like **data**, **manager**, or **handler**, irrelevant jargon, or abbreviations that cause more confusion than they save <sup><a href="https://andreacanton.dev/posts/2025-08-23-naming-things/#user-content-fn-3">3</a></sup>.

Great names don’t happen in isolation. Ask teammates for feedback during code reviews. Sometimes a fresh pair of eyes catches ambiguities you can’t see.

Also, AI tools can be great brainstorming partners. For example, when stuck with a name like **SettingsManager**, giving context to AI might produce alternatives like `ProductUserConfig` or `UserPreferencesService` to spark discussion.

This transforms naming from a solo chore into a shared effort, building a language everyone uses and trusts.

## The 10-Minute Investment

Spending ten minutes carefully picking a name may feel like overthinking—but it pays off.

Those ten minutes save hours of confusion, days of miscommunication, and weeks of costly refactoring. Our big **BillOfMaterials** renaming could have been avoided with a little upfront care.

## The Bottom Line

Every name you choose shapes how easy or hard the future will be for yourself and your team.

When tempted to accept vague or confusing names, remember: that choice echoes through dozens of files and months of development.

**Name it like your future self’s sanity depends on it.  
Because it does.**

[^1]: D. Feit, “Effects of Variable Names on Comprehension: An Empirical Study,” *ICPC*, 2017. [Link](https://www.cs.huji.ac.il/~feit/papers/Names17ICPC.pdf)

[^2]: P. Hilton, “Naming guidelines for professional programmers,” Hilton Foundation, 2025. [Link](https://hilton.org.uk/presentations/naming-guidelines)

[^3]: M. Makimo, “Naming conventions in programming – a review,” 2025. [Link](https://makimo.com/blog/scientific-perspective-on-naming-in-programming/)