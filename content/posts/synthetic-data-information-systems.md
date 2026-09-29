---
title: "Why Synthetic Data Matters for Information Systems Research"
date: 2026-09-27T09:30:00-02:30
lastmod: 2026-09-27T09:30:00-02:30
draft: false
description: "Synthetic and LLM-generated data are reshaping how information systems researchers design and evaluate artifacts. Here's why that matters."
summary: "Synthetic data is becoming a design material for information systems research, not just a privacy workaround."
categories: ["Research"]
tags: ["Synthetic Data", "LLM", "Information Systems", "Design Science"]
images: ["images/og-default.svg"]
toc: true
---

People used to treat synthetic data as a privacy-preserving substitute for real data. It let them share similar datasets without exposing sensitive records. That's no longer enough.

## From substitute to design material

Large language models can generate data beyond an existing dataset's distribution. They condition, constrain, and shape that data to test new hypotheses. Real-world data rarely offers this flexibility.

In design science terms, synthetic data is becoming a **design material**, not just a stand-in for the real thing. Researchers actively shape it while building and evaluating an artifact.

## Why information systems researchers should care

A few reasons this matters for IS research specifically:

1. **Conceptual modeling at scale.** Generating synthetic data forces us to state our assumptions clearly. We must specify which entities, relationships, and constraints we take as true. Conceptual modeling research has always demanded this rigor.
2. **Evaluation under scarcity.** Many IS phenomena are hard to study: their data is rare, sensitive, or expensive to collect. Synthetic data lets us stress-test artifacts against edge cases we'd otherwise never observe.
3. **Trust and explainability.** If a system's training or evaluation data is partly synthetic, users and auditors need to know how it was generated. That need pulls synthetic data into explainable AI territory.

## Open questions

This is still an early and somewhat unsettled area. Some questions I'm actively working through:

- How do we validate that LLM-generated data preserves the conceptual structure of the phenomenon it's meant to represent?
- What does "ground truth" even mean when the data itself is generated?
- How should design science evaluation criteria change when the artifact and its evaluation data are both partly synthetic?

I'll write more as these ideas develop.

