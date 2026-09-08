---
layout: post
title: "AI-Ready R&D Starts Before the AI: Structuring the Knowledge Your Engineers Already Have"
date: 2026-09-08
description: "AI-Ready R&D Starts Before the AI: Structuring the Knowledge Your Engineers Already Have"
tags:
  - AI for Science
  - self-driving labs
  - autonomous experimentation
categories:
  - AI for Materials
---

Many manufacturing and materials companies are thinking hard about how to apply AI to R&D.

But I think there's something that needs to be checked first:

> **Is the experimental knowledge that already exists inside the company actually organized in a form AI can use?**

Most R&D organizations have researchers and engineers who have spent years operating equipment and optimizing processes. They can spot anomalies just by looking at data, know empirically why certain conditions don't work well, and judge which results can be trusted and which need to be double-checked.

Some of this knowledge is recorded in SOPs, lab notebooks, reports, and databases. But a significant portion likely lives in personal notes, conversations from meetings, team-internal practices, or simply in people's heads.

And even when things are well documented, that doesn't automatically mean they're **AI-ready**.

## The Numbers Are Not the Whole Experiment

Suppose a database stores the following information:

* Process temperature: 300°C
* Pressure: 5 Torr
* Precursor flow rate: X sccm
* Film thickness: 100 nm

This information is certainly important on its own.

But to actually design experiments and decide on the next set of conditions, the questions behind these numbers matter just as much:

* Why was 300°C chosen?
* What failure mode was this condition meant to avoid?
* What are we actually trying to optimize: thickness, uniformity, defect density, or yield?
* When a result is poor, which variable do we suspect first?
* What signals make an experienced engineer distrust this experiment?

This kind of information is easy to leave out of traditional experimental datasets.

But if AI is going to recommend experimental conditions, decide on the next experiment, or eventually become part of an autonomous lab, this information may turn out to be critical.

## The Knowledge That Lives Outside the Database

Take a team optimizing a thin-film deposition process.

The database may properly record temperature, pressure, precursor flow rate, and film thickness. But an engineer who has worked with the equipment for a long time might also know things like:

* The process tends to become unstable within a certain pressure range.
* The first few runs right after chamber cleaning behave differently than usual.
* When a certain optical signal appears, film uniformity is likely to deteriorate afterward.

These can look like minor operational details.

But when AI needs to decide on the next experiment, they can become important descriptors.

So I don't think the first step of adopting AI should necessarily be finding a better model.

Instead, the first task may be to **surface and structure the experimental knowledge that already exists within the organization.**

## Start by Asking the People Who Already Know

Questions such as why a particular condition was chosen, which signals are trusted, and which results should be treated with caution often live in people's heads rather than in a database.

So figuring out how to surface this knowledge inevitably starts with asking people on the ground directly.

For example, researchers and engineers could be asked:

* What are we actually trying to achieve?
* Which variables can we directly control?
* What result would we consider a success?
* What signals make us trust or doubt an experimental result?
* Why do we prefer certain conditions over others?

If answers to these questions are collected systematically, existing experimental records can gradually shift from being a simple **data repository** into a **knowledge base that can explain decisions**.

## So How Do You Actually Structure This?

There's a gap between asking these questions and turning the answers into a genuinely machine-readable asset.

A few practical approaches come to mind.

### 1. Add Rationale to the Experimental Schema

One approach is to change the schema of the experimental log itself.

Instead of recording only **what was done**, an electronic lab notebook (ELN) could include a structured or mandatory **rationale** field capturing:

* Why this condition was chosen
* What hypothesis motivated the experiment
* What alternatives were considered
* Why certain alternatives were ruled out

At first, this may feel like additional overhead.

But once this information accumulates, the reasoning behind experimental condition selection becomes searchable data in its own right.

The organization is no longer storing only:

> **Condition → Result**

It begins to store:

> **Context → Reasoning → Condition → Result**

That is a much richer object for an AI system to learn from.

### 2. Structure Success and Failure Criteria

Another approach is to explicitly capture the criteria used to judge experimental outcomes.

For the same experimental result, one team might judge success primarily by film thickness, while another might care more about uniformity, defect density, device performance, or yield.

If these criteria are represented using an ontology or metadata schema, an AI system no longer has to infer why an experiment was labeled successful.

For example, instead of storing only:

* `outcome: success`

the system might capture:

* `primary_objective: film_uniformity`
* `acceptable_variation: < 5%`
* `secondary_constraint: thickness > 100 nm`
* `failure_mode: edge_nonuniformity`

The important part is not necessarily the exact schema.

It is making the **judgment criteria themselves explicit**.

### 3. Let AI Help Extract Tacit Knowledge

A third, and perhaps more interesting, direction is to have an LLM directly interview engineers to extract tacit knowledge as text.

Instead of requiring a person to design and conduct every interview, an AI system could first read through experimental logs and identify missing reasoning.

For example:

> *The log records that the temperature was changed from 280°C to 300°C, but it doesn't explain why. What observation led to that decision?*

Or:

> *Several experiments near 5 Torr were abandoned. Was this due to equipment instability, material quality, or another factor?*

The engineer answers, and the system connects that explanation back to the relevant experimental records. This creates an interesting loop.

AI is not only being introduced **after** an organization becomes AI-ready. AI itself can help the organization become AI-ready by identifying gaps in its own experimental knowledge base.

In a sense, this could be one of the first experiments on the path toward an autonomous lab.

## The Organizational Layer Matters Too

A technical mechanism alone isn't enough. If engineers are simply told to *"fill in the rationale field,"* it can easily become one more task added on top of an already full workload. Resistance is a natural outcome.

So alongside the technical infrastructure, there also needs to be an organizational and cultural layer: some way of recognizing the researchers who take the time to systematize their knowledge.

That could mean:

* Formal credit in performance reviews
* Attribution when someone's documented reasoning shapes a model or later experiment
* Visibility into how often a person's documented knowledge is reused
* Recognition for improving organizational knowledge infrastructure

The exact mechanism can vary.

The underlying goal is the same:

> **Turn knowledge documentation from an invisible chore into something the organization actually recognizes and rewards.**

## That Said, This Isn't Easy

Structuring tacit knowledge is not as simple as it sounds.

Different engineers may explain the same phenomenon differently or use different judgment criteria. It is difficult to treat one person's tacit knowledge as the universal standard.

For engineers who are already stretched thin, recording rationale for every experiment can also feel like an added burden. Getting organizational buy-in is therefore a problem of its own.

There is also a time component. When experienced people leave or move on, the judgment criteria unique to them can disappear with them. Structuring this knowledge is partly meant to prevent that loss, but if it isn't drawn out before they leave, it may already be too late. And some judgments may simply be difficult to verbalize in the first place.

An intuition like *"it just looked off"* may encode years of pattern recognition, but there are real limits to how completely that intuition can be captured using text, tags, or predefined metadata fields.

None of this makes the problem less important. It simply means that tacit knowledge should probably be treated as something to **progressively capture and refine**, rather than something that can be perfectly formalized all at once.

## Before Better AI, Build Better Knowledge Infrastructure

Despite these challenges, I think it is better to start structuring this knowledge imperfectly now rather than delaying because the representation will never be perfect.

Going forward, one of the key sources of competitive advantage for AI-ready R&D organizations may be exactly this. It may not be the company with the most experimental data that moves fastest.

It may be the company that has done the best job of structuring its own experimental knowledge - its assumptions, reasoning, failure criteria, contextual signals, and accumulated engineering judgment.

Because that is the information an AI system ultimately needs if it is expected to do more than fit a model.

It needs it if we want AI to help decide:

* Which experiment should come next?
* Which result should be trusted?
* Which variable should be changed?
* Which operating region should be avoided?
* When should a human expert step in?

Perhaps the first step toward an autonomous lab isn't automation itself.

It may start by capturing the experimental judgment we're already good at—and turning it into a form machines can learn from.
