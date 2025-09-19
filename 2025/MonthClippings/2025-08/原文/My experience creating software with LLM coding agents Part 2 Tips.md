---
title: "My experience creating software with LLM coding agents - Part 2 (Tips)"
source: "https://efitz-thoughts.blogspot.com/2025/08/my-experience-creating-software-with_22.html"
author:
  - "[[authorization]]"
published: 2025-08-23
created: 2025-08-26
description: "This post details my experiences creating software with LLM coding agents, emphasizing that what you do with AI agents is ‘creation’, not ju..."
tags:
  - "clippings"
---
*This post details my experiences creating software with LLM coding agents, emphasizing that what you do with AI agents is ‘creation’, not just 'coding,' and sharing what worked for me. This is not 'The One True Path To AI Success.'  
*  

## tl;dr:

- I’m not a professional developer, just a hobbyist with aspirations
- I wanted to accomplish a coding project beyond my skill level and have been experimenting with agentic coding tools for several months (spoiler: mostly success)
- You should use Anthropic’s Claude Sonnet model for complex coding tasks.
- Experiment with various agents and models; be adaptable as the field evolves quickly. I prefer Claude Code and Roo Code at this time.
- If you are a heavy user, ~~you should use pay-as-you go pricing; TANSTAAFL~~.*I [posted this on Hacker News](https://news.ycombinator.com/item?id=44991884) and was very forcefully corrected that with Anthropic in particular, you can use the [Claude Pro or Claude Max plan and auto-switch to pay-as-you-go](https://support.anthropic.com/en/articles/11145838-using-claude-code-with-your-pro-or-max-plan) if you run out of capacity.*
- If you are a light user, use your favorite free or “comes-with-my-monthly-subscription” chatbot and whatever model it comes with. I expand on what “light” means later but think “not very much at all, bash one-liners, single-file python scripts, etc.”
- [Part 1](https://efitz-thoughts.blogspot.com/2025/08/my-experience-creating-software-with.html) of this post has background and describes how I chose agent, model, and subscription type.

## Mad AI Skillz

I’ve learned a lot of tips and tricks (maybe even “skills”?) in getting more productive output from agentic AI and I wanted to share. This was actually the main point of me writing a blog post. I hope this helps you. I hope you share your tips with me and others.  

  

## Context

“Context” refers to the agent's short-term memory, including system prompts, standing instructions, and provided information, which the model uses for reasoning.  

  
Coding agents are really good at getting additional context if needed - they can add source code files, they can invoke local tools to extract particular information, and they’ll send that up to the model if needed.  
  
How the agent gets additional context is really important, as it significantly affects your experience. If you use a chat-based agent, you’ll have to paste or upload files manually. Some IDE-integrated agents require to to explicitly add files to context; these are a huge hassle when trying to make changes to nontrivial code bases with lots of files. Some, like Claude Code or Roo Code, automatically can use any file in your entire project with only a single approval.  
  
To get good results, give the AI model lots of context, but only context that is directly relevant to the task at hand. The model will get distracted by irrelevant content and give worse results than if you are careful. I’ve adopted a pattern that provides lots of context but gives meta-information about the context itself and I give the agent leeway to decide which of my standing context is relevant to the current task.  
  
I have started creating a context/ directory in the root of my projects, and modifying my user specific prompt (e.g. CLAUDE.md or.clinerules or AGENTS.md) to include instructions to the agent to look for context there. If you have a docs directory, tell the agent about it, too. I use context for internal (dev-only) stuff and docs for public-facing stuff. Here are relevant portions of my prompt:  
  
\`\`\`  
\- When starting, run the appropriate tool to list the files in the context directory and the docs directory.  
\- Read the README.md file in each of those directories to discover what each file is for and what kind of information is in it.  
\- Read any of the context or docs files that are relevant to the current prompt.  
\`\`\`  
  
Whenever I need the agent to document something, I have it write a markdown file and store it in context or docs, as appropriate. Whenever I make a significant change, I have the agent update the appropriate docs and README.  
  
➤ Be intentional and generous with context. Store context in a fixed place. Make your standing prompt to the agent tell the agent where to find your context and how to use it.  
  
➤ Save tokens (==$$$) by telling the agent what the context documents are before it has to read them all. Keep the context up to date.  
  

## Good Context is Where you Find It

A lot of my application is written in Typescript. I use node and pnpm to manage packages, and I chose two testing frameworks (Vitest & Cypress) for unit and integration testing, respectively. But every time my agent was writing tests, it kept writing them with Jasmine or Jest syntax, even though those weren’t in my project and even though the rest of the test file didn’t use that syntax and even though my standard prompt told it what to use and what not to use. I kept having to fix broken tests.  

  
Finally it occurred to me to put context where it was needed - directly in the test files. I had the agent to update all of the existing test files with the context I wanted. Now every time the agent reads a test file, it gets my test-related instructions reinforced. It has pretty much stopped making the mistakes it was making before.  
  
\`\`\`  
// This project uses vitest for all unit tests, with native vitest syntax  
// This project uses cypress for all integration tests  
// Do not use Jasmine or Jest, or Jasmine or Jest syntax anywhere in the project  
// Execute all tests using: "pnpm run test"  
// Execute this test only using: "pnpm run test" followed by the relative path to this test file from the project root.  
// Execute all tests for a component by using "pnpm run test:<componentname>"  
// Do not disable or skip failing tests, ask the user what to do  
\`\`\`  
  
You can also put context into individual comments in specific areas of files, like a comment before a function that tells the LLM to go read a doc before modifying that function.  
  
➤ To an LLM, everything is context, even the file that is being edited. Reinforce instructions or add special instructions in comments in source code files.  
  

## Too much context

Human developers usually build and maintain a lot of state about the project they are working on, in their head. Your brain automatically focuses on the important aspects and leaves out unimportant details - like you know that the code that does x is in /src/app/component/x.ts, but you don’t have to remember all the function names or lines of code.  

  
LLMs aren’t like that. They remember everything in a “session”. And LLMs have limited context windows - Gemini has a 1M token context window, Sonnet has a 200k token context window (update- since I first wrote this Sonnet now offers a 1M token context window for several times the price). To put it in perspective, 200k tokens will not hold my pnpm-lock.json file nor will it hold my openapi.json API specification. Every time I need the agent to touch those files, I avoid “out of context” errors and API failures (that invariably kill the session) by telling the agent specifically NOT to read the entire file, but to use tools to find and extract only the relevant lines from the files.  
  
\`\`\`  
Do not read pnpm-lock.yaml. The file is too large. If you need to read it, use tools to extract only the particular data that you need.

\`\`\`  
  
But there’s another problem with context: as context builds up during a session, the LLM starts to lose track of the big picture. This is kind of the opposite of what happens with humans. The key symptom is that the agent will e.g. “forget” that you were trying to get authentication working and instead will dive deep on some optimization to some side aspect of some function in your authentication system, and not bother fixing the core problem. They also have a recency bias- stuff very recent in the context window “outweighs” stuff early in the context window. So you’ll find the agent will start to ignore your standing instructions on coding guidelines, etc., and you’ll have to remind it.  
  
A lot of agents now have a “compact” feature, that will spend more tokens to take all the tokens from the current session, run them through an LLM to try to distill out the important stuff and discard the rest, and then start a new session with just the “compacted” context. Does it work? Yes. But I’m not sure it’s valuable unless it would be more than a couple of lines of typing to re-establish the task- or session-specific context that was needed. Remember the AI is not a human and it doesn’t remember complex state like humans do; I think compaction is humans trying to keep long sessions going because we think that it will be valuable like it would be to a human. But it’s not.  
  
So what’s the bottom line?  
  
➤ You need to watch your context size (all of the agents I have seen let you see how much context is in use) and you need to compact OR start a new session if (1) you are getting very low on available context, or (2) you notice that the agent seems to have lost the big picture and is going off on tangents or focusing overmuch on some recent side-quest.  
  
➤ Large files break sessions by exhausting context. If you need to work with a large file, tell the agent to use tools to only extract the needed information from the file.  
  
➤ Save tokens (==$$$) by skipping compaction and just starting a new session, giving a line or two of your own context if needed.  
  

## Bootstrapping context

If you think that the agent might struggle with something uncommon, then help the agent bootstrap itself by generating context up front.  

  
In my project, I am using a typescript library called X6 from a project called AntV. It’s written by the Alibaba team. The documentation is all in Chinese (with some English translations), as are the source code comments. There are examples that demonstrate some of the features. I knew from my experience using a similar library that the agent would likely struggle with figuring out how to use the library. So before I started, I had Gemini make me a [developer’s guide](https://github.com/ericfitz/tmi-ux/blob/main/context/Developers%20Guide%20AntVX6%20Graphing%20Library%20v2.md) by reading the source code and the examples. It’s not a great developer’s guide, but it does the job. Here was the prompt I gave Gemini; I ran it in thinking mode:  
  
\`\`\`  
I want you to write me a developer's guide for the latest 2.x version of the X6 graphing library from AntV. But I want you to write it by reading the code, which is at https://github.com/antvis/X6  
  
I want to document all the built-in APIs in the core library and on all the enumerated parameters each API supports.  
  
I also want you to generate similar documentation for the optional packages in the /packages directory of the source code.  
  
If you are considering leveraging any of the documentation or examples, you need to validate that the documentation or example actually matches what is currently in the code.  
  
Finally, I want you to describe how the functions are to be composed together to accomplish common tasks.  
\`\`\`  
  
➤ Predict areas that might be challenging for the LLM (you’ll develop a sense for this) and generate context before you start building, to help the agent with those areas  
  

## “Talking” with something that isn’t a person

Communication patterns are deeply ingrained in me, as are “manners”. I find it very hard not to say “ [please](https://futurism.com/altman-please-thanks-chatgpt) ” to an agent, and even though it’s not a person, I’ve never really talked to anything that’s not a person. I do notice that when you get mad at agents and especially if you curse (\`Damn it I specifically told you not to do that\`), then they stop being so ebullient and actually get pleasantly terse.  

  
I don’t think these matter to my personal finances. But I am struggling to stop trying to explain why I want to do something when it doesn’t matter. If I were talking to a human developer (that I am not paying) trying to get them to do something, of COURSE I am going to explain why because they don’t want to do anything that I want them to do because I am not the boss of them. I am a supplicant. I am an interruption. I want to make the best case I can and appeal to their sense of making the world a better place.  
  
But LLMs are not like that. Sometimes it helps to give them context about what you want to do, because they will realize that they can do a little more in accomplishing that goal. Like “I want you to remove this call to middleware X and just call function Y directly because middleware X is not adding value because reasons”. And then the LLM says “I’m fixing that. Done. Oh I see that we’re doing the same thing in this other file, I’ll fix that too.” Often for little things like this it’s right.  
  
But sometimes the reasons won’t change the result. You kind of have to build up an intuition. On the other hand, it’s trivial in token cost to read two of your typed sentences instead of one, so really the only cost that matters is your effort.  
  
I guess the takeaway is that if explaining yourself to the agent reveals to it a goal you want pursued or a guideline you want followed, and if you haven’t already explicitly told the agent that, then it helps to share the reason. If the explanation doesn’t expose anything new or anything with broader impact than the current task, then the LLM doesn’t need it. And if it’s worth explaining, it’s worth writing down in context so that the agent will remember it.  
  
Another habit I have to break myself of, is letting the agent know how things turned out. I promise you that if you tell an agent “ok that worked”, it will spend a lot of tokens generating a nice summary for you. If you want the summary, go ahead, but it doesn’t change anything unless you really want it.  
  
➤ The agent and the LLM are not people, even though you “talk” to them. It’s completely ok if you want to use your normal mannerisms to talk to agents, but unnecessary. The agent will do what you want even if you are not nice. Trying to “close the loop” by telling the agent how things turned out, will waste tokens generating summaries. Only offer explanations if they reveal a goal or a guideline to the agent that you have not previously disclosed to it.  
  

## Design

It is really important to have a design in mind (not just a goal) and to work with the agent to realize the design. Giving the agent a goal is good for one-off things, like “fix this bug” and so forth - but if you want to do something complex then you need a design. The agent REALLY likes to redesign things if it doesn’t recognize your design, and will helpfully suggest refactoring all the time. If you point it at a design and stick to it, it will stop trying to create random stuff.  

  
You can collaborate with the AI in chat to make the design, but you should be skeptical of everything it comes up with and try to poke holes in it.  
  
You MUST write the design down in a file that you can keep pointing the AI to. When you iterate on the design, update the design file (or have the agent do it).  
  
I suggest keeping separate design documents for every significant feature that you have, so that you don’t have to have the agent read the entire design of the entire application every time you want to make a change. This is just a way to save tokens (which equates to money).  
  
Here are links to two design docs for my feature and [collaboration](https://github.com/ericfitz/tmi-ux/blob/main/context/COLLABORATIVE_EDITING.md) features, and as a bonus here is my prompt for implementing authorization checking. The authorization design doc is in the context directory and my standard prompt tells the agent to read relevant files. I am very pedantic about the design, even in the prompt. If you stop being pedantic, you get much more variation in quality of results.  
  
\`\`\`  
I'd like to implement two standard authorization functions.  
  
First is the core function, something like "AccessCheck(principal:string, requiredRole:string, authorizationData:?)" that would return whether or not the principal has the required role, given the provided authorizationData. AuthorizationData might just be a small JSON that has the owner field and authorization array from the object. Principal in our case would be the user field, e.g. the email address of the user. By abstracting userName as "principal" and the specific JSON in our objects as "authorizationData", we make it easier to adapt to a new authorization scheme in the future if we choose to do so, and we encapsulate all the business logic for authorization into this function.  
  
Next is a utility function, something like "CheckResourceAccess (userName, resource, requiredRole)”. This is a wrapper around the AccessCheck() function, and is what will be used in most other locations in the code. CheckResourceAccess looks up the resource, extracts the authorization data (user field and authorization array field) and marshals it to AccessCheck(), e.g. AccessCheck(userName, requiredRole, authorizationData). CheckResourceAccess can support Diagrams by looking up the parent threat model and getting the authorization data from that object. In this way there is a clear separation of authorization logic from object parsing to extract authorization data.  
  
Please recommend any improvements you have for this approach, identify everywhere we can use these functions, and come up with a plan for implementation of both the functions and the refactoring to use them, and present the plan to me for review.  
\`\`\`  
  
Note that even though I went back in my prompt and renamed the isAuthorized function to AccessCheck and then forgot to update all references, it still figured it out. BTW the code generated was correct on the first try and I haven’t had to fix any bugs in it.  
  
The more detailed and specific the design is, the more the final code will be like your vision.  
  
The more detailed and formal the design is, the better the result will be. Since my project has a REST API server and a web application client, I designed the protocol and object model first using an OpenAPI specification, and stored the machine-readable specification file in both the client and server projects. I cheated and auto-generated the API template code, but now the client and the server have a single source of truth, extremely detailed, with examples of success and failure cases. As I added features I used the agent to add, remove, and reorganize the API schema, but each time I had the server agent go back and fix up the server code and the client agent go fix up the client code, according to the latest specification, and I was shocked how easy it was to get the client and the server successfully communicating. Some stuff worked on the first try but it only took me a couple of hours until everything was working, even though I had developed the client and the server separately.  
  
➤ Be intentional with design. Document design. Nitpick agent-proposed designs. Make design docs available to the agent as context. Keep design docs up to date. Be pedantic. Use standards-based machine-readable design document formats (e.g. OpenAPI specifications or XML schemas or JSON schemas…) if possible in your problem domain.  
  
➤ Save tokens (==$$$) by using small design documents for particular feature areas rather than large monolithic documents. Store them all in the same folder, list them and describe their contents in a readme file, and in your standing instruction to the agent, tell it about the directory, tell it to read the readme file, and tell it to read any of the other files relevant to the current task.  
  

## Planning

Whenever you’re going to do something complicated, don’t just tell the agent to do it. Always tell the agent to “think deeply” and present a detailed plan of how to accomplish it. Specifically use the words “think deeply” or “analyze deeply”- to agents, they are a magic incantation (for realz). These phrases cause the LLM to change from instant mode to deep reasoning mode or whatever your LLM provider calls their equivalent feature.

  
Some agents will immediately switch into execution mode after generating a plan, so I usually squash that in my prompts. It is very important to review the agent’s plan, poke holes in it and refine it. Looking at the plan can help you recognize that you failed to cover something. Here’s an example of me telling the agent to make a plan for fixing a bug:

  
\`\`\`  
Authentication is still not working. I want you to analyze deeply and add any diagnostic logging that you need. Step back and come up with a diagnosis, a way to confirm the diagnosis, and a plan to fix. Don’t make any changes, just present the plan and wait for my approval.  
\`\`\`  
  
As a side note, occasionally you will see agents get into loops, especially when trying to fix a complex problem. These “loops” look like going back and forth between two or three approaches, appearing to forget that they already tried that. I’ve found that deep thought mode often will break the looping behavior (in fact the example above is precisely a response to such a loop).  
  
➤ “Think deeply” or “analyze deeply” are hints to the agent to enter deep thought mode, useful for planning and avoiding loops.  
  
For really sophisticated features I will use this approach and have it write a [planning](https://github.com/ericfitz/tmi-ux/blob/main/context/DFD_INTEGRATION_TESTING_APPROACH.md) and [tracking](https://github.com/ericfitz/tmi-ux/blob/main/context/DFD_GRAPH_INTERACTION.md) document (and put it in context/, of course). Note that in that tracking document I painstakingly described all the specific interactions that I wanted and a governing principle, and then I had the agent update the doc as we completed each feature.  
  
You can “collaborate” with the agent on these documents - I might bang out a bullet list and save it, and then tell the AI agent to form a plan around that, and then go back and forth to fine-tune the design, and then have the agent “update” my original “document” with the full plan, and use it for tracking implementation progress.  
  
➤ Write a short document describing what you want, and “collaborate” with the agent to flesh it out into a plan and update it into a plan and tracking document.  
  
➤ Make a plan for anything nontrivial, and make the agent write the plan to a file. Iterate on the plan with the agent until you think you’ve eliminated ambiguity and planned for likely edge cases. Make the agent write the plan down and save it as context.  
  

## Inter-agent communication

When I started integrating my client and my server and had to get them both aligned on the protocol and usage, I had the crazy idea of making them talk to each other (through me, of course).  

  
So I fired up Claude Code #1 focused on the local clone of the server repo, and Claude Code #2 focused on the local clone of the client repo, and as I encountered integration problems, I would type in prompts like the following (these are real):  
  
*To the server Claude:  
*  
\`\`\`  
can you write a short doc for my client developer to describe how to implement TMI-server integrated OAuth login using our API- from using the /auth/providers endpoint to discover the providers and drive the UI, to the OAuth flow and how the client should participate at each step, to how the client should handle common errors or situations like expired tokens?  
\`\`\`  
  
*To the client Claude: <uploaded [CLIENT\_OAUTH\_INTEGRATION.md](https://github.com/ericfitz/tmi-ux/blob/main/context/CLIENT_OAUTH_INTEGRATION.md) >*  
  
*To the server Claude:*  
  
\` I’m getting some errors in the client javascript console, help me diagnose and suggest what I should do to fix it: <paste log> \`  
  
*To the client Claude: <pasting output from server agent>*  
  
\`\`\`  
I'm getting some errors. I shared them with the server developer and he looked at the logs and here's what he recommended:  
  
Update JWT Interceptor to Skip Public Endpoints  
  
#1: Your JWT interceptor should skip adding auth headers for public endpoints. Based on our TMI server configuration, these endpoints should be public:  
  
\- / (root/health check)  
\- /version  
\- /auth/login  
\- /auth/callback  
\- /auth/providers  
\- /auth/token  
\- /auth/refresh  
\- /auth/authorize/\*  
\- /auth/exchange/\*  
  
#2: Fix the Auth Service Token Check  
  
The auth service should handle the "no token available" case more gracefully for public endpoints.  
\`\`\`  
  
I know that I’m unnecessarily anthropomorphizing, but it seems natural and was a very effective pattern, evidently agents like to feel helpful.  
  
➤ When you’re trying to get two pieces of code to interoperate, start two agents, and have the agents “talk” to each other - with you as the messenger - to resolve problems.  
  

## Get really good at logging

For the agent to see what your program is doing when you’re debugging, you need to emit really good logs.  

  
One of the first classes I had the agent write for my project, was the logger class, and I gave it guidelines (“we’ll use 4 levels, debug, error, warning, info, we’ll begin each log line with an RFC3339/ISO8601 formatted timestamp, and for debug logs, we’ll put the name of the components before the message, like \[ApiService\], and have configuration that will allow us to only enable debug logging for specific components”).  
  
Every time that I have to debug a problem, I remind the agent to add more debug logging. I rarely remove debug logging, and only if it’s noisy and I think it’s not likely to be useful again. When I am trying to debug a problem, I tell the agent to add whatever diagnostic logging it needs to diagnose the problem.  
  
\`\`\`  
As you debug this, consider how we might modify the service to make the problem more debuggable. For instance, we might choose to add more information to error messages returned in API responses. Or we might choose to add more debug logging. If you find specific instrumentation helpful, suggest it as a permanent change to our service when not running in production and/or with debug level logging. Keep going.  
\`\`\`  
I will blog about logging another time rather than give a thousand tips here. But my big tips are to log:  
  
When a complex operation starts or finishes. This will allow the agent to see if things completed or not, or happened out of the expected order.  
  
When a significant state changes, or when a variable used to track a state changes (include the old and new values). This will help the agent to decide what code path to diagnose.  
  
When a data structure or message is received (log what was received) or sent (log what was sent) - this includes API requests and responses. This will allow the agent to see if what was sent or received was not in the expected form.  
  
Log redundantly at every layer - if you’re implementing an API, log at your handler, your validator, every middleware that you’re using, etc. There will be a lot of redundancy but the agent will be able to look at your logs and see the flow of data through your program, and if a layer is misbehaving or isn’t being invoked as expected.  
  
When you change part of an object, log the entire object if possible, including the change. This will allow the agent to diagnose errors related to object manipulation.  
  
Always put relevant values in your logs. Never log “Modified Object”. Always add detail: “Changed attribute <A> of object <O>. New value: { … }”. Remember the agent cannot see the screen and it can’t intercept the packets or insert a breakpoint and watch a variable; the only way it knows what’s going on is if you can give it the logs that record what’s going on.  
  
Add as much debug information as you can to responses, esp. API responses. This enables scenarios like the agent working on your client being able to understand why the server didn’t respond as expected. Security note: make sure that this is turned off in production builds.

  
➤ Log. A lot. With a lot of detail. Create ways to capture state and make it visible while the program is running so you can give it to the agent. Build logging in at the beginning, and keep reminding the agent to use it.  
  

## If you’re building a UI, you can also give log-like visibility in your UI.

  

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXc4hRw1XrIuctXGfyeuuNrqVdAAnvvs9Xgg-KJyOvBIRk3HZUCCFA3VIbvBM8usFdaKFciTep2tiKP3NElUxp_9gKUcIUbkysFh_CWYzPaRsE7ArSPi87h3gEwd827GajowrQPmKw=w640-h354?key=MQA7SFMGSvBlzQ_59OpCFQ)

➤ Make it easy in your development UX to get to the underlying state, to assist the LLM in debugging.

## Use defensive prompts

Occasionally the agent will hallucinate, but that hasn’t been a huge problem for me. Agent hallucinations when writing code tend to be inventing method/function names or guessing at parameters and order. I catch these very quickly because my standing instructions include the following:  

  
\`\`\`  
\- When making changes to any file:  
\- Always run lint with "pnpm run lint:all" and fix any lint errors or warnings related to changes you made  
\- When fixing lint issues about unused items, remove the unused item rather than prefixing with an underscore, unless the item is commented as a placeholder for future functionality  
\- In addition, when making a change to any file containing executable code:  
\- Run a build with "pnpm run build" and fix any build errors  
\- Run the related tests with the vitest CLI and fix any test errors related to the change  
\- Never complete a task if there are any remaining build errors  
\- If the file was a test file, run the test using the proper vitest CLI syntax and fix any test errors.  
\`\`\`  
  
➤ In your standing instruction to the agent, tell it that it’s not done with the task until lint-build-test all complete without errors.  
  

## Agents are lazy and cheat when you tell them to fix things

One of the weird things I found out about agents is that they actually give up on fixing test failures and just disable tests. They’ll try once or twice and then give up. They might use test-specific disablement features or they might just comment out the test.  

  
My completely uninformed guess is that something in the agent’s system prompt is telling it not to rathole and get back to the main task.  
  
But whatever the cause, I always update my standing instructions to tell the agent to never disable tests, and because they still occasionally did anyway, I now put that instruction in comments in all my test files (see above “Good context is where you find it”).  
  
➤ In your standing instructions to your agent, give it an instruction like “never disable or skip a failing test, always diagnose the failure to root cause and fix the test or the underlying code”.  
  

## Use git defensively

Agents struggle with complex changes to files. It turns out that telling an agent how to make precise changes to a very syntax-sensitive file is a hard problem, precisely as hard as source code management, which essentially is the same problem, only a human proposed the change instead of an LLM.  

  
One of the reasons I like Claude Code is that it is much better at modifying files successfully than other agents. Other agents will give up on complex file changes after an error or two and just rewrite the entire file - effective, but slow and wasteful of tokens.  
  
Agents will frequently make small syntax errors like leaving a comma after the last item in a list in a JSON file, or forgetting a closing brace, or forgetting a semicolon in a typescript file. My strategy from the last section - a prompt that tells the agent to always lint-build-test before completing a task - causes the agent to catch and fix most of these problems without me having to intervene.  
  
But there are two kinds of errors that agents make that are more severe. Occasionally an agent will completely mangle a file by botching a change- this happens when it gets the “here’s where the change starts” and “here’s where the change ends” markers wrong.  
  
In that case, you want to rewind to where you were before the change. Some agents like Roo Code have checkpointing built in and you can just scroll up and click the “restore to checkpoint” button. But there’s a strategy that works with all agents - make sure that there are no uncommitted changes before you begin your change, and then if something goes sideways, you can use git clean and or git restore (or just click the handy “undo” button next to the file in VS Code’s Source Control tab) and all you’ve lost are some tokens.  
  
This might all sound like git best practices, but I see a few differences from how I use git without agents (and maybe I was just doing it wrong):  
  
I start making small checkins much earlier when creating new code with an agent  
  
I make much more frequent checkins when modifying code with an agent  
  
The agent tends to modify more files at a time than I would manually, because it’s much more practical to do code-base-wide changes  
  
➤ Always start a change with no tracked or staged changes in git, and use git clean and git restore as an “undo” feature.  
  
Here’s an obvious one, but if you’re going to make a big change (let’s change test frameworks, or let’s refactor this component), create a new branch and have the agent make the change there. You don’t even need to know any git syntax, you can just write it in the prompt; all agents speak git:  
  
\`\`\`  
I want to change the test infrastructure from jest to vitest. I want you to add any necessary packages, convert all of our existing tests to vitest (use vitest syntax, not jest or jasmine syntax), and run all the tests to make sure they pass. Don’t disable any tests or test cases, figure out why the test is failing and fix it. Make a new branch “feature/test-refactor” and switch to that branch to make these changes.  
\`\`\`  
  
➤ Just like when you’re actually writing code, if you’re going to make a big change or try an experiment, make a new branch.  
  
The downside of all agents speaking git is that all agents speak git, and if your agent feels particularly motivated it will go ahead and check in its work without asking first or letting you review.  
  
You have to be very careful of what tools you allow the agent to run without stopping to ask permission. I let my agents run npm/pnpm scripts, ls, find, grep, etc. - but I don’t let them rm and I don’t let them cd out of the project directory and I never ever let them use git without stopping to ask. The best case is they will litter your change log with agent-generated change messages, but the worst case is they will mess up your ability to undo.  
  
➤ Never ever let agents use git without stopping and asking you first.  
  

## Break down big tasks into lists of small tasks, and use TODO lists to plan and track progress

If you can, break big tasks into small tasks. I like to break down tasks like this:  

  
For UX, I like to create the UX object as one task, with a specific instruction to make it not do anything. Then I like to “hook up” the UX to the data or logic in the code.  
  
For APIs, I like to create the API specification, then the framework (routes and empty placeholder handlers).  
  
For databases, I like to plan and fine-tune the schema, document it, and then implement the individual structures (tables and so forth).  
  
For business logic, I like to write down the business logic in plain English in a file, and then I like to create the minimal functions to hold the business logic and possibly a few utility functions, and then I like to just reinforce the agent to use the business logic function if I give it another task that needs to be business logic aware. You can see this in my access checking example, above.  
  
This forces you to think about architecture ahead of implementation (one of the reasons I hate the term “vibe coding”), but it also addresses one of the AI weaknesses I discussed above- context size. If the agent has to do a lot of work all in one session, the context will build up. Then you are at increased risk of the agent losing focus or going off on a side quest. So we keep work in manageable batches.  
  
How do we keep track of all the work to be done? TODO lists of course. Agents love to create TODO lists. I make the agent write down the TODO list and update it as we implement things. This makes it easy to end a session and start a new one without a bunch of pre-existing context for finished work. It effectively is a long-term memory for a big task; you can shut down the agent, go away for the night or a week, come back, and the TODO list will have everything the agent needs to continue the work.  
  
\`\`\`  
I want you to write down a to-do list of the endpoints that need handlers.  
\`\`\`  
  
Prioritize your TODO lists. The agent will usually take a guess and recommend prioritization and I often go with that, but sometimes I want to adjust priorities.  
  
\`\`\`  
I'd like to update the to-do list with priority values for each unimplemented endpoint handler, and remove the prioritization of core business logic vs. metadata vs. batch. Here are the rules:  
  
Priority 1: GET and PUT and POST and DELETE for individual sub-entities other than metadata. This does not include bulk operations.  
Priority 1: GET for lists of metadata  
Priority 2: GET and PUT and POST and DELETE for individual metadata items. This does not include bulk operations.  
Priority 3: PATCH for cells and threats  
Priority 4: PUT and POST bulk operations (endpoint contains "bulk")  
Priority 5: Anything else  
\`\`\`  
  
Do the actual work in batches. Have the agent update the TODO list as you go. If you find that the agent has a particular challenge or tends to overlook some detail, you can put instructions for that in the TODO list (if there are a lot of batches) or in your prompts for each batch of work, e.g. the “pay special attention to…” instruction in this prompt.  
  
\`\`\`  
Please read UNIMPLEMENTED\_ENDPOINTS\_TODO.md and continue implementation of the priority 2 items. Pay special attention to parameter matching between the routes and the handlers. Update the todo file as you implement the handlers.  
\`\`\`  
  
Occasionally, the agent will forget to update the TODO list with progress. You’ll stop for the night and come back the next morning, look at the TODO list, and say “I thought we implemented X”. That’s OK, have the agent fix it.  
  
\`\`\`  
Please read UNIMPLEMENTED\_ENDPOINTS\_TODO.md and see if there is any work that is not marked complete, but that is already done in the code. Mark such tasks as complete in the file.  
\`\`\`  
  
➤ Break big tasks into small tasks. Make the agent write TODO lists and keep them updated with progress.  
  

## Watch what the agent is doing and interrupt it with corrections

While the agent is working, you’ll see what it’s doing/thinking about in the chat window. Unless your whole approach to life is “YOLO”, you should watch the chat window, at least for the first batch of work that will be repeated many times. Sometimes you’ll be watching the chat window and realize “you know, I wasn’t pedantic enough about exactly what I wanted” and sometimes you’ll see that the agent has chosen a solution that might work but isn’t really what you would prefer. You can interrupt the agent - usually by pressing “escape” - and give it more instructions. I frequently interrupt the agent and give it very detailed instructions about guidelines, limitations, or expected behavior that I want to result from whatever it’s doing. I always follow this with “keep going” to tell it to continue with the current task. Example (I was trying to fix a “save” bug, but I got worried that the agent was going to make the dialog all reactive and do a crap ton of server calls every time the user typed a character). When I saw it was trying to do things I didn’t like, I stopped it and gave it a corrective prompt. Note that I focused on desired behavior more than implementation, because honestly the agent probably knows more about patterns and practices for the language and framework than I do.  

\`\`\`  
I expect the threat to be created and saved when the user clicks the save button in the add threat dialog. I expect no threat created and no properties of an existing threat to be changed if the user clicks "cancel" in the add threat dialog. If the threat editor dialog is opened against an existing threat, I expect no changes to be saved until and unless the user clicks the "save" button. Keep going.  
\`\`\`  
  
➤ Watch what the agent is doing and stop and correct it immediately if it starts doing something you don’t like.  
  

## Make the agent write good tests

A lot of developers online talk about using agents to write boilerplate and tests. This is a very seductive proposition; it’s the scut work of development. So it’s really tempting (guilty) to tell the agent “write unit tests for module foo”.  

  
First, agents can think of really good test cases and really useless ones; go back and prune the test cases and tell it to add new ones for scenarios you really care about but that it didn’t think of.  
  
But along the way I discovered my #1 concern about using agents to build software: agent-created tests almost NEVER catch bugs. I don’t know exactly why this is, but my intuition is that the main cause for this is likely the way agents create software (including tests): they iterate until the test passes. If the original function isn’t working as expected, I suspect that the agent-created test will test the functionality as it exists, not as was intended, regardless of what it calls the test case. A side issue here are that agents are lazy and will disable or suppress test cases if you don’t keep reminding them not to do that (discussed earlier)  
  
Maybe I just am not experienced enough writing tests, and so I am not a good judge of whether a test implementation is good. Or maybe I’m not paying enough attention to the test definitions.  
  
My learning here is that whenever you find a bug and it wasn’t discovered by a test, specifically ask the agent why not, and make it debug the test.  
  
➤ Review agent-created test cases, add ones for scenarios important to you, and remove useless ones. Whenever there's a bug that a test did not discover, ask the agent why the test didn’t discover the bug, and make it fix the test.  
  

## Make the agent write a lot of custom tools

Agents are designed to invoke “tools”. A typical coding agent will have tools like read a file, write a file, edit or multi-edit a file, run a command in a bash terminal, search the web, etc. The ability to run an executable in a terminal means that you’re practically unlimited in the tools you can build. And you can use the agent’s context file to tell the agent about the tool.  

  
Whenever I see the agent start to struggle with the mechanics of executing a task, I look for an opportunity to write a tool. I was having problems with the agent making changes to a very large json file; the file was too large for context so the file read tool would fail, then it would try different strategies to grep to fine the line(s) it was interested in, then it would try to dump a few lines at a time, then it would realize it read the wrong section and have to do it again. And editing large complex files like that is even worse- you have all the location and file read problems, but then you have to surgically alter it while leaving it syntactically correct. I had the agent write a Python tool that targeted an element in the json file and replaced it with another element. I added a Make target for the tool, told the agent about the tool in its context file, and stopped struggling with that problem.  
  
Likewise I’ve had the agent build all sorts of script-like tools to validate complex files, and to do specialized editing and diffing (are all the keys in my en-US localization file, also present in each other locale?).  
  
One note: maybe do a web search before you have the agent create a tool; I recently accidentally recreated an API testing tool that already existed.  
  
➤ If the agent struggles with a task, help it build a tool to do the task, and teach it to use your tool to perform the task.  
  

## Other stuff I’ve learned

Agents are sycophantic. I had a whole section on this but took it out; it’s so common it’s a meme now. My hot take: it’s engagement farming for LLMs- gives you that hit of dopamine to keep you coming back.  

  
Agents like to repeat code and will happily repeat 20 lines of code 100 times if you let them. If you see this, give them really precise instructions on refactoring (e.g. centralizing mocks instead of repeating the logger mock in every test file).  
  
Never ask the agent for its opinion on your design. True story- at the end of a long session, I asked Claude how my design was. It was effusive in its praise, pointed out all the things we had done for modularity, separation of concerns, etc. Then I exited Claude and restarted, and asked the exact same question, only this time it had no context. It told me that the design needed a lot of work, complained about the stuff it had just praised, etc.  
  
You can ask the agent for advice on ways to improve your application, but be really careful; it loves to “improve” things, and is quick to suggest adding abstraction layers, etc. Every single idea it gives you will seem valid, and most of them will seem like things that you should really consider doing. RESIST THE URGE, unless there’s something that really jumps out at you as fixing a problem that you’re already encountering. In general, it’s better to ask very specific questions like “why are there calls to the low-level function in this function but also in this other abstract function on a higher layer?”  
  

## Stuff I tried that didn’t work well

***Code → Spec → Translated Code  
***

  
I experimented a bit with getting the agent to write as-built specifications and then have the agent (or another agent) use the specifications to write the app in another language. I had it write a Python application, then write a spec for it, then re-write the application in Go. The Python application worked great. The Go app was a mess but I got it working, it was nowhere near turnkey.  
  
The big takeaway is that the agent really sucks at writing specifications, at least with the level of effort I was willing to put in. I believe if the specification had been better, the translated application would have been better.  
  
My particular test workflow wasn’t the best because, as mentioned above, all the agents are really good at Python. Sonnet is not nearly as good at Go as it is at Python. So I spent a lot of effort coaxing the agent through debugging the Go app. But I tried it in Grok 3 and o3 and had similar experiences.