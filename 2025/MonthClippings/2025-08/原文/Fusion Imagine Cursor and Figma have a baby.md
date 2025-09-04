---
title: "🐴 Fusion: Imagine Cursor and Figma have a baby"
source: "https://designwithai.substack.com/p/fusion-imagine-cursor-and-figma-have-a-baby?utm_source=post-email-title&publication_id=2297988&post_id=169235177&utm_campaign=email-post-title&isFreemail=true&r=53wl0h&triedRedirect=true&utm_medium=email"
author:
  - "[[Xinran Ma]]"
published: 2025-08-10
created: 2025-08-26
description: "Explore Fusion by Builder.io: connect to your codebase, use YOLO mode, edit designs, send PRs, connect to your design systems with this key feature guides."
tags:
  - "clippings"
---
### A detailed walkthrough of its special features

“I wish Cursor and Figma could have a baby.”

Someone commented that during one of my AI courses earlier this year.

Cursor is a popular tool among developers. You can do a lot with it. But it’s just not a designer-friendly tool. And you would struggle with it more if you have minimal technical experience.

On the other hand, you can view and edit designs in Figma intuitively. So if Cursor and Figma had a baby, we could get the best of both worlds.

**[Fusion](https://www.builder.io/fusion)** is like that baby.

It is an intriguing AI tool created by the Builder.io team. It is similar with Lovable, but with more features such as connecting to an existing codebase, sending a PR, editing the design in detail.

Today, I’ll walk you through what stood out to me about Fusion.

---

## Intriguing Interface

Fusion has three modes that users can switch to—Interact, Code, and Design.

### Interact

Interact Mode is the most typical type of interface that you would see in any of other AI prototyping tools. On the one side is the chat window; on the other is the preview.

![](https://substackcdn.com/image/fetch/$s_!9u_N!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F140f799b-0c25-42aa-ba10-a77f84069e28_3830x2102.png)

Interact Mode

### Code

Code Mode is also commonly seen in other similar tools.

![](https://substackcdn.com/image/fetch/$s_!KA9d!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fbc85a8ef-1b8f-4e2f-bd94-4d043cc1b544_3830x2102.png)

Code Mode

### Design

Design Mode is what makes it special. It offers many more editing capabilities than tools like Lovable. It has a solid editing panel that reminded me of Figma’s.

![](https://substackcdn.com/image/fetch/$s_!xM2i!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F04cc72f9-2835-4358-bfff-26ff21775750_3830x2102.png)

Design Mode

---

## Send a PR

As a designer, “Send a PR” was one of the tech jargon terms I learned after countless meetings with developers.

It means “pushing your code and requesting that it be merged”. If the team approves, it’s merged into the main branch—in other words, your code update becomes official.

But that’s traditionally a developer’s job. If you’re not a developer and spot minor visual bugs, like spacing, color, or font issues, you probably have to take screenshots, make callouts, and ask developers to fix them. On top of the back-and-forth communication, these fixes are often low priority for developers. They have more important tasks to handle.

What if, with AI’s help, you could make those fixes yourself and send a PR?

Granted, the updated code would still need review from developers, but this workflow could open up interesting possibilities for certain teams.

### How it works

If you already have a GitHub repo, you can hook it up in Fusion. If not, you can generate the design first, then click Create Repo in the top-right corner to create a new repo.

Then, follow these steps as shown in the demo below:

1. Switch from Interact Mode to Design Mode.
2. Make your design revisions.
3. Click Apply Visual Changes in the top navigation bar.
4. Click Send PR in the top navigation bar.
5. Your team is able to see the PR on Github.
<video src="blob:https://designwithai.substack.com/99239559-8d75-4b27-9f7a-9ae9a4331b25"></video>

---

## Connect to Design System

This is very exciting, although it’s still in Beta and the experience is not as smooth as I expected.

### How it works

Set up a new project and add your design system repo.

![](https://substackcdn.com/image/fetch/$s_!Cu0m!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ffc88d15e-90b8-4afa-99eb-a700b7f79c2e_1496x929.png)

Set up a new project

![](https://substackcdn.com/image/fetch/$s_!LPND!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fa6977bef-5048-4d88-b750-dcb8c0645fd8_1410x930.png)

Choose a commit mode

In the settings, you can select how you prefer to commit to the repo.

I tested different design system repos, but it either took a lot of time to connect or ran into the error below:

![](https://substackcdn.com/image/fetch/$s_!i0Wh!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fcc6f8bdc-3611-4d30-9268-0e72cd64ffca_1477x910.png)

Error connecting to a design system repo

So while connecting to design systems is such an attractive feature, it’s still not a reliable workflow to me yet based on its accuracy and scalability. That said, I know Fusion’s enterprise plan offers customized support and I plan to learn more about it.

### Alternative Option

Instead of connecting to a design system repo, I found that it’s so much easier to get a better result by dramatically narrowing down the context.

For example, below is a prompt I used when I was making design revisions. I selected a component, then included a link of reference that was only about that component.

```markup
Change to this style:

https://base.uber.com/6d2425e9f/p/756216-button/b/05bb77/i/165897280
```

![](https://substackcdn.com/image/fetch/$s_!UhGv!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fb1792063-e083-460a-91b0-45f38c83cb27_1461x881.png)

Select a component and provide a URL for reference

The result was quite accurate, using the specific style I asked for:

![](https://substackcdn.com/image/fetch/$s_!kyNP!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fedcc8236-b38a-4417-a7c1-360b6e03ccb3_1478x909.png)

AI updated the component accordingly

---

## Import Design from Figma

Since Build.io already has a Figma plugin, attaching a screen from Figma to Fusion is straightforward. You simply use the plugin to export code.

![](https://substackcdn.com/image/fetch/$s_!2Jmd!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F1eab3c9a-da2d-4357-9fae-b69e2c92c436_1496x928.png)

Export code via Builder.io’s Figma plugin

After code exporting is done, go to Fusion, click into the prompt box, and press Ctrl+V. Then the design is attached.

Then I simply asked “Recreate this as accurately as possible.”

![](https://substackcdn.com/image/fetch/$s_!2led!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F6275d111-3025-41cd-afbc-98b048c594e1_1408x843.png)

Attach the design in Fusion’s prompt window

Here’s the result:

![](https://substackcdn.com/image/fetch/$s_!nPVO!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F0f335165-c9a5-4543-9520-b650cd671ad5_1374x907.png)

Fusion recreated the design based on code

To compare, I also ran with attaching a screenshot instead. The result of code exporting via plugin was more precise than just screenshots:

![](https://substackcdn.com/image/fetch/$s_!SAyI!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc097d23c-2924-4df1-b049-7e1d91eb8bab_1464x880.png)

Try recreating the design based on a snapshot instead

To further validate my point, I also attached the screenshot in Lovable to generate the design accordingly and the result was not as good either.

![](https://substackcdn.com/image/fetch/$s_!GYK6!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F75bb2d04-5551-4c77-b282-9e9e4564d9ab_1406x823.png)

Try recreating the design in Lovable based on the snapshot

---

## YOLO Mode

I was surprised that Fusion uses YOLO mode by default. I have not seen this in other similar prototyping tools like Lovable. (Cursor has it if you set that up.)

So YOLO refers to the automatic execution of commands suggested by the AI, without your confirmation. It’s essentially “auto-run”.

For example, I asked Fusion to create a quote generator app with a one-liner, simple prompt. Then it kept running, identifying and fixing bugs, and the whole process took over two minutes.

![](https://substackcdn.com/image/fetch/$s_!P_NX!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F8689082e-a365-411b-8144-7669df529202_3232x2256.png)

AI is auto-running in the chat window

This is a double-edge sword for me.

On the one end, a simple prompt like this took longer than other similar tools, but on the other hand, you can just sit there watching it solve problems automatically and the result was good.

![](https://substackcdn.com/image/fetch/$s_!Fa9D!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc6bbf702-28ef-4560-a507-6efda39147b7_800x470.gif)

The clickable prototype Fusion generated

---

Thanks for reading. Curious about your experience with **[Fusion](https://www.builder.io/fusion)**.

Let me know in the comments.

See you next time,

Xinran

\-

*P.S. Today’s newsletter has two “firsts”.*

- *First time having a video in it—I’ve always used GIFs before.*
- *First time ignoring the “Post too long for email” alert from Substack instead of reducing the amount of content—hope you can still read it well.*