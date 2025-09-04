---
title: "How Does Graph Theory Shape Our World?"
source: "https://www.quantamagazine.org/how-does-graph-theory-shape-our-world-20250626/"
author:
  - "[[Janna Levin]]"
published: 2025-06-26
created: 2025-08-30
description: "Maria Chudnovsky reflects on her journey in graph theory, her groundbreaking solution to the long-standing perfect graph problem, and the unexpected ways this abstract field intersects with everyday life."
tags:
  - "clippings"
---
![A diagram of an eye](https://www.quantamagazine.org/wp-content/uploads/2025/06/JOW-S4-Ep8-MARIA-CHUDNOVSKY-Lede-LOGO-scaled.webp)

Peter Greenwood for Quanta Magazine

Born in the 18th century when Leonhard Euler solved the puzzle of the seven bridges of Königsberg, graph theory has become a foundational tool in mathematics. It studies relationships through nodes (vertices) and the links (edges) that connect them, transforming the complexity of systems — from friendship networks to airline routes — into elegant abstractions that reveal underlying structure and interaction.

[Maria Chudnovsky](https://web.math.princeton.edu/~mchudnov/) from Princeton University is a leading mathematician in the field. In this episode of *The Joy of Why*, Chudnovsky talks with co-host Janna Levin about how she got into graph theory, solved the decades-old perfect graph problem, and used it to plan her wedding seating chart. Chudnovsky also reflects on her appearance in commercials as a “superstar mathematician,” and how her background primed her for a discipline that transcends language, culture and time.

Listen on [Apple Podcasts](https://podcasts.apple.com/us/podcast/the-joy-of-why/id1608948873), [Spotify](https://open.spotify.com/show/2FoxHraQSKwxV2HgUfwLMp), [TuneIn](https://tunein.com/podcasts/Science-Podcasts/The-Joy-of-Why-p1653040/) or your favorite podcasting app, or you can .

## Transcript

**JANNA LEVIN:** I’m Janna Levin

**STEVE STROGATZ:** And I’m Steve Strogatz.

**LEVIN:** And this is *The Joy of Why*, a podcast from *Quanta Magazine* exploring some of the biggest unanswered questions in math and science today.

**LEVIN:** Steve, hi.

**STROGATZ:** Hi there. How are you doing, Janna?

**LEVIN:** Good. It’s good to see you again.

**STROGATZ:** Yeah, great to see you.

**LEVIN:** I have a math problem for you.

**STROGATZ:** Oh, love it.

**LEVIN:** So, imagine you’re visiting a city, and it has a river, maybe let’s say. Maybe it’s an island like Manhattan, and there’s little islands like Randall’s Island or Roosevelt Island, and they’re connected by bridges. And you’re a tourist, you want to cross every bridge, but you don’t want to overexert yourself. So, you’re going to try to cross each bridge once.

**STROGATZ:** Mmmmm.

**LEVIN:** Have you heard of this before as a mathematical problem?

**STROGATZ:** You know, I have.

**LEVIN:** Yeah, seed planted.

**STROGATZ:** Yeah. Yeah. No, it’s a classic problem sometime in the 1700s. Leonhard Euler was asked this question. You know, a funny thing about it that I only recently learned is that when the mayor of that town, Königsberg, asked him to think about this question, Euler complained, what are you asking me for? This is not a math problem.

**LEVIN:** Right.

**STROGATZ:** Isn’t that interesting? To him, this was not math at the time.

**LEVIN:** Yeah, that’s really interesting.

**STROGATZ:** He founded a new branch of math in thinking about it.

**LEVIN:** Right

**STROGATZ:** But he didn’t see it as math at the time.

**LEVIN:** So how did he get interested enough to mathematize the problem, which is really what we’re doing a lot of the times?

**STROGATZ:** I think it’s just that Euler felt that it was a curious question worth thinking about, just because it involved, as he put it, reasoning.

**LEVIN:** Mmmmm, a puzzle.

**STROGATZ:** It was a puzzle, yeah.

**LEVIN:** Yeah, now Königsberg is now the Russian city of Kaliningrad, if I’ve got that right. So, can a visitor there figure out how to go across? There’s a river, there’s a mainland, there’s two islands and seven bridges.

**STROGATZ:** Yeah, that’s right. And in that old problem, the townspeople used to go out on Sundays and take strolls, and it was an amusement to see if they could walk across each bridge exactly once. And no one could ever do it, but nobody could prove it was impossible. Until Euler, who did prove it was impossible.

**LEVIN:** And so how does he turn this into a math problem?

**STROGATZ:** Well, if you look at his original paper, what he does is use letters. Capital letters for the land masses and lowercase letters for the bridges.

**LEVIN:** Hmmmm.

**STROGATZ:** And then he plays around with the combinations of these uppercase and lowercase letters that would correspond to admissible walks.

**LEVIN:** Oh, how interesting.

**STROGATZ:** Nowadays, we would use dots and lines. So, and of course he found that he couldn’t do it because some of the land masses had an odd number of bridges touching them.

**LEVIN:** So, once he solves that problem, he realizes, oh, immediately he can say, if this problem crops up again, you need an even number of bridges. So, he’s already…

**STROGATZ:** He’s already generalizing.

**LEVIN:** … making headway towards generalizing. And so, you said it invented a whole new branch of mathematics, and what’s that branch?

**STROGATZ:** Well, we call it graph theory, or if we’re in England, we would say “ *GRAHF* theory.”

**LEVIN:** Well, here we were talking to Maria Chudnovsky, who’s a really interesting mathematician at Princeton. She works primarily on graph theory and managed to solve a very interesting, outstanding problem, it was nearly 50 years old, about perfect graphs.

**STROGATZ:** Hmm, that’s a term I haven’t heard before.

**LEVIN:** I’ll let her sort of tell the story, but it’s really about color coding and visualizing and nodes and dots and connectors. So, let’s hear from Maria. You want to eavesdrop a little bit?

**STROGATZ:** I’m all ears.

**LEVIN:** Great. Here’s Maria Chudnovsky from Princeton talking about graph theory.

\[*Music plays*\]

**LEVIN:** Maria, welcome to the show. It’s so nice to have you on.

**CHUDNOVSKY:** Thank you.

**LEVIN:** I wish we could be in the same studio. We realized we’re only a few blocks apart.

**CHUDNOVSKY:** Maybe next time.

**LEVIN:** Maybe next time. I actually was amused to discover that you had been in a TurboTax commercial.

**CHUDNOVSKY:** That’s right. That’s my claim to fame. I also did a mattress commercial, did you know that?

**LEVIN:** Yes, I saw you sleeping in a mattress commercial.

**CHUDNOVSKY:** Exactly, exactly. “Smart begins with better sleep.” There’s no statement I believe in more.

**LEVIN:** They’re getting free advertisement with us here. I was amused to see that they listed you underneath your name in these commercials as a “superstar mathematician.” And I wonder if you think the culture is changing in our attitude towards mathematicians?

**CHUDNOVSKY:** I think there’s a lot more understanding now of how important math is. I used to tell people I’m a mathematician, “They would say, oh, yeah, I’m terrible in math. Math is really boring.” And now they say, “Oh, wow, that’s really interesting, what do you do?”

I think, you know, with the advance of technology and the internet and, obviously our lives have changed a lot over the last 30 years or 100 years, depends how you want to think about it. And I really think math is kind of gaining popularity and gaining traction.

**LEVIN:** It really is interesting that mathematical literacy or scientific literacy is considered important, more than it used to be, at least.

**CHUDNOVSKY:** I’m so happy about that because, you know, it really it seemed to be an educated person, you need to read books, you need to know something about art, and I would never say that’s not important. But now it seems that there’s another component to it. And, you know, given that that’s a huge part of my life, I’m very, very happy about that.

**LEVIN:** There’s also an old idea that mathematics is the language of the universe, which might actually be attributed to Galileo. What do you make of this quote? I mean, do you see it as a universal language of sorts?

**CHUDNOVSKY:** I certainly do in many ways. Like, you don’t need to speak any particular language very well in order to be able to effectively communicate mathematics. If you have something interesting and important to say in math, you need to have some basic common language as the person you’re speaking with. But you don’t need to be, um, eloquent. You don’t need to be a great speaker. You can just write down what you have to say and say what you have to say, and it’s been communicated. There is no kind of added layer of “I need to say it in such a way that it convinces them.” If you have a proof, it convinces them. It doesn’t matter how you say it.

**LEVIN:** And it’s the same around the world.

**CHUDNOVSKY:** And it’s the same around the world. Yeah, there’s really no differences. Another thing math brings to the table is clear thinking.

That’s maybe a little less of a language thing, but the way you understand things, the way you think about things, you try to break it into pieces and see what’s important, what matters, what was incidental and coincidental and not important. If you’re used to thinking in a mathematical way that really puts you at an advantage.

**LEVIN:** It’s like a meta-language, like a way of understanding the world that transcends the grammatical structures.

**CHUDNOVSKY:** Right, there are all these studies that depending on what language you think it, you perceive the world a little differently—which I’m incredibly fond of.

**LEVIN:** That’s amazing. I was actually going to ask you about that hypothesis in linguistics that language structures your thoughts.

**CHUDNOVSKY:** So, I’m fluent in two languages and I understand three languages. And I know this about myself; things change a little bit in the way I think when I’m dealing with a different language.

**LEVIN:** Fascinating. I understand that you did have a personal experience with languages, with countries, with moving. You were born in Russia and moved to Israel as a teenager. So, this played a personal role for you, this issue of language, transcending language and using math as a medium to express yourself.

**CHUDNOVSKY:** Absolutely. I’m sure the fact that of all the subjects I could study, the one that required the least command of a language was math, had a lot to do with my choice of field of study.

As a mathematician and a scientist, if you’re used to thinking mathematically, then, you perceive the world in a certain way, which is a little bit like if you’re used to thinking in a certain human language, then you perceive the world in a certain way.

**LEVIN:** I don’t want to completely leave this idea too quickly. I wonder, how math can structure your thoughts, the particular field that you choose can structure your thoughts. You’re in a branch of math known as graph theory. Can you give us just a quick explainer of graph theory to anchor us in your subject?

**CHUDNOVSKY:** Sure. Graph theory is branch of math that studies pairwise relations. Let’s start with something in the world. Suppose you have a system that consists of objects, and some pairs of objects are in a relation, and some are not.

Like, you can have a bunch of people, and some pairs of people are friends, and some pairs of people are not friends. Or you can start with, buildings and roads between them. Or you can have a bunch of cities, and some pairs of cities have direct flights and some pairs of cities don’t have direct flights between them. So, all these things are examples of graphs where you can take objects and then say this pair is in relation, it goes together, this pair doesn’t go together.

So now, forget all these examples and just stay with the abstraction where you put a dot on your piece of paper for every object and now you put a line between two dots — we call it an edge — if these two objects were in a relation.

So now you have an abstract mathematical object, called a graph. Apparently, Euler came up with this idea in 17-something. And now instead of studying a system of people’s friendships or a system of flights or a system of roads, you can just study this abstraction of a graph. You’re no longer a social scientist or a transportation expert. Now suddenly you’re a graph theorist.

**LEVIN:** Right, you’re a mathematician. What drew you to this particular topic of graph theory? And also, do you really think you think more visually and differently because you’re so embedded in graph theory, or you think it was the other way around? You were inclined to visual thinking and that drew you to graph theory?

**CHUDNOVSKY:** I think the answer is we’ll never know. When I was applying for grad school, I knew I wanted to do discrete math because when I was in college, these were the courses that somehow were easiest to me. I felt that I understood them the best. Like when you take a class, some classes you study, you prepare for the test, you get your grade, and you’re grateful it’s done.

Some classes, they really stay with you, and you keep thinking about it. It’s kind of just the tip of the iceberg, and then you keep going deeper and deeper in your mind, and then when you show up for the test, you didn’t even need to study, because you understood it so much better than what they tried to teach you. And so, classes in discrete math were like that for me.

**LEVIN:** I personally love discrete math. I once had a friend who said, “there are different kinds of math?” Like this is a surprise to people who don’t live in this world that there are different kinds of math. Can you help our audience with the difference between, sort-of, continuous and discrete?

**CHUDNOVSKY:** Sure, right. Roughly, you can partition all of mathematics into two parts. One part is things where you can say, “this one is the next one after that one.” And then things where you can’t say that, because between every two things, there’s another one. So, I’ll give you an example, though, because of course if you didn’t know what I meant before, you don’t understand now either.

Let’s say I’m thinking about, counting numbers, natural numbers. So immediately after one comes two, immediately after two comes three. and that’s discrete. There’s no counting number between seven and eight.

Now let’s think about fractions. Between one and two, there’s one and a half. Between one and one and a half, there’s one and a quarter. Between one and one and a quarter, there’s one and an eighth. I’m not going to continue, but I think we get the gist.

The first example was a discrete example. The second example is a continuous example.

Courses in discrete math were somehow better for me. I always enjoyed them better; I understood them better. And so, when I was applying to grad school, it was clear to me that I was going to do some kind of discrete math. Then I got into Princeton, where the kind of discrete math they were doing was graph theory. And I became a graph theorist. Had I gone to a different university, I would have probably done something else, and maybe I would have been good at that, or maybe I would have had a different career.

**LEVIN:** You might not have made it into a mattress commercial.

**CHUDNOVSKY:** Exactly.

**LEVIN:** One of the aspects you mentioned, just as an aside, I think is so fascinating about the continuum between two integers is you can remove an infinite number of rationals and still have an infinite set left over. I mean, the beauty of discrete math is really mind-blowing.

On another note, I think it’s interesting for people that graph theory is a very visual subject. I often see that you’re drawing pictures on the board and making connections. You’re doing them very fast because you’re so used to it. But how strong is the visual aspect for you in your actual work? How much are you actually using a kind of visual mapping do you think?

**CHUDNOVSKY:** All the time. I only think in pictures. Eventually, I have to sit down and write it because, otherwise you miss things and you make mistakes, but all the development of ideas is visual.

**LEVIN:** And it’s quite beautiful to watch. Now, a lot of people also wonder what mathematicians are doing all the time.

**CHUDNOVSKY:** Doodling.

**LEVIN:** You know, what’s at stake for the mathematician? Why are these problems important? There’s this sort of tension between the very abstract mathematics, which I believe you very much love, and real-world application, but what is that balance like for you? What’s really at stake for you as a mathematician?

**CHUDNOVSKY:** I mean, I do abstract math. I’d be very happy if somebody someday finds applications for what I do. You know, sometimes if people come to me and they have a question I can help them with, and it has something to do with the world, that’s exciting. That’s fun. I like it. But my world is completely abstract.

**LEVIN:** Do you ever have to use graph theory to solve your own real-world problems?

**CHUDNOVSKY:** So, when I was getting married to my husband, we had to design a seating chart. And we were nervous about it. And I said to him, let me try to do it. You can’t be too picky about it. But I took our list of guests, which, by the way, the vast majority of guests at our wedding were people I didn’t really know from my husband’s side, I only knew kind of some stories about them.

But it’s a graph theory problem. What you do is, you make a graph where the vertices, the dots are the people. And now you put an edge between two vertices, if these two people are such enemies that you can’t put them at the same table.

And now what you need to do is take your graph and partition its vertices into subsets so that in each subset, you don’t have two people assigned to the same table that can’t sit together. You don’t have two vertices joined by an edge. And, if there are a lot of edges in your graph, that’s a hard problem. But if there are few edges in your graph, namely most of your friends and family get along, then it’s actually easy. You can use something called the ‘greedy algorithm’ and it just works.

You know, our friends and family are reasonable people. There are not so many edges in this graph. So, I took this list and a few minutes later I had—it’s called the coloring of the graph—a seating arrangement, tables of 10 to 12. And it was basically completely acceptable. My husband was very surprised by that.

**LEVIN:** Your wedding went without incident, I assume?

**CHUDNOVSKY:** No. No, no incidents.

**LEVIN:** Now, you’ve just been describing graph coloring, right. You’re color coding. This is the group and here’s a different group. As soon as you get to a point where, “Oh, this person can’t sit next to this person,” you need to assign a new color. Now this, graph coloring, is this a very old human problem?

**CHUDNOVSKY:** It absolutely is. There is probably the most famous problem in graph theory, the Four Color Theorem, which was actually posed by a cartographer 200 years ago. And what he posed is that for any map on earth, you can color in such a way that two countries that share a border get different colors, right? So, you can do that by using at most four colors. No matter how the world is partitioned into countries you can color it with four colors in such a way that countries that share borders get different colors.

**LEVIN:** It’s not obvious.

**CHUDNOVSKY:** It is very, very far from obvious. It inspired a lot of mathematical research for dozens of years. It’s very far from being trivial.

But let me just say a few things. One is when you say two countries share a border, they really need to share, a little interval of a border. Sharing just one point doesn’t count.

Thing two, this is only true if the countries are connected. If you have country with islands, that’s false.

And the third thing is, you know, I said every map on Earth, I amuse myself with that. That’s not just an expression. If your map is not on Earth, if your map is on a planet that has high genus, like a donut or a pretzel, then it’s not true.

**LEVIN:** Mmmmm. So, if it’s multiply connected in some way.

**CHUDNOVSKY:** Right, not simply connected.

**LEVIN:** So how fascinating. So, there is right there a real-world application, which is trying to understand maps and borders. Maps in the 19th century were very important in terms of beginning to understand and think spatially. You’ve had a very big impact in an area that describes perfect graphs. Can you explain to me what makes a graph perfect in terms of coloring?

**CHUDNOVSKY:** I’m so glad we started this by talking about graph coloring, because this sets the stage perfectly for talking about perfect graphs. So, you have a graph. It has vertices and edges. And now you would like to color it. So, you want to partition the vertices into sets so that there’s no edge inside a set, right? Another way to say it is you color the vertices with different colors. And the rule is vertices of the same color are not joined by an edge. If two vertices are joined by an edge, they get different colors.

Okay, so far, so good. But here is a coloring. Color every vertex with a different color. That is not a very interesting concept. To make it a little less abstract, imagine you know, you have to pay per color and you don’t want to buy more paints than you need. Okay, so now the question becomes: If I give you a graph, how many colors do you need in order to be able to color it? That’s called the chromatic number of a graph.

First of all, algorithmically it’s very hard. If I give you a graph and ask you how many colors do you need? What’s the smallest number of colors with which you can color this graph? You in general can’t give an answer in a reasonable amount of time.

Okay, but another thing is maybe I can look at a graph and start connecting how many colors I need to add the properties of this graph. Maybe I still won’t be able to give you an answer, but here’s an obvious lower bound on the number of colors you need. If I have a graph and in it there is a hundred vertices all pairwise adjacent, I need at least a hundred colors in order to color this graph. Now, there are graphs with no three pairwise adjacent vertices that need a thousand colors, and there are graphs with no three pairwise adjacent vertices that need a million colors.

Now, on the other hand, there are graphs where that doesn’t happen. There are graphs where this obvious lower bound of how many pairwise adjacent vertices you have is actually the right answer. And these are called perfect graphs.

**LEVIN:** I get the gist of it and let me just try to help for our audience to bridge a little gap. It’s my understanding that when you have these, you’re calling them pairwise adjacent vertices, we could call those a clique.

**CHUDNOVSKY:** Yes. Clique is the right word for it.

**LEVIN:** I’m just imagining that socially people understand when you’re trying to do a wedding graph or a dinner party graph that there’s a little clique. And in that clique if that number of vertices equals the number of colors you need to use, the chromatic number, then you’re on your way to a perfect graph.

**CHUDNOVSKY:** So, a graph is perfect if its chromatic number equals to the largest size of a clique in it.

**LEVIN:** Oh, excellent. Exactly. So, the largest clique, yes. Now, in the 1960s, a French mathematician, Claude Berge, began to think more about coloring and perfect graphs. He formulated this conjecture known as a strong perfect graph conjecture. Now this has loomed large in your work. How does your work tie in with this famous conjecture, long-lasting conjecture, over 50 years?

**CHUDNOVSKY:** So, when I came to Princeton as a graduate student I came to the office of Paul Seymour. And he was working on the strong perfect graph conjecture at the time, and I knocked on his door, and I said, “Can I work on this with you?”

And I think he was a little surprised, because that’s not a question people often ask, but he didn’t know what to say, so he said yes. And then a couple of years later, four of us solved this problem. It wasn’t my first theorem, but it was the first theorem I proved as a PhD student and, you know, it was a good way to start a career.

**LEVIN:** That must have had an enormous impact — a half-century-old conjecture, many people working on this important problem. How did you approach this, you and your collaborators, so that you were able to make progress where others were stymied?

**CHUDNOVSKY:** That problem was open for 40 years at the time, and people worked on it. Berge’s conjecture was every graph with this and that structural property is perfect. And it was clear that, if and only if, a graph is perfect, then it must have those structural properties. You know, when you just say a sentence like that, you have no idea where to start, right? How would you prove that everything with those three properties have that fourth property?

But what you could try to do is try and understand what all graphs with these first three properties look like. And then take that and deduce from that the fourth property you’re actually interested in.

And because people had been thinking about this problem for 40 years, there were a lot of ideas of how this gap may be bridged. None of them were exactly correct. In the end, we had to come up with our own correct intermediate statement. But there was enough thoughts in the world that at least we knew in which direction we should start going. And then, you know, we worked really hard, we got lucky, we are smart, all kinds of things.

**LEVIN:** So, I love how that refers to a larger global collaboration, which I think relates to something we were talking about in the beginning about the transcendence of mathematical language, that this is an international collaboration, even if not in an individual paper, in the larger scheme of things.

**CHUDNOVSKY:** Very much so. I mean, I work with people from all over the world. I travel a lot. And because math is math and, truth is truth you can disagree on everything, but you will agree that the proof is correct, or you will agree that the proof is not correct, and your other opinions don’t play into it at all.

\[*Music plays*\]

**STROGATZ:** I love how she says it. Math is math and truth is truth. But it makes me wonder if this kind of training that we get prepares us ill for the real world.

**LEVIN:** Maybe you could say the real world is overrated.

**STROGATZ:** You know, that’s what some of us think in math because how many other places can you say something like that? Math is math and truth is truth. I mean, this is an oasis. It’s such a pretty place to live.

**LEVIN:** It’s such a pretty place to live. And we talk about this a lot on the show; just how transcendent the ideas are. They’re true for all of us, and that’s really special and really unusual.

**STROGATZ:** It’s also a gift that we get to talk to each other across the centuries. You know, like we mentioned Leonard Euler, and you can have in your mind, at least a conversation with someone from hundreds of years ago. There are some differences, but there’s a lot that we have in common.

**LEVIN:** Absolutely. I love that idea that we’re having a dialogue across time. I mean, not only across cultures, right?

**STROGATZ:** Right.

**LEVIN:** Not only across the globe, but we can actually go across time. I mean, this is, when we talk about sending messages out into the universe the most reasonable messages to send are ones that have to do with math.

Let’s go back to our guest. Let’s hear more from Maria right after this break.

\[*Music plays*\]

**LEVIN:**  Welcome back to *The Joy of Why*. We’ve been speaking with graph theorist Maria Chudnovsky on how she proved the strong, perfect graph theorem, something that was proposed by Claude Berge back in the 1960s.

Math can be very frustrating, and it can take a very long time. You have this enormous breakthrough, but it’s not a single moment. For you, how does this unfold, and come clear to you that you were really onto something?

**CHUDNOVSKY:** You know, you never know until you know. You really think you’re making progress, you set your next goal and you proved it, and now you think, “Okay, well, great, this was a big hurdle, now it’s a straight line from here,” and then suddenly it’s not a straight line. It’s a nerve-wracking process.

But on the plus side, there are a lot of little celebrations. Just because it’s not the last hurdle doesn’t mean it wasn’t an important one, right? Every step is a eureka moment. I think now every proof is very complex. There’s not one eureka moment. But there are a lot of victories. There are a lot of celebrations. Ingrid Daubechies in some interview once said, “the reason we do math is because we’re addicted to the high.” And it’s completely true.

**LEVIN:** That’s a t-shirt. I don’t know if this story is true or if it’s apocryphal, but I heard that Berge was read the news of the impending proof while he was in the hospital. Is that a true story?

**CHUDNOVSKY:** You know, he was in the hospital, that’s true. He was told the news in his last days when we found the proof. He was told about the proof.

**LEVIN:** It’s a nice dimension, and of course, mathematics is ultimately a human pursuit. I wanted to ask a little bit about applications that have branched off of this discovery. Are there, to your knowledge, examples in which people are using this in other fields?

**CHUDNOVSKY:** Right, so the answer is I don’t know. There is a paper about perfect garbage collection in Brooklyn.

**LEVIN:** How grateful I shall be to you if that problem is solved.

**CHUDNOVSKY:** There we go. Exactly. But it’s not me, it’s before my time.

**LEVIN:** I definitely do not need for there to be a practical application to value mathematics. And I love that we’re asking people to appreciate that the stakes are high, even for very abstract mathematics,

I know that we have sirens in the back, so there’s probably some graph theory problem for solving the route that an ambulance or cop car has to take through Manhattan.

**CHUDNOVSKY:** You know, designing optimal routes is definitely a graph theory problem, right? You have junctions and roads between them, and that’s a graph, and now you’re to find best way to navigate that graph.

**LEVIN:** So, let’s take this back to the way you approached your solution. The problem that you approached… how long, for instance, is the paper that you wrote?

**CHUDNOVSKY:** It’s about 150 pages long.

**LEVIN:** Ok, so this is very long.

**CHUDNOVSKY:** This is very long. This is hard. This has nothing to do with complexity hierarchy. This is just hard.

**LEVIN:** This is just colloquially hard.

**CHUDNOVSKY:** Right.

**LEVIN:** How did you simplify the problem? There seemed to have been a strategy where you broke the graphs into pieces in a systematic way to allow you access to this proof.

**CHUDNOVSKY:** Right, so, there is a lot of breakage going on. So, the goal was to prove if you have two properties then you’re perfect. So, what we did was we showed that if you have these two properties, then either you have some graph we can describe — or what’s called, an explicit construction — or you can break your graph apart in such a way that showing that this half is perfect and showing that this half is perfect is enough.

So that was the theorem we proved. This is a theorem with a lot of outcomes. We have five explicit constructions, three kinds of decompositions, that’s three kinds of ways to break a graph. So, what you’re proving is if properties one and two hold, then one of those eight things happen.

Now, in general, that’s a theorem that’s very hard to prove because you don’t know which way to push, right? You know, are you trying to prove that the graph behaves like this, or are you trying to prove that it behaves like that? So, what’s helpful is to break the world into pieces, where in this part of the world it’s always like this, and in this part of the world it’s always like that. And in a way, that’s the key to almost every mathematical proof. You have some huge overwhelming thing, but you’ve simplified it into a scenario where it’s always like this, and a scenario where it’s always like this, and a scenario where it’s always like that. And if you can distinguish between your scenarios, then usually that leads you to a proof.

And so that was kind of a very important insight, a very important thing to do in this proof to understand how to approach the world in this stratified way.

**LEVIN:** Hmm, it’s a strategy.

**CHUDNOVSKY:** Right, right.

**LEVIN:** So, it’s fascinating. Maria, I wonder how do you know when you’re approaching a problem, how hard it is?  Is the next problem you brave going to be a necessarily even harder one, or are the challenges unpredictable?

**CHUDNOVSKY:** I don’t think problems are linearly ordered by difficulty. I think, every problem is hard until you solve it, and then you have a solution. The reason to choose a problem is not because it’s harder than the previous problem you solved. The reason to choose a problem is because there’s a phenomenon you want to understand, and in order to understand it you need to answer this question. If the question appealing to me, it’s an aesthetical choice. You know, it’s a little bit of a practical choice if I think I have a chance of contributing. But it’s also, like, does this question interest me?

**LEVIN:** And so, what is that intuition? What drives your choices in big problems?

**CHUDNOVSKY:** I think, and this is speculation, questions that interest us are related to questions we’ve already thought about. It’s very rare that somebody, you know, comes into the room and says, “Here is a question you must be really interested in.” If I’ve never thought about it, what does it have to do with me?

So, I think there’s like some kind of world you’re building throughout your lifetime, and every next question interests you because it relates to the world you’ve built so far. But I think it’s probably only clear to you. From the outside, I think it’s a little less obvious.

**LEVIN:** I wanted to ask you one last question. And that is, what brings you joy in your research?

**CHUDNOVSKY:** Seeing order in a new place, understanding that something is actually built in a way I can describe, even though, until recently, it was just a mess. I guess, bringing order to the mess.

**LEVIN:** Beautiful. Maria, thank you so much for joining us. There’s such a depth here, I could talk to you for hours.

**CHUDNOVSKY:** Thank you very much for having me. I really enjoyed this.

\[*Music plays*\]

**STROGATZ:** I’m struck by how personal the experience of being a mathematician is, because when she says that what interests her is not necessarily how difficult a problem is, but whether it connects to things that she’s thought about before, I feel like that’s not a universal phenomenon. That’s something that some of us would use.

But I’m thinking, let’s say of John Nash, the great mathematician profiled in A Beautiful Mind, who would change fields just looking for the hardest, unsolved problem. It was a macho thing for him. I think he was interested in everything as long as it was hard.

**LEVIN:** I mean, isn’t that also the testament that it takes all kinds of personalities and ways of thinking to make an entire discipline, right? A healthy discipline.

**STROGATZ:** Exactly. And as Maria says, it’s an aesthetic choice for her. Some people are driven by aesthetics, but I think some are driven by, I want to use my craft. You know, I have this powerful technique and I’m just looking for something I can use it on.

**LEVIN:** Yeah. Do you feel that challenge and difficulty intrigues you when trying to solve something?

**STROGATZ:** No.

**LEVIN:** Interesting.

**STROGATZ:** No, I really resonated with what she said about phenomena. It really hit me that she uses the word that a scientist would use, not a mathematician. That she sees phenomena and it’s phenomena that appeal to her, and she wants to think about things that seem curious and baffling, but that are close enough that she thinks she could contribute. So, I love that view of it. That’s much closer to my own.

I mean, actually what personally drives me has always been paradox.

**LEVIN:** Oh intriguing.

**STROGATZ:** I really like it when something seems wrong, when something is off. Like that shouldn’t be the way this works. That’s a kind of question I always like.

**LEVIN:** Right, and then you can’t, you can’t not follow it.

**STROGATZ:** Yeah.

**LEVIN:** You know, I think, sometimes I like these kind of big visual problems with a lot of math, right. A lot of geometry, a lot of big spatial moves. Big brush strokes that move things around.

**STROGATZ:** I’m taken with your analogy to painting. Do you actually paint?

**LEVIN:** Oh, gosh. I mean, a long time ago, but I don’t advertise myself as a painter. But it’s true. There’s a method, right? You go up and you do big brush strokes. And then you, you do, you get a refiner eventually. You’re on your two-hair brush.

**STROGATZ:** Well, it’s really great talking to you about all this, Janna.

**LEVIN:** Yeah, great talking to you, Steve. Till next time.

**STROGATZ:** Okay, bye bye.

\[*Music plays*\]

**STROGATZ:** If you’re enjoying *The Joy of Why* and you’re not already subscribed, hit the subscribe or follow button where you’re listening. You can also leave a review for the show. It helps people find this podcast. Find articles, newsletters, videos and more at quantamagazine.org.

**LEVIN:***The Joy of Why* is a podcast from *Quanta Magazine*, an editorially independent publication supported by the Simons Foundation. Funding decisions by the Simons Foundation have no influence on the selection of topics, guests, or other editorial decisions in this podcast or in *Quanta Magazine*.

*The Joy of Why* is produced by PRX Productions. The production team is Caitlin Faulds, Livia Brock, Genevieve Sponsler and Merritt Jacob. The executive producer of PRX Productions is Jocelyn Gonzalez. Edwin Ochoa is our project manager.

From *Quanta Magazine*, Simon Frantz and Samir Patel provide editorial guidance with support from Matt Carlstrom, Samuel Velasco, Simone Barr and Michael Kanyongolo. Samir Patel is *Quanta’s* editor in chief.

Our theme music is from APM Music. The episode art is by Peter Greenwood, and our logo is by Jaki King and Kristina Armitage. Special thanks to the Columbia Journalism School and the Cornell Broadcast Studios. I’m your host, Janna Levin. If you have any questions or comments for us, please email us at quanta@simonsfoundation.org. Thanks for listening.