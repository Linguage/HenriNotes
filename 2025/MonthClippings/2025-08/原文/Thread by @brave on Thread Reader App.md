---
title: "Thread by @brave on Thread Reader App"
source: "https://threadreaderapp.com/thread/1958152314914508893.html?utm_campaign=topunroll"
author:
  - "[[@brave]]"
published:
created: 2025-08-26
description: "@brave: AI agents that can browse the Web and perform tasks on your behalf have incredible potential but also introduce new security risks. We recently found, and disclosed, a concerning flaw in Perplexity's Comet br...…"
tags:
  - "clippings"
---
## Enter URL or ID to Unroll

AI agents that can browse the Web and perform tasks on your behalf have incredible potential but also introduce new security risks.  
  
We recently found, and disclosed, a concerning flaw in Perplexity's Comet [browser](https://threadreaderapp.com/thread/?utm_campaign=topunroll#) that put users' accounts and other sensitive info in danger. ![Image](https://pbs.twimg.com/media/GyzACvZXUAAC5kO.jpg)

This security flaw stems from how Comet summarizes websites for users.  
  
When processing a site's content, Comet can't tell content on the website apart from legitimate instructions by the user. This means that the browser will follow commands hidden on the site by an attacker.

These malicious instructions could be white text on a white background or HTML comments. Or they could be a social media post.  
  
If Comet sees the commands while summarizing, it will follow them even if they could hurt the user. This is an example of an indirect prompt injection.

One example attack:  
1\. A Comet user sees a Reddit thread where one comment has hidden instructions.  
  
2\. The user asks Comet to summarize the thread.  
  
3\. Comet follows the malicious instructions to find the user's Perplexity login details and send them to the attacker. <video controls=""><source src="https://video.twimg.com/amplify_video/1958150857653919744/pl/-jrSrKzDdd9acFWL.m3u8?container=fmp4" type="application/x-mpegURL"><br><source src="https://video.twimg.com/amplify_video/1958150857653919744/vid/avc1/1158x720/qLVozKd45wsQzbIY.mp4" type="video/mp4"><br><source src="https://video.twimg.com/amplify_video/1958150857653919744/vid/avc1/578x360/iz7HhzZbgtk0iH_u.mp4" type="video/mp4"><br><source src="https://video.twimg.com/amplify_video/1958150857653919744/vid/avc1/1736x1080/WhU9WNIe-3PJYa2F.mp4" type="video/mp4"><br><source src="https://video.twimg.com/amplify_video/1958150857653919744/vid/avc1/434x270/p6GlP1EhV8AJBA6m.mp4" type="video/mp4"><br><source src="https://video.twimg.com/amplify_video/1958150857653919744/vid/avc1/3452x2146/aCbMjAInY26kAoCG.mp4" type="video/mp4"></video>

This attack demonstrates the risks presented by AI agents operating with full user authentication across multiple sites.  
  
New security measures are needed to make agentic browsing safe.

In today's blog post, we share more details on this vulnerability and discuss potential protections against other attacks of this nature.  
  
Perplexity has patched this error since we reported it to them.

Security and privacy cannot be an afterthought in the race to build more capable AI tools.  
  
In the next blog post of this series, we'll discuss Brave's efforts to deliver secure AI browsing to our nearly 100 million users. Stay tuned!

• • •

Missing some Tweet in this thread? You can try to [force a refresh](https://threadreaderapp.com/thread/?utm_campaign=topunroll#)

**Keep Current with [Brave](https://threadreaderapp.com/user/brave)**

![Brave Profile picture](https://pbs.twimg.com/profile_images/1951131044171644928/7RtvNuKF_bigger.jpg)

Stay in touch and get notified when new unrolls are available from this author!

**This Thread may be Removed Anytime!**

![PDF](https://threadreaderapp.com/assets/icon-pdf-ceb3626bf7a8daddf0ed92c9f804942d567013f5556e880d9c5e2c234ebe021d.png)

Twitter may remove this content at anytime! Save it as PDF for later use!

Influencer marketing courses

## More from @brave

Aug 11

AI assistants collect personal information, store your conversations on their servers and use your inputs to train their models.  
  
Leo doesn't. Here's how we built privacy into every part of the Brave [browser's](https://threadreaderapp.com/thread/?utm_campaign=topunroll#) AI assistant...

All of the AI models offered through Leo are hosted on our own infrastructure to ensure user privacy.  
  
We don’t retain your conversations with Leo or use them for model training. We also don’t collect any personal data such as your IP address.

This same approach applies to any documents or images you ask Leo to analyze. They’re discarded immediately after Leo answers your prompt.  
  
Other companies retain these files on their servers.

Jul 23

New testing confirms that Brave for Android is outperforming the competition. 🏆  
  
It's faster, uses less battery and CPU, and consumes less mobile data and Wi-Fi bandwidth than other major [browsers](https://threadreaderapp.com/thread/?utm_campaign=topunroll#). 🧵

We conducted performance tests with a Google Pixel 6a using our open-source BLaDE infrastructure.  
  
In the tests, we measured Brave against four competing browsers: Chrome, DuckDuckGo, Edge and Firefox.  
  
Here's what we found...

Battery and CPU:  
  
Brave uses 3.9% less energy than Chrome, Edge, and Firefox and 5.5% less CPU on average.  
  
It uses 23.7% less energy and 17.6% less CPU than DuckDuckGo. On review, we found a resource management issue in DDG that we shared with its team: [github.com/duckduckgo/And…](https://github.com/duckduckgo/Android/issues/6433)

Apr 23

Users can't trust Google.  
  
Google has lied repeatedly to Chrome users about plans to protect their privacy.  
  
This week, it broke yet another promise. 🧵

In 2020, Google announced plans to remove third-party cookies from Chrome by 2022.  
  
Then Google delayed the removal of these trackers to 2023.  
  
Then Google delayed it to 2024.  
  
Last summer, the company announced it wouldn't block third-party cookies after all.

While Google dragged its feet, nearly every other [browser](https://threadreaderapp.com/thread/?utm_campaign=topunroll#) began blocking third-party cookies.  
  
Chrome is now the worst browser for user privacy by far. Users' data is collected through cookies (and other tracking methods) so they can be targeted with ads.

Sep 17, 2024

Did you just download Brave?  
  
Here are a few things you should do right away to get the most out of our browser... 🧵

1) Import settings/bookmarks  
  
When you install Brave on desktop, you’ll be prompted to import your data from previous browsers.  
  
If you don’t do this at setup, you can do it at any time by heading to Settings -> Get Started and clicking “Import bookmarks and settings.” <video controls=""><source src="https://video.twimg.com/ext_tw_video/1836089848869912577/pu/pl/ScVji-0DkUFxfatG.m3u8?tag=12&amp;container=fmp4" type="application/x-mpegURL"><br><source src="https://video.twimg.com/ext_tw_video/1836089848869912577/pu/vid/avc1/320x320/XhNKQltehkeeVcxM.mp4?tag=12" type="video/mp4"><br><source src="https://video.twimg.com/ext_tw_video/1836089848869912577/pu/vid/avc1/540x540/pLuhrwUVCXrnstwF.mp4?tag=12" type="video/mp4"><br><source src="https://video.twimg.com/ext_tw_video/1836089848869912577/pu/vid/avc1/720x720/Zkwv9K5uH1OIFhdb.mp4?tag=12" type="video/mp4"></video>

2) Set up syncing  
  
If you use Brave on more than one device, you can synchronize your browsing data across all of them.  
  
Go to Settings -> Sync to start a sync chain.

Aug 26, 2024

Google Chrome's proposed "Related Website Sets" (RWS) feature will further undermine Chrome users' privacy.  
  
RWS allows companies to track you across sites without your knowledge.

If two sites are owned by the same organization, Chrome will allow third-party cookies between them.  
  
This would let Google link YouTube videos you watch to your Google profile, even when you’re not logged into YT, and even after third-party cookies are deprecated in Chrome.

Google justifies RWS by saying that users expect two sites owned by the same company to share data.  
  
However, a study we conducted with @univofstandrews, @imperialcollege, and @hkust showed that users can't consistently tell if two sites are related: [brave.com/blog/related-w…](https://brave.com/blog/related-website-sets/)

## Send Email!

Email the whole thread instead of just a link!

![email this](https://threadreaderapp.com/assets/emailthisv3-19db7e62925577c40531c0104134c2d93d1434dc7b3d7b20b761bea35c595420.gif)