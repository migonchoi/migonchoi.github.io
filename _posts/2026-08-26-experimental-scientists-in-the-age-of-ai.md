---
layout: post
title: "Will AI Replace Experimental Scientists? Why Your Lab Intuition Is More Valuable Than Ever"
date: 2026-08-26
description: "Why experimental scientists' domain knowledge may become more valuable in the age of AI—and how to start connecting that knowledge to data and algorithms."
tags:
  - AI for Science
  - experimental science
  - machine learning
  - autonomous experimentation
  - research
categories:
  - STEM Research & Career
---

AI is rapidly taking over many kinds of work, and we are hearing more and more about AI and machine learning in research as well. Now that people are even talking about “vibe coding,” experimental scientists may find themselves thinking,

> *“I feel like I should start doing something too. But where am I supposed to begin?”*

I have worked in both research laboratories and industry, and I started my research career as an experimental scientist. Since 2022, I have been actively incorporating AI and machine learning into experimental science. So rather than writing from the perspective of someone trained in computer science, I want to write from the perspective of someone who started in experimental research, learned AI, and then applied it to real scientific problems.
<br>

## The Limits of LLM Hype in the Lab

Recently, especially through early 2026, expectations around AI, especially large language models (LLMs), were extremely high. At times, the conversation made it sound as though LLMs would eventually be able to do almost everything, leaving experimental scientists with little more than the role of generating data. I do not agree.

LLMs are undeniably useful. In particular, I believe they will continue to play an important role in reading information from unstructured text such as scientific papers, identifying relationships between different concepts, and extracting data from large bodies of literature to build datasets. But that does not mean I expect LLMs to solve every fundamental scientific problem. Instead, I think we will continue to need new models and systems specialized for individual scientific problems. And at least for now, I believe we may be entering a period in which the domain insights held by experimental scientists become more valuable than before.
<br>

## So How Can Experimental Scientists Make Better Use of Those Insights?

First, think about what we do in the lab every day. Even if we assume that the general direction of a project has already been decided, actually carrying out an experiment requires a huge number of decisions. Take chemistry or materials science as an example.

Which reagent should you use? You have probably read previous papers, compared existing results, and selected candidates based on the chemical and physical principles you understand. You are not simply copying a material that appeared in a paper. You are making a judgment: *“Why might this material work in this particular system?”* That is already an important insight.

Which instrument should you use? Which experimental protocol should you follow? Even when working with the same material, the outcome can change dramatically depending on synthesis conditions, temperature, time, atmosphere, concentration, and instrument settings. Experimental scientists choose these conditions based on experience, the literature, and previous experimental results.

The decision-making continues while the experiment is running. If you are using a glovebox, for example, you may monitor oxygen and moisture levels, pressure, and the condition of the equipment. If one of those numbers is slightly different from usual, you may have to decide whether the difference is large enough to affect today's experiment. A machine can record a number such as “oxygen level: 0.5 ppm.” But an experimental scientist decides whether that number matters for today's experiment, whether it can safely be ignored, or whether it is serious enough to call the entire result into question. That, too, is valuable insight.

The same is true after the experiment is finished. You organize and analyze the data coming from the instrument and decide which results are meaningful. You try to determine whether a particular data point represents a genuinely new phenomenon, a measurement error, or an artifact introduced during sample preparation.

And finally, you decide what experiment to do next.

* Why did you increase the temperature next time?
* Why did you switch to a different precursor?
* Why did you decide that a particular region of the parameter space was no longer worth exploring?
* Why did you decide to run another replicate?

Most of these decisions are never fully documented in scientific papers. In many cases, they are not recorded in the data files either. But real science progresses through exactly this kind of continuous sequence of small decisions. And I think this is one of the most interesting areas in AI for Science today.
<br>

## The Gap Between Computation and Autonomous Labs

Look around and you will see, on one side, researchers using simulation and computational screening to explore thousands or tens of thousands of candidates. But a question remains:

> *How do we bring a candidate discovered inside a computer into the real experimental world?*

On the other side, researchers are trying to build autonomous laboratories using robotics. This is also an extremely important direction. But just because a robot can perform experiments in the physical world does not mean that the domain insight of an experienced experimental scientist is automatically embedded in that system.

So what exists between these two areas? I think there is still an enormous amount of opportunity there.

* How should we translate candidates proposed by simulation into actual experiments?
* Which experiment should we run first?
* Which conditions are physically unrealistic?
* Which data should we not trust?
* Which changes during an experiment actually matter?
* And when new results come in, how should we choose the next experiment?

These are all places where the knowledge of experimental scientists can meet AI. So the point I want to make is simple. **The judgments you make so naturally in the laboratory, sometimes almost unconsciously, may be far more important and valuable pieces of information than you realize.**
<br>

## Then What Do You Need to Do to Connect Those Insights to an Actual AI System?

First, AI, machine learning, and statistics use a somewhat different language from the experimental sciences we are familiar with. That does not mean experimental scientists need to become computer scientists or mathematicians. But it is useful to understand the core concepts behind the techniques you want to apply.

A short course may be enough. So might a good review paper. You should understand, at a basic level, what a model takes as input and produces as output, what uncertainty means, why training and validation data are separated, and under what circumstances you should not trust a model's results. The important thing is not to perfect the algorithm itself. The first priority is to define your domain problem clearly.

* What is currently the most expensive part of the process?
* What takes the most time?
* Are you running too many experiments?
* Are material costs too high?
* Is there a part of the workflow where a person repeatedly has to make the same kind of judgment?
* Are you missing promising candidates?
* Is experimental reproducibility poor?

Start by asking which parts of these problems might be improved with the help of AI.

Once you have developed some understanding of AI and algorithms, I also recommend collaborating with methodologists. The person writing the actual code and applying the algorithm to your domain may very well be the experimental scientist. In many cases, that can actually be much more powerful. But there is a great deal to gain from working with someone who studies the methodology deeply when it comes to questions such as whether your statistical assumptions are appropriate, whether you are misinterpreting the model, whether your validation is sufficient, or whether you are placing too much trust in the algorithm.
<br>

## A Simple Exercise for Today

Finally, I want to suggest one very simple exercise you can do right now. Think through an ordinary day in your laboratory and ask yourself:

> *“What decision am I actually making here?”*

Then try to write down as many of those decisions as possible.

* Why did I choose this precursor?
* Why did I choose this concentration?
* Why did I decide that this data point was an outlier?
* Why did I think this measurement needed to be repeated?
* Why did I move the next experiment in this direction?
* What equipment conditions do I consider acceptable, and at what point do I decide to stop the experiment?

The answers to these questions may be more than just research know-how. If you eventually build an AI system, these judgments could become features, constraints, or objectives. In some cases, they could become feedback signals or decision rules. Before asking how you might hand your experiments over to AI, first write down the decisions you are already making.

The most important asset of an experimental scientist may not simply be the ability to perform an experiment. It may be knowing what to observe and knowing what judgments to make based on what you observe. And in the age of AI, I believe experimental scientists who can make those judgments explicit and connect them to data and algorithms may become more valuable than ever.
