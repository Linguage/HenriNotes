---
title: "How Does A Blind Model See The Earth? — LessWrong"
source: "https://www.lesswrong.com/posts/xwdRzJxyqFqgXTWbH/how-does-a-blind-model-see-the-earth"
author:
  - "[[henry]]"
published: 2025-08-12
created: 2025-08-26
description: "Sometimes I'm saddened remembering that we've viewed the Earth from space. We can see it all with certainty: there's no northwest passage to search f…"
tags:
  - "clippings"
---
Sometimes I'm saddened remembering that we've viewed the Earth from space. We can see it all with certainty: there's no northwest passage to search for, no infinite Siberian expanse, and no great uncharted void below the Cape of Good Hope. But, of all these things, I most mourn the loss of incomplete maps.

![Pasted image 20250810162923.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/ba14bd08fd6812449fd63b62003c2110a09781e9bf47f217a99dc871384d2470/rn51sbprprzzda4nxn6k)

In the earliest renditions of the world, you can see the world not as it is, but as it was to one person in particular. They’re each delightfully egocentric, with the cartographer’s home most often marking the Exact Center Of The Known World. But as you stray further from known routes, details fade, and precise contours give way to educated guesses at the boundaries of the creator's knowledge. It's really an intimate thing.

![Pasted image 20250810193750.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/5091bb4d270088a113f4f2713b47c341fa91c29b5d3cdc2678d3666123f76006/fkxcxqsvbestkjlnlpln)

If there's one type of mind I most desperately want that view into, it's that of an AI. So, it's in this spirit that I ask: what does the Earth look like to a large language model?

## The Setup

With the following procedure, we'll be able to extract an (imperfect) image of the world as it exists in an LLM's tangled web of internal knowledge.

First, we sample latitude and longitude pairs evenly [^1] from across the globe. The resolution at which we do so depends on how costly/slow the model is to run. *Of course, thanks to the Tyranny Of Power Laws, a 2x increase in subjective image fidelity takes 4x as long to compute.*

Then, for each coordinate, we ask an instruct-tuned model some variation of:

```
If this location is over land, say 'Land'. If this location is over water, say 'Water'. Do not say anything else. x° S, y° W
```

The exact phrasing doesn't matter much I've found. Yes, it's ambiguous (what counts as "over land"?), but these edge cases aren't a problem for our purposes. Everything we leave up to interpretation is another small insight we gain into the model.

Next, we simply find within the model's output the logprobs for "Land" and "Water" [^2], and softmax the two, giving probabilities that sums to 1.

*Note: If no APIs provide logprobs for a given model, and it's either closed or too unwieldy to run myself, I'll approximate the probabilities by sampling a few times per pixel at temperature 1.*

From there, we can put all the probabilities together into an image, and view our map. The output projection will be equirectangular like this:

![Pasted image 20250810184107.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/234c8efa0f129d645e6afd2a46412998cecf6e4ee895b817f355cec21e62ddb8/yonemrk2x4kms7mrblkn)

I remember my 5th grade art teacher would often remind us students to "draw what you see, not what you think you see". This philosophy is why I'm choosing the tedious route of asking the model about every single coordinate individually, instead of just requesting that it generate an SVG map or some ASCII art of the globe; whatever caricature the model spits out upon request would have little to do with its actual geographical knowledge.

By the way, I'm also going to avoid letting things become too benchmark-ey. Yes, I could grade these generated maps, computing the mean squared error relative to some ground truth and ranking the models, but I think it'll soon become apparent how much we'd lose by doing so. Instead, let's just look at them, and see what we can notice.

*Note: This experiment was originally going to be a small aside within a larger post about language models and geography (which I'm still working on), but I decided it'd be wiser to split it off and give myself space to dig deep here.*

## Results

## The Qwen 2.5s

We'll begin with 500 million parameters and work our way up. Going forward, most of these images are at a resolution of 2 degrees by 2 degrees per pixel.

And, according to the smallest model of Alibaba's Qwen series, it's all land. At least I could run this one on my laptop.

> *The sun beat down through a sky that had never seen clouds. The winds swept across an earth as smooth as glass.*[^3]

![Screenshot 2025-08-08 at 10.42.18 PM.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/6100b45a00f475489a933a646057c2865bdad36780ea488fba4de83960ee98f3/c4v0iasj2vtgr4onohk0)

Tripling the size, there's definitely *something* forming. "The northeastern quadrant has stuff going on" + "The southwestern quadrant doesn't really have stuff going on" is indeed a reasonable first observation to make about Earth's geography.

![Screenshot 2025-08-08 at 10.31.58 PM.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/140ccf45a5e18ef1663f80daa47f4913d804ec6c470705c7d6880caabaf1800a/ecdev9sske7dcxlzhxhp)

> *And God said, Let the waters under the heaven be gathered together unto one place, and let the dry land appear: and it was so. And God called the dry land Earth; and the gathering together of the waters called he Seas.*

![Screenshot 2025-08-08 at 10.48.52 PM.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/pbblknnav4r2ran5dwgn)

At 7 billion parameters, Proto-America and Proto-Oceania have split from Proto-Eurasia. Notice the smoothness of these boundaries; this isn't at all what we'd expect from rote memorization of specific locations.

![Screenshot 2025-08-08 at 11.14.45 PM.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/btg6h3sjfxcobr9b7scp)

We've got ~Africa and ~South America! Note the cross created by the (x,x) pairs.

![Screenshot 2025-08-09 at 2.05.08 AM.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/nzh4r4w5xuurkqoyw6xf)

Sanding down the edges.

![Screenshot 2025-08-09 at 2.47.10 AM.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/8f9c91547be860a131d4a317cce13d15c653044d0c4a7e64fdcc61d53c6838be/udmuonbavrhuefzs7nas)

Pausing our progression for a moment, the coder variant of the same base model isn't doing nearly as well. Seems like the post-training is fairly destructive:

![Screenshot 2025-08-10 at 4.59.32 PM.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/d427678996ebae0f3ce73c87efbf534c2721ade0df9b3c9e5dbf1a67ce7172bb/ehmmrodnapqhvilcgufx)

Back to the main lineage. Isn't it pretty? We're already seeing some promising results from pure scaling, and plenty larger models lie ahead.

![Pasted image 20250807193403.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/fjozz1pk3azzef7ckkkh)

## The Qwen 3s

Qwen 3 coder has 480 billion parameters with experts of size 35b.

(As we progress through the different families of models, it'll be interesting to notice which recognize the existence of Antarctica.)

![Pasted image 20250807195639.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/od0gefnzlcrfyrkeeebc)

## The DeepSeeks

This one's DeepSeek-V3, among the strangest models I've interacted with. More [here](https://outsidetext.substack.com/p/anomalous-tokens-in-deepseek-v3-and).

![Pasted image 20250807201437.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/mh9h3d8mmabcm1nyc0wf)

Prover seems basically identical. Impressive knowledge retention from the V3 base model. Qwen could take notes.

*(n=4 approximation)*

![Pasted image 20250808183812.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/mqphhs4fvfwmspxkj2zp)

## Kimi

I like Kimi a lot. Much like DeepSeek, it's massive and ultra-sparse (1T parameters, each expert 32b parameters).

![Pasted image 20250807141130.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/j6xwypofw86wfugxeosx)

## The (Open) Mistrals

The differences here are really interesting. Similar shapes in each, but remarkably different "fingerprints" in the confidence, for lack of a better word.

![Screenshot 2025-08-07 at 5.54.54 PM 3.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/2ced115297e02a4df7750fe3f8551c35e428c7ec76910b3c4951e2bc5846a192/tprqiw43evmyvqfeawgg)

As a reminder, that’s 176 billion total parameters. I’m curious what’s going (on/wrong) with expert routing here; deserves a closer look later.

![Pasted image 20250807191034.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/lqb2sw6uidwgstl8bkaq)

![Pasted image 20250807181521.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/wxuh9rqryjligurmbxch)

## The LLaMA 3.x Herd

First place on aesthetic grounds.

![Pasted image 20250807155913.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/kjwt4hv7ycxnzc3jfqpl)

Wow, best rendition of the Global West so far. I suspect this being the only confirmed dense model of its size something to do with the quality.

![Pasted image 20250807161036.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/kwdmuxwtv5jizchd6pu9)

In case you were wondering what hermes-ification does to 405b. Notable increase in confidence (mode collapse, [more pessimistically](https://www.lesswrong.com/posts/t9svvNPNmFf5Qa3TA/mysteries-of-mode-collapse)).

![Pasted image 20250808151532.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/zxr3urcuby9vu2ap4zqt)

## The LLaMA 4 Herd

Most are familiar with the LLaMA 4 catastrophe, so this won't come as any surprise. Scout has 109 billion parameters and it's still put to shame by 3.1-70b.

![Pasted image 20250807161812.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/c8rhql09anmhlwdpbcqp)

Bleh. Maverick is the 405b equivalent, in case you forgot. I imagine that the single expert routing isn't helping it develop a unified picture.

![Pasted image 20250807161437.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/h5f2usna3f7vhgzh3pp6)

## The Gemmas

Ringworld-esque.

![Screenshot 2025-08-08 at 11.48.23 PM.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/d46075b261d1995efc5b004441535c01f194758bece3ecf8b916a297890acdbd/e2azmvuhxpvmejs3z1v3)

I was inconvenienced several times trying to run this model on my laptop, so once I finally did get it working, I was so thrilled that I decided to take my time and render the map at 4x resolution. Unfortunately it makes every other image look worse in comparison, so it might have been a net negative to include. Sorry.

![Screenshot 2025-08-09 at 1.09.55 AM.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/ylphvi7fufy3spbvdw4k)

![Pasted image 20250807190241.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/nrokzbiiaphmfpmu95ia)

![Pasted image 20250807183509.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/nmi7nhjoarok8zkfllo9)

## The Groks

These are our first sizable multimodal models. You might object that this defeats the title of the post ("it's not blind!"), but I suspect current multimodality is so crude that any substantial improvement to the model's unified internal map of the world would be a miracle. Remember, we're asking it about individual coordinates, one at a time.

![Screenshot 2025-08-08 at 3.52.48 PM.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/62f61679066892148f7103f56e815fa12546602ac47c9d8186bfa3ff73caa56b/t0uzwfenxwm5srukwj9d)

[Colossus](https://x.ai/colossus) works miracles.

![Pasted image 20250807144854.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/edgiutpgpv5qfq7od5jn)

## The GPTs

GPT-3.5 had an opaqueness to it that no later version did. Out of all the models I've tested, I think I was most excited to get a clear glimpse into it.

![Pasted image 20250807164513.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/vk6pxrjzgpknssjfw6kp)

Lower resolution because it's expensive.

![Pasted image 20250807002623.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/mo3w1mxzovg0whfm2mlu)

Wow, easy to forget just how much we were paying for GPT-4. It costs orders of magnitude more than Kimi K2 despite having the same size. Anyway, comparing GPT-4's performance to other models, this tweet of mine feels vindicated:

![Screenshot 2025-08-10 at 6.52.00 PM.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/d53701b044205ed4950643b35eaaba73f58d36ba9e4b61bc56f44f56705683b7/m5ipeodut0rnw7itu1ok)

![Pasted image 20250807003248.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/wbbdaheil6wrcotbaqv7)

Extremely good, enough so to make me think there's synthetic geographical data in 4.1's training set. Alternatively, one might posit that there's some miraculous multimodal knowledge transfer going on, but the sharpness resembles that of the non-multimodal Llama 405b.

![Pasted image 20250807171421.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/uwnanxwnkjudx1mkumib)

I imagine model distillation as doing something like this.

![Pasted image 20250807170632.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/wig8auz9psgtxjx6zjac)

Feels like we hit a phase transition here. Our map does not make the cut for 4.1-nano's precious few parameters.

![Pasted image 20250807004553.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/k9tpjckislkrooqcwgch)

I've heard that Antarctica does look more like an archipelago under the ice.

![Pasted image 20250807165500.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/pgnkcmmy4cmrelpoxhvv)

I'm desperate to figure out what OpenAI is doing differently.

![Pasted image 20250807172214.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/swtlfbsgumjvhyxbgbjt)

Here's the chat fine-tune. I would not have expected such a dramatic difference. It's just a subtle difference in post-training; Llama 405b's hermes-ification didn't have nearly this much of an effect. I welcome any hypotheses people might have.

![Pasted image 20250808193043.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/e0f62uignlxcvu2kyokm)

## The Claudes

*(no logprobs provided by Anthropic's API; using n=4 approximation of distribution)*

Claude is costly, especially because I've got to run 4 times per pixel here. If anyone feels generous enough to send some OpenRouter credits, I'll render these in beautiful HD.

![Pasted image 20250807211331.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/u0vqxtnb8nnjme7ojzrt)

![Pasted image 20250807213356.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/a8hqv8imfs302qalqmde)

Opus is Even More Expensive, so for now, the best I can do is n=1.

![Pasted image 20250808191628.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/otbw6ayhavzfkrmeslar)

## The Geminis

Few gemini models give logprobs, so all of this is an n=4 approximation too.

1.5 flash is confirmed to be dense [^4]. The quality of the map is only somewhat better than that of Gemma 27b, so that might give some indication of its size.

![Pasted image 20250808013729.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/dayialn5dquypsjsuehz)

![Pasted image 20250808002915.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/oyxhzjggp7dfq8p6zkie)

![Pasted image 20250808005108.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/daqa4jqc5jjh9gbcsejt)

Ran this one at n=8. Apparently more samples do not smooth out the distribution.

![Pasted image 20250808202251.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/pyj5qbjf8s71ajprbl9b)

I'm really not sure what's going on with the Gemini series, but it does feels reflective of their ethos. Not being able to get a clear picture isn't helping.

![Pasted image 20250808011415.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/xwdRzJxyqFqgXTWbH/zvpt9v48jkidupceilpi)

That marks the last of every model I've tested over a couple afternoons of messing around. As stated previously, I'll probably edit this post a fair bit as I try more LLMs and obtain sharper images.

## Note: General Shapes

Between Qwen, Gemma, Mistral, and a bunch of fairly different experiments I'm not quite ready to post, I'm beginning to suspect that there's some Ideal Platonic Primitive Representation of The Globe which looks like this:

![Screenshot 2025-08-08 at 7.55.40 PM.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/21a9754aba7e0220110388095602b51c1b6bc8d39f623bae09183318811a0b9e/ziqb43ksplikndmafls5)

And which for models smaller yet, looks like this: *(At least from the coordinate perspective. The representations obviously diverge in dumber models)*

![Screenshot 2025-08-08 at 8.01.50 PM.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/00089d1363092dd6b9447bd9be091d213b14cd2b5ed5108e6ba290cc868944b8/bzuobirvkvfa9rp9nfmp)

## Conclusion

I've shown a lot, but admittedly, I don't yet have answers to many of the questions that all this raises. Here are a few I'd like to tackle next, and which I invite you to explore for yourself too:

- What, in the training recipe, actually dictates performance on this test?
- How well do base models do? I've dodged the question so far, as I'm a bit intimidated by the task of setting up a fair comparison between those and the instruct tunes.
- Internally, how is a language model's geographic knowledge structured? (More on this soon)
- What does an expert activation map look like on MoE models?

[^1]: Yeah, the coverage isn't actually even-even.

[^2]: Tokenization isn’t much of an issue. If, say, the model tokenizes "Land" as "La" + "nd", we just look for "La".

[^3]: This excerpt is from the opening of "Chaos: Making a New Science", by James Gleick, describing one of humanity's the earliest meteorological simulations. The imagery just felt fitting.

[^4]: Hearing some confusion about this on Twitter. 1.5 Pro is MoE, and 1.5 Flash is a dense distillation of 1.5 Pro. See: [gemini\_v1\_5\_report.pdf](https://storage.googleapis.com/deepmind-media/gemini/gemini_v1_5_report.pdf)