---
layout: post
title: "Beyond the Hype of Self-Driving Labs: What AI for Science Needs to Succeed"
date: 2026-08-26
description: "Why AI for Science depends on closing the loop between experiments, data representation, models, and decisions."
tags:
  - AI for Science
  - self-driving labs
  - autonomous experimentation
  - machine learning
  - uncertainty quantification
categories:
  - AI for Materials
---

Recently, both academia and industry have been increasingly focused on self-driving labs, experimental automation, and even the idea of “superintelligence” for science.

At their core, however, many of these efforts are trying to build the same fundamental loop:

> *Experiment → Data Representation → Model → Decision → Experiment Again*

<div style="text-align: center; margin: 1.5rem 0;">
  <img src="/assets/img/blog/self-driving-lab-loop.png"
       alt="Experiment–data–model–decision loop"
       style="width: 55%; max-width: 620px; height: auto;">
</div>

While completing my PhD at Duke University and later interacting with technology companies and the venture capital community, I found myself thinking more deeply about what actually makes this loop work.

AI projects in real-world R&D often fail for reasons that have surprisingly little to do with model performance itself.

More often, the problem is that we fail to understand how each component of this loop is connected to the physical world.

For AI to become more than a prediction engine, and instead become a genuine **decision-making tool** in laboratories and R&D environments, I believe each stage has a distinct role to play.

## 1. Experiment: The Anchor for Decision-Making

Experiments are not simply factories that generate data to feed into AI models.

They are the **ground truth that gives our decisions physical meaning**.

They tell us:

- What can we actually control, and what can we observe?
- What are the physical and chemical limits of the system?
- Is an observed effect causal, merely correlated, or simply an artifact of noisy data?

When machine learning is applied without this physical context, there is always a risk of learning patterns that are statistically real but physically meaningless.

Experiments are therefore one of the strongest anchors preventing an AI system from drifting away from reality.

## 2. Data Representation: Structuring Information for Decisions

Collecting more data should not be the end goal.

Data should become **information structured in a way that enables the next decision**.

Raw data coming directly from scientific instruments is often optimized for manual interpretation by researchers, not for machine learning.

Before modeling, that raw information must often be transformed into representations that AI systems can meaningfully use: SMILES-based molecular descriptors, RDKit-derived features, physically meaningful gradients, or other domain-specific representations.

The key question behind data representation is therefore surprisingly simple:

> *What decision does this data structure actually allow us to make?*

A large dataset is not necessarily useful if it cannot inform an action.

## 3. Model: Not an Oracle, but a Summary of What We Know and What We Don’t

Many research teams naturally focus on larger models and higher predictive accuracy.

But in fields such as materials science and chemistry, datasets are often **small, noisy, and heterogeneous**.

Under these conditions, a model is unlikely to become a perfect oracle.

This is why the prediction itself is often less important than understanding its **uncertainty**.

A useful scientific model should tell us not only what it predicts, but also:

- Where does the model have sufficient evidence?
- Where is it extrapolating?
- Where should we simply not trust it yet?

Only when we understand these boundaries can engineers and scientists use model outputs to make high-stakes R&D decisions with appropriate confidence.

> *In many scientific settings, knowing **what the model does not know** is just as valuable as knowing what it predicts.*

## 4. Decision: The Engine That Completes the Loop

Decision-making is the stage where insights from experiments, data, and models are translated into action.

For example:

- Which experiment should we run next?
- Which variables are no longer worth exploring?
- What additional measurements would most effectively reduce uncertainty?

Approaches such as **active learning and Bayesian modeling** can move us beyond passive prediction toward recommending the most informative next experiment.

That decision then leads to another experiment, which produces new data, updates the model, and drives the next decision.

As the loop continues, the system should do more than simply accumulate data.

Ideally, it becomes progressively better at understanding **which decisions matter and why**.

## What I Learned from My PhD Research at Duke

Looking back, much of my research at Duke University and earlier at Samsung Electronics can be viewed as working on different parts of this loop.

### 1. Experimental Foundation

During my work on p-type doping of mixed tin–lead perovskites, I spent long days fabricating devices and running experiments in the lab.

That experience taught me firsthand how expensive and slow high-quality scientific data can be to generate, and how strongly experimental constraints shape what questions we can realistically ask.

### 2. Data Representation and Interpretable Machine Learning

While working with datasets for 2D perovskite solar cells, I transformed heterogeneous experimental data into chemically meaningful descriptors that machine-learning models could use.

I then built interpretable models designed not only to make predictions, but also to reveal which material and chemical factors were driving them.

### 3. Uncertainty-Aware Decision-Making with Bayesian Modeling and Active Learning

In another project involving low-dimensional hybrid metal halides, the available dataset was extremely limited.

Rather than treating the problem as conventional supervised learning, I developed uncertainty-aware Bayesian models and an active-learning framework for selecting informative candidates.

This approach improved candidate discovery efficiency by approximately **20% compared with random selection**.

Across these projects, I gradually became less interested in asking:

*“How accurate is the model?”*

and more interested in asking:

> *“What decision does this model allow us to make next?”*

## Closing Thoughts

The core challenge of AI for Science is not simply building larger models.

It is **closing the gap between the physical reality of the laboratory and the predictions produced by machine learning systems**.

A self-driving lab is only as useful as the loop connecting its experiments, representations, models, and decisions.

For me, this is one of the most interesting problems in scientific AI: building systems that remain useful and trustworthy even when data is limited, experiments are expensive, and uncertainty is unavoidable.

I am particularly interested in connecting with researchers and technology teams working on AI for Science, autonomous experimentation, and uncertainty-aware decision-making in real-world R&D.

If you are working on related problems or simply want to exchange ideas, feel free to reach out through [LinkedIn](https://www.linkedin.com/in/migonchoi1998).
