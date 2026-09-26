---
layout: post
title: "The Decision Layer: What Should We Actually Run Next?"
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

Most of the attention in AI for science has gone to two ends of the loop. On one end, models that generate and prioritize candidates: foundation models, simulation, LLMs. On the other, platforms that physically run experiments: robotics and automation.

In between sits the layer that decides what actually happens next.

- With limited time, budget, and instrument capacity, which experiment should run next?
- How much should we trust the model's suggestion, and the data coming back from the lab?
- When is the right move to repeat, wait, characterize further, or stop?

This is the layer I want to build: AI systems that make useful decisions under the noise, drift, and constraints of real experimental environments. Knowing when an output is actually actionable takes both wet-lab intuition and depth in AI/ML.

## Why the second question matters more than it looks

Bayesian optimization and active learning assume the data coming back is trustworthy. In a real lab that assumption breaks regularly through contamination, drift, aged reagent, or a bad contact, and nothing in the acquisition function notices.

Researchers handle this every day. You look at today's control, decide the batch is off, and redo it. That judgment rarely gets written down, and it differs from person to person. The demo makes that call explicit, every run, with the reasoning attached.

## What the demo does

Each press is one day in a lab. Six films get made: three controls, three treated samples. The glovebox drifts on its own, the way it does in reality, and you only find out what kind of day it was after the engine has judged it.

The engine returns one call per run:

- **Run.** Controls are normal, so this result counts.
- **Repeat.** Usable, but not enough yet to conclude.
- **Defer.** Today's data cannot be trusted, and here is what to check.
- **Characterize and stop.** The question has been answered.

It also reads across runs. Three flagged days in a row is not three bad days; it is a glovebox that needs a pressure-decay test.

## Where the rules came from

The numbers in the demo are synthetic. The rules are not.

They were first replayed, run by run, over the experimental log of a study I published on molecular doping of tin-lead perovskites ([paper](https://doi.org/10.1021/acsami.5c19800)). In the paper, as in most experimental work, we analyzed only runs whose control samples behaved consistently. That judgment is essential, and it is usually made after the fact. The replay made it at every run instead.

Two things came out of that exercise. The runs the engine judged trustworthy reproduced the published average for one of the dopants. And it called stop on the same run we did.

## What I am looking for

I would like to talk with:

- teams running automated or semi-automated experimental platforms who want a decision layer on top of their models and hardware
- materials and chemistry groups with past experiment logs, messy runs included, who would like to see what a replay reveals
- researchers and investors who see decision-making under real lab constraints as core to autonomous experimentation

