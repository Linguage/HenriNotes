---
title: "Which Programming Language Should I Teach First?"
source: "https://parentheticallyspeaking.org/articles/first-language-wrong-question/"
author:
published:
created: 2025-08-26
description: "Parenthetically Speaking: Articles by Shriram Krishnamurthi"
tags:
  - "clippings"
---
|  |
| --- |

“Which programming language should I teach first?" is the least productive question to ask in computer science. There’s a good reason it’s unproductive: it’s the wrong question to ask. The reason computer science’s endless “language wars” feel pointless is that they’re a symptom of this problem. Here’s why.

Curricula are never designed in isolation. All curricula, for anything, have to begin by considering the following:

- First: goals. These must obviously begin with learning objectives. However, they must go a lot farther: e.g., “students must eventually get jobs”. But even “jobs” is not some monolith: even within the same discipline, the expectations of a university that places students primarily in the small companies in its local area are completely different from those of one that intends to place students at world-class companies across the globe. (I’ve studied, worked at, visited, and helped universities at numerous points, and indeed both ends, of this spectrum. The differences are night and day.)
- Second: constraints. Constraints vary across both space (different places) and time (different years). The constraints can include: the needs of the rest of the university; whether the department is in a College of Engineering or College of Arts and Sciences; whether the department is accredited; how many majors the department offers; how many competing majors are offered by other departments on campus; and so on.
	There are also unwritten, unacknowledged, but very real constraints like how resistant to change the faculty are. And there can be even subtler constraints: I remember a well-known computer science professor arguing with me about the importance of teaching C in the first semester (she was firmly in favor). After a few rounds, she acknowledged that her main consideration was actually that students be prepared to work on her lab’s research projects, which were (then) all implemented in C. Strange as this may be, you can’t make progress until this has been articulated: until then, to use the “language wars” metaphor, you’re effectively fighting a proxy war.

Curriculum design is an optimization problem. Without stating goals, we don’t even know what we’re solving for. Without stating constraints, we don’t know what the feasible set of solutions is. Thus, until we’ve articulated both, we can’t even begin a meaningful conversation.

Programming languages are a solution-space artifact: they fall into the feasible set. You don’t start with them, you end with them, relative to everything else. So starting with the “which programming language” question is guaranteed to lead to talking at cross-purposes.

A basic problem in computing education is that we don’t even have a vocabulary for what we’re talking about. As a result, we reduce everything to a language, which is not necessary, sufficient, or even useful. As an example, for a long time, educators found curricula like [Structure and Interpretation of Computer Programs](https://en.wikipedia.org/wiki/Structure_and_Interpretation_of_Computer_Programs) (SICP) hard. (Now, they’ve just stopped talking about it.) This got translated to “Scheme is hard”, because people could only see things through the overly simplistic lens of the programming language. What they missed is that SICP and other curricula, typically coming out of functional programming, had gone well past the “rubbing two rocks to get sparks” stage to, for their time, the “igniting boosters” stage.

The other problem we have in computing edcuation is that we don’t think enough about how we can relax the constraints, future-proof the goals, widen the space of methods, etc. So we go from one blub language to another per decade: Pascal, C, C++, Java, Python… Here is my highly scientific summary of the progress we’ve consequently made in computing education:

> | Decade |  | Dominant Language |  | Dominant Data Structure |
> | --- | --- | --- | --- | --- |
> | 1970s |  | Pascal |  | arrays |
> | 1980s |  | C |  | arrays |
> | 1990s |  | C++ |  | arrays |
> | 2000–2015 |  | Java |  | ArrayList |
> | 2015–now |  | Python |  | associative arrays |

Whatever languages make easy become the default and determine a lot of other things. What languages make hard get ignored for many reasons. This is why so many of our curricula today look not that different from the curricula from the mid-1980s onward, once Pascal really consolidated itself in curricula.

A lot of people reading this are likely to be computing people who are sometimes asked to help out in schools. If you find yourself in this situation, I beg you, please watch at least until 8m30s into this talk: [Curriculum Design as an Engineering Problem](https://www.youtube.com/watch?v=5c0BvOlR5gs). You’ll get it. It’s designed for you!

To be clear, I am not a disinterested party. I’ve worked on multiple programming languages, [Racket](https://racket-lang.org/) and [Pyret](https://www.pyret.org/), and two books, [How to Design Programs](https://htdp.org/) and [A Data-Centric Introduction to Computing](https://dcic-world.org/), designed for introductory programming education. These are opinionated languages and books. To a good extent, the languages and books are co-designed, so they present unified, coherent worldview. Naturally, I encourage you to check them out! You may also find this talk interesting: [A Data-Centric Introduction to Computing](https://youtu.be/HwPM0xMdiNU?si=-yEIW6tFGEt3EjLX).