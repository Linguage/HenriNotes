---
title: "Robots can now learn to use tools—just by watching us"
source: "https://techxplore.com/news/2025-08-robots-tools.html"
author:
  - "[[Cheng Zhu]]"
published: 2025-08-23
created: 2025-08-26
description: "Despite decades of progress, most robots are still programmed for specific, repetitive tasks. They struggle with the unexpected and can't adapt to new situations without painstaking reprogramming. But what if they could learn ..."
tags:
  - "clippings"
---
---

![Robots can now learn to use tools—just by watching us](https://scx1.b-cdn.net/csz/news/800a/2025/robots-can-now-learn-t.jpg)

Credit: UIUC HCA LAB

Despite decades of progress, most robots are still programmed for specific, repetitive tasks. They struggle with the unexpected and can't adapt to new situations without painstaking reprogramming. But what if they could learn to use tools as naturally as a child does by watching videos?

I still remember the first time I saw one of our lab's robots flip an egg in a frying pan. It wasn't pre-programmed. No one was controlling it with a joystick. The robot had simply watched a video of a human doing it, and then did it itself. For someone who has spent years thinking about how to make robots more adaptable, that moment was thrilling.

Our team at the University of Illinois Urbana-Champaign, together with collaborators at Columbia University and UT Austin, has been exploring that very question. Could robots watch someone hammer a nail or scoop a meatball, and then figure out how to do it themselves, without costly sensors, motion capture suits, or hours of remote teleoperation?

That idea led us to create a new framework we call " [Tool-as-Interface](https://arxiv.org/abs/2504.04612)," currently [available](https://arxiv.org/abs/2504.04612) on the *arXiv* preprint server. The goal is straightforward: teach robots complex, dynamic tool-use skills using nothing more than ordinary videos of people doing everyday tasks. All it takes is two camera views of the action, something you could capture with a couple of smartphones.

![](https://www.youtube.com/watch?v=dkU0Pl1LFq8)

Credit: UIUC HCA LAB

Here's how it works. The process begins with those two video frames, which a vision model called MASt3R uses to reconstruct a three-dimensional model of the scene. Then, using a rendering method known as 3D Gaussian splatting—think of it as digitally painting a 3D picture of the scene—we generate additional viewpoints so the robot can "see" the task from multiple angles.

But the real magic happens when we digitally remove the human from the scene. With the help of "Grounded-SAM," our system isolates just the tool and its interaction with the environment. It is like telling the robot, "Ignore the human, and only pay attention to what the tool is doing."

This "tool-centric" perspective is the secret ingredient. It means the robot isn't trying to copy human hand motions, but is instead learning the exact trajectory and orientation of the tool itself. This allows the skill to transfer between different robots, regardless of how their arms or cameras are configured.

We tested this on five tasks: hammering a nail, scooping a meatball, flipping food in a pan, balancing a wine bottle, and even kicking a into a goal. These are not simple pick-and-place jobs; they require speed, precision, and adaptability. Compared to traditional teleoperation methods, Tool-as-Interface achieved 71% higher success rates and gathered training data 77% faster.

One of my favorite tests involved a robot scooping meatballs while a human tossed in more mid-task. The robot didn't hesitate, it just adapted. In another, it flipped a loose egg in a pan, a notoriously tricky move for teleoperated robots.

"Our approach was inspired by the way children learn, which is by watching adults," said my colleague and lead author Haonan Chen. "They don't need to operate the same tool as the person they're watching; they can practice with something similar. We wanted to know if we could mimic that ability in robots."

![](https://www.youtube.com/watch?v=cr5T14eBt0M)

Technical explanation video. Credit: UIUC HCA LAB

These results point toward something bigger than just better lab demos. By removing the need for expert operators or specialized hardware, we can imagine robots learning from smartphone videos, YouTube clips, or even crowdsourced footage.

"Despite a lot of hype around robots, they are still limited in where they can reliably operate and are generally much worse than humans at most tasks," said Professor Katie Driggs-Campbell, who leads our lab.

"We're interested in designing frameworks and algorithms that will enable robots to easily learn from people with minimal engineering effort."

Of course, there are still challenges. Right now, the system assumes the tool is rigidly fixed to the robot's gripper, which isn't always true in real life. It also sometimes struggles with 6D pose estimation errors, and synthesized camera views can lose realism if the angle shift is too extreme.

In the future, we want to make the perception system more robust, so that a could, for example, watch someone use one kind of pen and then apply that skill to pens of different shapes and sizes.

Even with these limitations, I think we're seeing a profound shift in how robots can learn, away from painstaking programming and toward natural observation. Billions of cameras are already recording how humans use tools. With the right algorithms, those videos could become training material for the next generation of adaptable, helpful robots.

This research, which was honored with the Best Paper Award at the ICRA 2025 Workshop on Foundation Models and Neural-Symbolic (NeSy) AI for Robotics, is a critical step toward unlocking that potential, transforming the vast ocean of human recorded video into a global training library for robots that can learn and adapt as naturally as a child does.

*This story is part of [Science X Dialog](https://sciencex.com/news/dialog/), where researchers can report findings from their published research articles. [Visit this page](https://sciencex.com/help/dialog/) for information about Science X Dialog and how to participate.*

**More information:**Haonan Chen et al, Tool-as-Interface: Learning Robot Policies from Human Tool Usage through Imitation Learning, *arXiv* (2025). [DOI: 10.48550/arxiv.2504.04612](https://dx.doi.org/10.48550/arxiv.2504.04612)

**Journal information:**[arXiv](https://techxplore.com/journals/arxiv/)

Cheng Zhu is second author of Tool-as-Interface: Learning Robot Policies from Human Tool Usage through Imitation Learning, UIUC BS Computer Engineering, UPenn MSE ROBO

---

---

#### Your Privacy

This site uses cookies to assist with navigation, analyse your use of our services, collect data for ads personalisation and provide content from third parties. By using our site, you acknowledge that you have read and understand our [Privacy Policy](https://sciencex.com/help/privacy/) and [Terms of Use](https://sciencex.com/help/terms/).

<video src="https://resources.infolinks.com/static/black.mp4"></video>