---
layout: post
title: "The Decision Layer Demo"
date: 2026-09-26
description: "Models propose experiments and robots run them. Something in between has to decide what actually happens next, and that is the part I am building."
tags:
  - AI for Science
  - self-driving labs
  - autonomous experimentation
  - experimental design
  - decision making
categories:
  - AI for Materials
---

## Try it first

**[Run the demo](/demo/decision-layer/)** — press the button a few times and watch what the engine says. One minute is enough.

![Decision layer demo](/assets/img/decision-layer-demo.gif)

## The gap I keep coming back to

A lot of attention in AI for science has gone to two ends of the experimental loop.

On one end, models propose and prioritize experiments through simulation, machine learning, foundation models, and LLMs. On the other, robotics and automation physically run those experiments. But something still has to decide what actually happens next.

- With limited time, budget, and instrument capacity, which experiment should run next?
- How much should we trust the model's suggestion and the data coming back from the lab?
- When should we repeat, wait, characterize further, or stop?

This is the layer I want to build: AI systems that make useful experimental decisions under the noise, drift, and constraints of real labs.

Knowing whether a result is actually actionable requires more than a model prediction. It requires an understanding of both the experiment and the uncertainty around it.

## Why the second question matters more than it looks

Optimization and active learning methods can tell us what experiment would be most useful to run next. But in practice, that only helps if the data coming back from the lab is usable. Real experiments fail in ordinary ways. A sample may be contaminated. An instrument may drift. A reagent may age. A device contact may be bad.

Researchers deal with this constantly. You look at today's control samples, realize that something is off, and decide not to trust the batch. That decision is important, but it is rarely recorded in a structured way. It often stays in someone's head, and the criteria can vary from person to person.

The demo makes that decision explicit. For every run, the engine decides whether the result should be trusted and explains why.

## What the demo does

Each press represents one day in a lab.

Six films are made: three controls and three treated samples. The simulated glovebox conditions drift over time, as experimental environments often do. You do not know what kind of day it was until the measurements come back.

The engine then makes one decision:

- **Run.** Controls are normal, so this result counts.
- **Repeat.** Usable, but not enough yet to conclude.
- **Defer.** Today's data cannot be trusted, and here is what to check.
- **Characterize and stop.** The question has been answered.

The engine also looks across runs. Three flagged days in a row may not be three unrelated bad days. They may point to a systematic problem, such as a glovebox that needs a pressure decay test.

That distinction matters because experimental decisions are rarely made from one measurement in isolation.

## Where the rules came from

The numbers in the demo are synthetic. The decision logic is not. I first tested these rules by replaying the experimental history of a study I published on molecular doping of tin lead perovskites ([paper](https://doi.org/10.1021/acsami.5c19800)).

As in most experimental work, we only analyzed runs in which the control samples behaved consistently. That quality judgment was essential to interpreting the results, but it was made as part of the research process rather than represented explicitly in an algorithm.

The replay asked a different question: what if those decisions had been made systematically after every run?


Two things stood out.

- First, the runs that the engine judged trustworthy reproduced the published average for one of the dopants.

- Second, the engine recommended stopping at the same point we did.

This was a small retrospective test, not a validation of a general system. But it showed me that experimental judgment can be represented more explicitly than it usually is.



The long-term question I am interested in is simple:

**Can we build systems that do not just suggest experiments or execute them, but also know when the evidence is good enough to act?** 
