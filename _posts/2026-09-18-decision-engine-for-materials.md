---
layout: post
title: "Decision Engine for Materials R&D: Beyond Prediction and Automation, Toward the Age of Decision-Making"
date: 2026-09-18
description: "Why AI for Science depends on closing the loop between experiments, data representation, models, and decisions."
tags:
  - AI for Science
  - Materials R&D
  - self-driving labs
categories:
  - AI for Materials
---

## Introduction: We Need Better Decisions, Not Just More Experiments

AI for Materials R&D is advancing rapidly. Simulation and AI are proposing vast numbers of candidate materials, while robotics and Self-Driving Labs are beginning to automate experiments themselves. But generating more candidates and running experiments faster does not automatically make the overall R&D process more efficient.

In real laboratories, different kinds of decisions need to be made at every moment.

Should I continue this experiment?
If the control looks abnormal, should I remake the sample?
If the environment is unstable, would it be better to wait a day?
Should I perform characterization before running additional experiments?
If enough evidence has already been collected, should I stop the project here?

In this article, I refer to the software layer responsible for these decisions as an **Experimental R&D Decision Engine**, or **Decision Layer**.

To examine this idea, I reconstructed the experimental process using data from a perovskite doping research project that I previously conducted. Over approximately 4.5 months, the project involved 26 experimental runs and 143 Hall measurements, but only a subset of those measurements directly contributed to the key conclusions of the final paper.

This does not mean that all failed experiments were unnecessary. Failure is important information in research. However, if the control status, environmental changes, and previous experimental results had been systematically connected at the time, some experiments might have been repeated earlier, deferred, or stopped. In R&D, time, reagents, equipment, and budgets are all limited.

Therefore, the important question for the future of Materials R&D may not simply be **“What is the next candidate?”**, but rather,

> **“Given the current state, what is the most reasonable action to take next?”**

---

## 1. What Is Missing Between Prediction and Automation

The evolution of AI in Materials R&D can be broadly divided into three stages.

### Stage 1: Prediction — The Age of Prediction

Simulation, machine learning, generative models, and LLMs explore vast candidate spaces and propose promising materials or experimental conditions. The key question is:

**“What should we experiment on?”**

### Stage 2: Execution — The Age of Automation

Robotics and Self-Driving Labs automate synthesis, processing, and measurement tasks that were previously performed manually. The key question is:

**“How can we run experiments faster and more reproducibly?”**

### Stage 3: Decision Engine — The Age of Decision-Making

But one important layer is still missing between Prediction and Execution. Just because a predictive model proposes a candidate does not mean that the experiment should always be run immediately.

A control sample may be abnormal, the oxygen concentration in the glovebox may be elevated, or a precursor may be too old. Equipment may be unstable, or repeated measurements under the same condition may need to come first.

A Decision Engine integrates this information and determines the next action (Figure 1).

**RUN / REPEAT / EXPLORE / DEFER / CHARACTERIZE / STOP**

In other words, it does not decide what to predict. It decides **what to do given the current state**.

An autonomous-driving analogy helps illustrate this idea.

* **Simulation / AI model** = a map that calculates the route to the destination
* **Robotics / Automation** = the vehicle that physically follows the route
* **Decision Engine** = the control system that looks at road conditions, weather, and vehicle status and decides whether to proceed, stop, or reroute

Even with a good map and a fast vehicle, fully autonomous driving is difficult without a control system that can respond to real-time conditions. The same is true in the laboratory.

<div style="text-align: center;">
  <img src="/assets/img/blog/decision-engine-overview.png" alt="Decision Engine architecture for materials R&D" width="70%">
</div>

<p style="text-align: center; font-size: 0.95rem;">
  <em>Figure 1. Conceptual architecture of an Experimental R&D Decision Engine.</em>
</p>

---

## 2. Why a Decision Engine Is Needed

### 2.1 R&D Cost Is Determined More by ‘Which Experiments Are Run’ Than by ‘How Many Experiments Are Run’

Resources in experimental R&D are limited. Every run consumes reagents, substrates, equipment time, researcher time, and characterization costs. Therefore, rapidly repeating low-value experiments does not necessarily mean that research is being conducted efficiently.

The goal of a Decision Engine is not simply to reduce the number of experiments.

It is to **identify experiments that have low information value or a high probability of failure under the current state**.

---

### 2.2 Real Laboratories Are Noisy

One of the biggest differences between a simulation environment and a real laboratory is uncertainty.

Temperature and humidity change, and O₂ and H₂O concentrations in a glovebox fluctuate. Reagents degrade over time, and equipment conditions also change gradually. Even when the same protocol is used, the results may not be identical. These variables are not merely noise; they are part of the actual experimental state.

Therefore, for Physical AI to operate in a real laboratory, it needs more than automated execution. It also needs **logic that determines whether the current experimental environment is valid**.

---

### 2.3 Data Quality Comes Before the Model

If data generated under invalid conditions are directly fed into an AI model, subsequent predictions can also become distorted. A Decision Engine can therefore serve not only as an experimental scheduler but also as a **quality gate** before data enter the database.

For example, it can automatically flag runs that fail Control QC or separately classify data generated under environmental conditions outside the normal range. A good AI model first requires a good data-generating process.

---

## 3. Testing the Decision Engine on a Real Perovskite Research Project

To examine whether this idea could be meaningful in a real experimental workflow, I reanalyzed a previously published perovskite doping research project. The dataset consisted of experiments conducted over several months.

* 26 experimental runs
* 143 Hall measurements
* Undoped control and two dopant conditions
* Records of glovebox abnormalities during certain periods
* Results used in the final published paper

The overall process can be simplified as follows.

**Precursor Preparation → Solution Processing → Hall Measurement**

I evaluated the Decision Engine in two different ways. One was **Replay**, which used only historical data that actually existed, while the other was **Simulator**, which introduced explicitly stated assumptions. I intentionally kept these two tracks separate.

---

## 4. Track A: Replay — Re-running Past Decisions Using Only Recorded Data

The goal of Replay is simple.

> **What would the Decision Engine have decided if it had used only the information available at the time?**

I entered the 143 Hall measurements and 26 batches recorded between February and October 2023 in chronological order. There was one important principle.

**Do not invent information that was never recorded.**

If missing values are filled in retrospectively after the outcome is already known, it becomes easy to fall into circular reasoning.

### Quality Gate Using the Control

The most basic decision criterion was the carrier density of the Undoped Control.

I checked whether the Control remained roughly within

$$
10^{14} - 10^{15}\,\mathrm{cm}^{-3}
$$

and showed consistency across repeated measurements, and used this as a basic validity indicator for each run. If the Control itself was abnormal, then the run should first be questioned, no matter how interesting the doped-sample result appeared.

---

## 5. The First Pattern from Replay: Many Experiments Could Have Been Stopped Earlier

When I reanalyzed the 16 runs conducted before July, runs with either no Control or a Control that failed the QC criteria appeared repeatedly. The 43 doped samples measured during this period lacked a reliable comparison group according to the Decision Engine criteria.

In other words, if a real-time Decision Engine had existed, rather than simply continuing to fabricate the next sample, it might first have recommended

**REPEAT** or **DEFER**.

In Replay v0.1, I also incorporated later-confirmed records of O₂ leakage and elevated H₂O levels in the glovebox as environmental variables. For the runs on July 5 and July 12, the engine recommended **DEFER** rather than simply repeating the experiment—in other words, pausing the experiment until the environment returned to normal.

---

## 6. The Engine Could Also Partially Reproduce the Researcher’s Actual Decisions

In the later part of the Replay, an interesting alignment appeared between the engine’s recommendations and the actual direction of the research. In the October 11 data, measurement variability was high, and the Decision Engine recommended an additional **REPEAT**.

After the October 13 data were included, there was enough evidence to support the differences between conditions, and the engine recommended

**CHARACTERIZE → STOP**.

Around the same time in the actual research process, I also moved away from expanding the Hall experiments and toward consolidating the results, conducting characterization, and writing the paper. In other words, a Decision Engine may be useful not only for blocking failed experiments, but also for determining **“When has enough evidence been collected?”**

---

## 7. Could It Also Reproduce the Published Results?

I recalculated the average carrier density values using the data selected by the Decision Engine according to its QC rules. The resulting values were:

* Undoped: $3.76 \times 10^{14}\,\mathrm{cm}^{-3}$
* Mo dopant: $3.89 \times 10^{15}\,\mathrm{cm}^{-3}$
* F₄TCNQ: $7.51 \times 10^{17}\,\mathrm{cm}^{-3}$

Compared with the average values reported in the Supporting Information of the published paper, the differences were approximately **+4.5%, 0%, and -6%**.

In other words, even simple QC and decision rules were able to produce results quite similar to the post hoc data-selection process carried out by the researcher. This was the first signal of the potential of the Decision Engine.

---

## 8. Track B: Simulator — What If Environmental Sensors Had Been Available?

Replay has a clear limitation. During the original experiments, changes in glovebox O₂ and H₂O were not stored as structured data at every time point. Rather than retroactively inventing missing historical values and feeding them into Replay, I created a separate Simulator Track.

In this Track, every estimated value was explicitly labeled as a **synthetic / assumed value**.

I generated 1,500 synthetic experimental projects and tested the following question:

> **How many unnecessary experiments could be avoided if environmental sensor data were connected to the Decision Engine?**

---

## 9. Simulator v0: Even H₂O Alone Reduced Experimental Waste

The first simulator was very simple. If the glovebox H₂O concentration exceeded a predefined threshold, the engine would DEFER the experiment rather than proceed. No complex AI model was used. It was a simple rule-based decision. Under a specific leak scenario, the number of films fabricated under contaminated conditions dropped from 25 to approximately 4–7. Relative to the total number of fabricated films, this corresponded to preventing approximately **18–21% of unnecessary sample fabrication**.

---

## 10. Simulator v1: The Important Question Is Not ‘How Many Sensors?’ but ‘Are You Looking at the Right Variable?’

A more important result emerged here. Using H₂O alone as an absolute criterion created a problem. If the experiment was stopped whenever H₂O exceeded 0.3 ppm, the engine sometimes DEFERRED experiments even on days when the experiment could actually have proceeded. In the Simulation, these false positives created an average of **2.8 days of unnecessary delay** per project.

However, when I incorporated domain knowledge that the relevant dopant chemistry was much more sensitive to oxygen than to moisture and changed the primary control variable to O₂, the result changed. The engine prevented contaminated samples at a similar level while reducing unnecessary delay from **2.8 days → 0.1 days**.

This result shows that the key to a Decision Engine is not simply connecting more sensors. **The system must be designed with domain knowledge about which variables matter and how sensitively it should respond to them.**

---

## 11. What Did We Learn?

Four findings stood out from the Replay and Simulation.

First, **Control QC alone could identify many low-value experiments early.**

Among the 16 runs before July, reliable controls were often missing, and the 43 doped samples from this period therefore had limited interpretability.

Second, **adding environmental information made it possible to distinguish between REPEAT and DEFER.**

If the sample itself is the problem, the experiment should be repeated. But if the environment itself is the problem, immediately repeating the same experiment does not make sense.

Third, **environment-based decision rules showed the potential to reduce the fabrication of defective samples.**

In the synthetic simulation, approximately 18–21% of sample fabrication could be avoided.

Fourth, **an overly conservative decision rule creates a new cost.**

Using H₂O alone as an absolute criterion introduced 2.8 days of delay. In contrast, an O₂-based rule aligned with the chemistry reduced this to 0.1 days.

In other words, the goal of a good Decision Engine is not simply to minimize failure.

It is to **balance failure cost, delay cost, and information value**.

---

## 12. Beyond Automation: Controlling Uncertainty

Many discussions around Autonomous Labs emphasize how quickly robots can run experiments. But automation does not necessarily mean better decision-making. If an automated system fabricates hundreds of samples while the environment is invalid, it may waste resources far faster than a human researcher.

An automated system therefore needs a separate logic layer that can answer questions such as:

**Is the current experimental state valid?**

**Is there enough evidence to run the next experiment?**

**Should the experiment be repeated, or should another condition be explored?**

**Would it be better to wait until the environment recovers?**

**Is the information gain from an additional experiment large enough?**

This is the domain I refer to as the Decision Layer.

---

## 13. A Decision Engine Can Incorporate Much More Context

Real experimental decisions are influenced by far more variables than O₂ and H₂O.

For example, the following information could all form part of the experimental state.

### Reagent and Material State

* Date of reagent purchase and opening
* Storage location and conditions
* Time elapsed since solution preparation
* Precursor aging
* Batch or lot information

### Laboratory Environment

* O₂ / H₂O
* Temperature and humidity
* Equipment condition
* Maintenance history
* Environmental changes such as nearby construction or vibration

### Research Resources

* Remaining quantity of expensive reagents
* Number of available substrates
* Equipment availability
* Current project budget
* Characterization cost

### Project State

* Results from previous runs
* Control reliability
* Measurement uncertainty
* Current evidence level for the hypothesis
* Remaining alternative hypotheses

With this information, a Decision Engine can move beyond a simple pass/fail system toward multi-objective decision-making.

For example,

> The probability of success is 60% if the experiment is run now, but it will consume an expensive reagent.

versus

> Waiting one day would increase the probability of success, but it would delay the project schedule.

The system could then expand into a decision problem that jointly considers **cost, time, uncertainty, and information gain**.

---

## 14. Why Replay and Simulation Must Be Kept Separate

One part of this project that I considered especially important was separating data according to their origin. If sensor values that did not exist in the historical record are estimated retroactively and then used to claim that “the system could have made this decision at the time,” the result can easily become distorted. That is why I kept the two Tracks clearly separated.

**Replay**

Uses only data that were actually recorded at the time.

The question is:

> “What could have been decided using only the information that was actually available then?”

**Simulator**

Introduces realistic assumptions explicitly.

The question is:

> “If these sensors and data existed in the future, what value could they create?”

As Decision Engines become more sophisticated, data provenance and assumption tracking may become just as important as the model itself.

---

## 15. A Decision Engine Is Not Only for Self-Driving Labs

When people first think about this idea, it is easy to imagine a large robotics facility or a fully autonomous laboratory. But it can begin in a much smaller form.

Even in a conventional wet lab where researchers perform experiments manually, the system could provide guidance such as:

> “Given today’s glovebox conditions, it would be better to defer this experiment.”

> “Control variability is high. Consider repeating the experiment before moving to the next condition.”

> “There is enough evidence to evaluate the current hypothesis. Consider characterization before fabricating additional samples.”

In other words, the system does not need to control a robot from the beginning. The first product could be **experimental decision-support software** that helps researchers make decisions.

As laboratory automation increases, this software layer could evolve from a human-facing decision-support tool into the control layer of an autonomous system.

---

## Conclusion: Better Decisions, Not Just Faster Experiments

The future of Materials R&D may not depend only on generating more candidates or running experiments faster. Prediction tells us **what may be possible**, Automation **executes the experiment**, and the Decision Engine sits between them and decides **“What should we do given the current state?”**

This small Replay and Simulation study does not demonstrate a complete autonomous laboratory. But by revisiting real research data, it revealed one possibility.

The decisions that were previously scattered across a researcher’s experience and intuition—

**RUN / REPEAT / EXPLORE / DEFER / CHARACTERIZE / STOP**

—can be represented through explicit data structures and decision logic. And once that happens, a new type of data begins to remain—data that used to disappear.

**Why was that experiment run at that moment?**

**Why was it repeated?**

**Why did we wait?**

**Why was the project stopped?**

Over time, this decision history may become one of the most important datasets for autonomous experimentation. The competitive advantage in future Materials R&D may not come simply from running more experiments.

**Choosing the right experiment at the right time.**

That is the problem the Experimental R&D Decision Engine is designed to address.

*The simulations presented here are intended as a proof-of-concept prototype to illustrate the potential value of a Decision Engine in experimental R&D.*
