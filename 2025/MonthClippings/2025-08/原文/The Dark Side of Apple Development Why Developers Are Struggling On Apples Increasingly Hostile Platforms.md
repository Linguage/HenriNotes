---
title: "The Dark Side of Apple Development: Why Developers Are Struggling On Apple’s Increasingly Hostile Platforms"
source: "https://www.magiclasso.co/insights/apple-development/"
author:
  - "[[Magic Lasso Adblock]]"
published:
created: 2025-08-26
description: "Once upon a time, developing for Apple was an exciting, rewarding challenge. Apple built world-class hardware and software, and developers created incredible apps that made those devices indispensable. It was a win-win. But in 2025, that relationship has soured."
tags:
  - "clippings"
---
![The Dark Side of Apple Development: Why Developers Are Struggling On Apple’s Increasingly Hostile Platforms image](https://www.magiclasso.co/insights/apple-development/apple-development-header.webp)

Once upon a time, developing for Apple was an exciting, rewarding challenge. Apple built world-class hardware and software, and developers created incredible apps that made those devices indispensable. It was a win-win. But in 2025, that relationship has soured.

Apple has transformed into a trillion-dollar giant that sees developers not as partners, but as a resource to control, extract from, and — when convenient — ignore.

The result? Apple now has the most hostile developer ecosystem of any major platform.

Endless bureaucracy, shifting rules, poor support, and ever-present potential of being “Sherlocked” make building apps for Apple a high-risk endeavour. And yet, many developers persist — because for many, [myself included](https://www.magiclasso.co/), there’s no other choice.

In this article, I’ll break down exactly why Apple’s platforms have become so toxic for developers and explore whether it’s time to look elsewhere.

Buckle up: it’s going to be a bumpy ride.

### On this page

- [An Imbalanced Relationship](https://www.magiclasso.co/insights/apple-development/#relationship)
- [Lots of Responsibilities, with Very Little Support](https://www.magiclasso.co/insights/apple-development/#responsibilities)
- [A High-Risk Endeavour](https://www.magiclasso.co/insights/apple-development/#risk)
- [What’s the alternatives?](https://www.magiclasso.co/insights/apple-development/#alternatives)

## An Imbalanced Relationship

Many years ago, Apple and developers had a symbiotic relationship.

Apple made great hardware and software, and developers made killer apps that helped sell devices. Remember how desktop publishing with third party software turned the Mac into a must-have tool? Those were the days.

In those days, platform owners knew the benefits that quality third party software could bring to their devices and supported developers accordingly.

But times have changed. Apple has grown into a trillion-dollar juggernaut. They no longer feel the need to find and nurture any killer apps. They don’t see the benefits of genuinely supporting developers, both big and small, in order to ensure their devices have the best software.

Sure, they’ll pay lip service to developers. But as in any relationship, don’t listen to the loving words of the perpetrator, instead observe their hurtful actions. Apple has continually created an environment and policies, along with nurturing a culture, that is detrimental and harmful to developers.

They see the millions of App Store apps, and just like any popular bully, can see the next victim at their door and justify their actions by pointing to their popularity.

Of course, they conveniently don’t ask the relevant questions.

Why, over the last 10 years, has every one of their new device categories been accompanied by a failed app ecosystem?

Why is the iPad still an afterthought for developers?

Why did the Apple Watch never really develop a rich app platform?

Why despite being launched as ‘it’s all about apps’, did the Apple TV never have any apps to talk about other than those for video streaming?

And finally, why with the launch of spatial computing and the Apple Vision Pro, was the platform so poisonous to developers that not even the most frenzied of Apple supporters could stomach it?

All to say that Apple is now so big, so financially successful and so smug that they no longer feel they need developers. And they act accordingly.

Rationally you could point to the failed platform launches of the last 10 years and their current antitrust issues to argue that they do need developer support. But Apple’s $42 billion in quarterly operating profit says otherwise. Until it hits their bottom line, it’s unlikely that Apple’s behaviour will change.

## Lots of Responsibilities, with Very Little Support

Developing for Apple isn’t just about writing great code — it’s about navigating a bureaucratic obstacle course filled with red tape, secret handshakes, and hidden pitfalls.

Over time, the App Store’s requirements have become more and more burdensome. There are so many requirements now just to launch or update an app, that it has become a nightmare that would make any bloated government department proud.

Multiple agreements that must be reviewed and signed, and re-signed, whenever Apple makes a change. Regional Tax forms and Compliance agreements. Digital Services Acts that require the procurement and publishing of a public phone number and physical address.

Privacy policy and privacy checklists and labels for each app release, including declarations of the type of encryption that may or may not be used. Content rights, license agreements, age ratings, ICP filing numbers. Declaring app sandbox capabilities. And then, all the additional work that needs to go into setting up subscriptions or in-app-purchases correctly.

It has become overwhelming even for experienced App Store developers. The path for new developers must be terrifying.

This is not the type of environment that occurs when a platform owner is attempting to simplify, nurture and support developers.

It’s these hidden pitfalls and requirements which take up the most time, that cause the most frustrations, and that ultimately make you question why you’re bothering to develop on an Apple platform in the first place.

Once you manage to get through the bureaucratic maitre-de, you’ll be seated at a developer table where you’ll find undercooked technical documentation, lacklustre support and elitist serving staff who’ll rarely deign to communicate with you.

Apple developer relations and support regularly feels like trying to get a response from an ancient oracle — except instead of wisdom, you get vague replies, cryptic documentation, and a reminder that Apple knows best (even when it clearly doesn’t).

When your app hits an edge case – which any reasonably complex app is likely to hit often – then you are left to question why the behaviour is occurring, when you are following all documented requirements.

For example, in [my ad blocking app](https://www.magiclasso.co/), I load content blocking rules into Safari.

Now from experience, I know there is a limit on the number of rules that can be loaded. This isn’t documented anywhere. You are just meant to know the limit. Possibly from searching the internet for days and then seeing what other developers have come across. Or, perhaps from finding a small detail in a dot point release of Safari’s release notes, from 5 years ago.

Fine, now you know what the limit is.

Unfortunately – and what isn’t documented anywhere – is that although you can load that many rules, you are unlikely to actually be able to do so. There is also a hard, undocumented, memory limit on the extension process that loads the rules. A memory limit that kills the extension and means the app doesn’t work if it’s exceeded. A memory limit that isn’t documented, isn’t defined and isn’t known until you spend weeks trying to determine why your app is not working. An undocumented memory limit that is also different across iOS and macOS.

These rough edges, undocumented limitations and unclear use cases are rife throughout Apple’s APIs and platforms.

This is frustrating enough, but it gets even more frustrating when you try and request Apple’s help. Posting on the Apple Developer Forums or requesting DTS (Developer Technical Support) is often unhelpful.

First, you’ll be lucky to get a response. Second, if you do get a response, it will probably take multiple back and forths before the responder acknowledges what you can prove is occurring. Then they’ll likely state this is expected behaviour, note that you should have known this – despite there being no known public human record of this ‘known’ behaviour on the internet – and close the ticket as completed.

These edge cases happen frequently. In any complex system, edge cases are understandable; but the lack of useful documentation and lacklustre support is not.

Developers aren’t expecting to be supported for free.

In my case, via my app [Magic Lasso Adblock](https://www.magiclasso.co/), I pay Apple tens of thousands of dollars per year in App Store commissions. However, despite huge ongoing payments to Apple, it doesn’t improve the quality of support received.

## Needing to Run Fast In Order to Stand Still

If you’re an indie Apple developer, you’re on a treadmill that never slows down.

Apple’s annual OS updates mean a constant stream of changes, and unlike Apple — where teams of engineers handle updates — you’re expected to keep up with everything solo. The annual OS release cycle forces developers to scramble to update their apps, even if nothing is broken.

Apple’s constant API changes and deprecations create an ongoing headache for developers. Swift and SwiftUI continue to evolve so quickly that learning them feels like chasing a moving target, with major shifts that often require rewriting large portions of code.

StoreKit changes made in-app purchases a moving target as well, forcing developers to adapt to new implementations. StoreKit 2 completely changed the API structure, forcing rewrites to systems that had been working for years.

Other examples abound: UIKit and AppKit developers had to rethink entire UI structures when Apple pushed SwiftUI as the future. Core Data, long a staple for managing persistence, has been overshadowed by SwiftData, requiring yet another major shift. The introduction of new concurrency models — first Grand Central Dispatch, then Combine, and now async/await — may mean rewriting asynchronous code multiple times over in just a few years.

For Apple, these changes represent progress. For developers, they represent an endless cycle of busy maintenance work that doesn’t always improve their apps, but is necessary just to keep them running.

This rapid iteration is business as usual for Apple, a way to keep their annual iPhone device sales and upgrades occurring. For indie developers, it’s an endless maintenance burden that yields little financial reward.

Keeping an app up to date isn’t just about compatibility — it’s about survival. Fall behind, and your app might stop working, get rejected in the next app submission, or be downgraded in App Store search rankings. The sheer volume of upkeep makes it difficult to focus on actual innovation, leaving many developers feeling like they’re running fast just to stay in place.

All platforms require some measure of constant maintenance. However the pace of change and deprecations that occur in the Apple ecosystem force an unprecedented level of sustained maintenance.

As a developer you can put off a lot of these items for as long as possible, but eventually, the overwhelming technical debt will need be paid.

## A High-Risk Endeavour

After dealing with the lopsided relationship, persevering through the App Store baeacuracy, and creating a killer app that needs excessive ongoing maintenance, you may think that the Apple developer experience will be smooth sailing from then on.

Unfortunately not.

Building a successful app for an Apple platform is kind of like playing poker at a table where Apple is both the dealer and the house. The odds are rarely in your favour. Once you have an app out in the word, there are two main difficulties which will continue to haunt any successful app developer.

### Being “Sherlocked”

Apple has a history of looking at successful third party apps and thinking, “We’ll take that, thanks.” Competing with Apple on its own platform is like opening a coffee shop inside a Starbucks — good luck with that.

Over the years, developers have watched Apple integrate features inspired by (or outright copied from) third party apps into macOS and iOS. Whether it’s password managers, weather apps, or email clients, Apple has a habit of releasing native solutions that make independent alternatives less viable. And, of course, they have the advantage of deep system integration that no third party app can match.

The EU is looking unkindly on this behaviour, but Apple continues to do everything in its power to retain the status quo.

So if you are fortunate enough to develop a successful app, the next stage of emotion is wondering when Apple will see that success and decide to crush it for their own gain. And when they do, there is nothing you can do about it.

### The App Store Rejection Rollercoaster

The unpredictability of the App Store makes running a business on Apple’s platforms a high-stakes gamble. One rule change, one policy enforcement spree, or one algorithm tweak could sink your app overnight.

Worse still, even before you have a successful app, you could spend months — if not years — developing the app, only to discover that Apple rejects it outright when you finally submit it. There’s no way to get pre-approval, no way to test the waters, and no guarantee that the work you’ve poured into a project will ever see the light of day. It’s a level of uncertainty that makes planning a long-term business strategy nearly impossible.

Even if another app does exactly the same thing that your new app does, it’s no guarantee that it will be accepted on the App Store. Apple has created an intentionally opaque and inconsistent way in which it enforces App Store rules. This ensures control is always in Apple’s hands and keeps developers constantly anxious about how rules may, or may not, be applied.

A platform where the owner is both your judge and your most ferocious competitor, should kill all investment in that platform. Unfortunately for app developers, the App Store grew to a critical mass quickly that despite the extraordinarily unfair playing field, these are the established rules.

## What’s the alternatives?

Apple may be starting to see the consequences of its own actions. Every new platform it has launched in the last decade — the iPad, Apple Watch, Apple TV, and now Vision Pro — has struggled to gain meaningful developer support. Why? Because developers are tired of being in an abusive relationship.

If I were starting fresh today, I wouldn’t build my business on Apple’s ecosystem.

Instead, I’d consider web development, where you can control your own distribution, pay no platform commissions and not deal with a mercurial gatekeeper. Or perhaps focus more on cross-platform development, so you’re not locked into a single company’s walled garden.

Finally even becoming a content creator, on a platform like YouTube, seems like a more stable way to make a living these days.

The reality is that Apple’s development ecosystem has become a high-risk, high-maintenance environment. New developers looking for a sustainable career path would do well to consider alternatives that offer more control and fewer headaches.

## Conclusion

Developing for Apple used to be a thrilling challenge. Now, it feels more like an endurance test with constantly shifting rules.

While iOS and macOS remain incredible platforms from a technical perspective, the business side of things makes it harder and harder to justify the investment.

If you’re already in Apple’s ecosystem, the best strategy might be to diversify and reduce reliance on their platforms.

If you’re just starting out, my advice? Look elsewhere — unless you really enjoy jumping through flaming hoops with no safety net.

---

If you liked this article and want a fast, efficient and high performance ad blocker for the iPhone, iPad and Mac with native Safari integration, please considering giving my app [Magic Lasso Adblock](http://www.magiclasso.co/) a try.

![Community icon](https://www.magiclasso.co/img/homepage/community-icon.svg)

## Join a community of over 350,000 users

Try Magic Lasso Adblock for free today![The Best Safari Ad Blockers for iPhone, iPad & Mac (2025 Edition)](https://www.magiclasso.co/insights/best-safari-ad-blockers/best-safari-ad-blockers-2025-header.webp) ![Magic Lasso Adblock 2025 Year in Review: Focus Fuelled Our Growth](https://www.magiclasso.co/insights/ad-blocker-year-in-review-2025/year-in-review-2025-header.webp) ![Block Ads in iPhone, iPad and Mac Apps with Magic Lasso Adblock v5.0](https://www.magiclasso.co/insights/app-ad-blocking/app-ad-blocking-header.webp) ![Safari Extensions: The Ultimate Guide to Install, Use, and Manage on iPhone, iPad and Mac](https://www.magiclasso.co/insights/safari-extensions-guide/safari-extensions-guide-header.webp) ![Introducing Our Biggest Ad Blocking Performance Update Ever](https://www.magiclasso.co/insights/ad-blocking-performance-update/ad-blocking-performance-update-header.webp) ![How to block ads: The Ultimate 2025 Guide to Blocking Ads on Your Devices](https://www.magiclasso.co/insights/how-to-block-ads/how-to-block-ads-header.webp) ![The Best Web Browser in 2025](https://www.magiclasso.co/insights/best-web-browser-2025/best-web-browser-2025.webp) ![How to Block YouTube Ads (August 2025 Edition)](https://www.magiclasso.co/insights/how-to-block-youtube-ads/how-to-block-youtube-ads-header.webp) ![Introducing Regional Ad Blocking](https://www.magiclasso.co/insights/regional-ad-blocking/regional-ad-blocking-header.webp) ![The Best Web Browser in 2024](https://www.magiclasso.co/insights/best-web-browser/best-web-browser-header.webp) ![A Love Letter to Safari: The Unsung Hero of Browsing](https://www.magiclasso.co/insights/safari-love-letter/safari-love-letter-header.webp) ![Magic Lasso Adblock 2024 Year in Review](https://www.magiclasso.co/insights/ad-blocker-year-in-review-2024/2024-year-in-review.webp) ![Dear Safari, 4 Things I Hate About You](https://www.magiclasso.co/insights/dear-safari/dear-safari-header.webp) ![Family Sharing has arrived](https://www.magiclasso.co/insights/family-sharing/family-sharing-header.webp) ![Magic Lasso Redesigned](https://www.magiclasso.co/insights/magic-lasso-redesigned/magic-lasso-redesign-header.webp) ![Improvements to YouTube ad blocking](https://www.magiclasso.co/insights/youtube-adblocking-improvements/youtube-adblocking-improvements.webp) ![Introducing Adblock Performance Insights](https://www.magiclasso.co/insights/adblock-performance-insights/performance-insights-header.webp) ![Introducing Tap to Block, Custom Rules and Strict Mode](https://www.magiclasso.co/insights/introducing-magic-lasso-adblock-4/introducing-4-header.webp) ![Magic Lasso Adblock 2023 Year in Review](https://www.magiclasso.co/insights/ad-blocker-year-in-review-2023/2023-year-in-review.webp) ![Apple Should End Their Google Search Partnership](https://www.magiclasso.co/insights/apple-google-search-partnership/apple-google-search-partnership.webp) ![Safari's Dangerous Defaults](https://www.magiclasso.co/insights/safaris-dangerous-defaults/safaris-dangerous-defaults.webp) ![Is Chrome the new IE?](https://www.magiclasso.co/insights/is-chrome-the-new-ie/is-chrome-the-new-ie.webp) ![The Triumph of Safari](https://www.magiclasso.co/insights/triumph-of-safari/triumph-of-safari.webp) ![The Tragedy of Safari](https://www.magiclasso.co/insights/tragedy-of-safari/tragedy-of-safari.webp) ![The Best YouTube Ad Blocker](https://www.magiclasso.co/insights/youtube-adblocking/youtube-adblocking-header.webp) ![Double Your Battery Life with Magic Lasso Adblock for iPhone, iPad & Mac](https://www.magiclasso.co/insights/adblock-that-doubles-battery-life/doubles-battery-life.webp) ![Introducing Magic Lasso Adblock 2.0](https://www.magiclasso.co/insights/introducing-magic-lasso-adblock-2/introducing-2-header.webp) ![“Hey Google, stop tracking me”](https://www.magiclasso.co/insights/hey-google/hey-google.webp) ![Google’s attempts to undermine ad blockers](https://www.magiclasso.co/insights/google-undermines-adblock/google-undermines-adblock.webp) ![What difference does an adblocker really make?](https://www.magiclasso.co/insights/difference-adblocking/difference-adblocking.webp) ![Magic Lasso Adblock 2018 Year in Review](https://www.magiclasso.co/insights/ad-blocker-year-in-review-2018/ml-adblock-year-2018.webp) ![Why use an adblocker?](https://www.magiclasso.co/insights/why-adblock/why-adblock.webp)