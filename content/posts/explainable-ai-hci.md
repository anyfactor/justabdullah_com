---
title: "Notes on Explainable AI in HCI Contexts"
date: 2026-09-27T10:00:00-02:30
lastmod: 2026-09-27T10:00:00-02:30
draft: false
description: "Explainability is a human-computer interaction problem, not just a model property. Some notes on viewing XAI through an HCI lens."
summary: "Explainable AI research often stops at the model. HCI pushes us to ask whether an explanation helps the person who receives it."
categories: ["Research"]
tags: ["Explainable AI", "HCI"]
images: ["images/og-default.svg"]
toc: true
---

Much explainable AI (XAI) work treats explainability as a model property: feature importances, saliency maps, counterfactuals. These are useful. But they miss the real question: does the explanation help someone decide better?

## The gap between "explainable" and "understood"

An explanation that's technically correct can still fail if:

- it assumes a level of statistical literacy the user doesn't have,
- it's delivered at the wrong point in the user's workflow, or
- it answers a question the user isn't asking.

This is where HCI earns its keep. The discipline offers decades of methods for this: mental models, task analysis, usability evaluation. Mainstream XAI research has absorbed almost none of it.

## A question I keep asking

Instead of asking *"is this model explainable?"*, I ask a different question: does this explanation change what the user does? Does it change it for the better? That question treats explainability as an interaction outcome, not a fixed model trait. It also lets us borrow evaluation methods from HCI, not invent new ones from scratch.

## Where this is headed

I want conceptual frameworks that help researchers plan ahead. A framework should specify what an explanation must accomplish for a given user and task. Only then should we choose a model-side technique. More on this as the framework takes shape.

