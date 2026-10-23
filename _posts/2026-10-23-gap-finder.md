---
layout: post
title: "Gap Finder: A Tool That Finds What Scientific Papers Leave Out"
date: 2026-10-23
categories: AI for Materials
tags: Materials-Science, Perovskite-Solar-Cells, AI
description: "Building Gap Finder, a tool that identifies missing evidence and helps readers ask better questions about scientific claims."
---

**[Try Demo]({{ "/demo/gap-finder/" | relative_url }})**

## 1. Reading a Paper Is Not the Same as Evaluating a Technology

Thousands of scientific papers are published every day, but impressive research results do not necessarily mean a technology is ready for real-world applications.

For example, when a solar cell paper reports a power conversion efficiency above 25%, several important questions remain. How large was the device? Was the efficiency independently certified? How stable is the device under real operating conditions?

Without expertise in the field, it is easy to overlook these details.

This motivated me to build an AI tool that looks beyond **what a paper reports and identifies what it does not fully explain.**

## 2. Gap Finder: What Is Missing from This Paper?

Gap Finder is an AI tool that analyzes scientific claims and identifies missing or unclear information needed to evaluate research results.

For the first prototype, I focused on **perovskite solar cells**, a field I have worked in during my research.

Users can paste text or upload a PDF to receive four types of analysis:

- **Key Claim Summary:** Summarizes the paper's main findings and reported achievements.
- **12-Point Checklist:** Evaluates key metrics such as efficiency, device area, stability, and reproducibility, labeling each as `Found`, `Gap`, `Unclear`, or `Check SI`.
- **Expert Briefing:** Explains how the reported results compare with existing technologies and what they mean in practice.
- **Three Critical Questions:** Generates three important follow-up questions, along with explanations of why they matter.

The goal is not simply to summarize scientific papers. It is to **help people read them more critically and understand what questions to ask next.**

## 3. Limitations and Next Steps

This is still an early prototype, and there are important limitations.

LLMs can misinterpret information or generate inaccurate statements. Also, just because something is not reported in a paper does not necessarily mean the experiment was never performed.

For this reason, Gap Finder is designed to highlight areas that need further investigation rather than make final judgments about a technology.

My next steps are to test the tool on real scientific papers, compare its outputs with expert evaluations, and identify where it performs well and where it needs improvement.

While the current version focuses on perovskite solar cells, I would eventually like to explore applications in other materials science fields, including batteries and semiconductors.

---

> **Can AI go beyond summarizing scientific papers to critically examine research claims and help us ask better questions?**

Gap Finder is my first attempt to explore that question.
