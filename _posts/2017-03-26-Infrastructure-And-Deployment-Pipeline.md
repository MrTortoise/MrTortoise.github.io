---
layout: post
title: "Infrastructure and Deployment: Problem and Goals"
date: 2017-03-26 21:27:48 +0000
categories: docker deployment kubernetes
---

## What is the problem?

1. Need Fast Deployment process
2. Need all environments to be as close to live as possible.
3. Goal is to be able to go live on a push and automate all dev->qa->live with a single button press
4. Need to be able continually evaluate and change live deployment configuration.
5. Needs to have a controlled monthly cost.
6. Need good logging for evidence based deployment decisions.
7. When all goes wrong need to be able to revert to earlier version ASAP.

## Pie In Sky Goals

1. 5 minutes to deploy (This is in addition to building / cooking assets etc.).
  - If whole process starts to take more than 10 minutes then it seriously effects iteration speed.
  - When something breaks the ideal is to have a pipeline that allows fixing it and deploying rather
  rather than spend time scrambling to recover and then fixing it.
2. Blue - Green deployments.
2. Cost is a real issue, building up in a way that greatly limits cost initially, expands organically.
  - This will mean being v clear about redundancy vs resiliency.
  - Focus on discovering requirements on one machine, diminishing returns with load.
3. Dev and QA environments basically being the same as live.
4. Clarity surrounding resources available for redundancy and simply redundant resources.


## Initial thoughts:

1. Windows is both expensive and due to image sizes slow to deploy.
  - This makes .net a less than ideal choice (core and standard libraries
  volatile - been burnt by mono in the past and about to be superseded by core)
2. Using framework choices that are both efficient, license minimal seems v prudent.
3. This has led me straight into thinking about language choices and CI options -
which is exactly what i wanted to avoid any decisions on.

### kubernetes

[services](https://kubernetes.io/docs/concepts/services-networking/connect-applications-service/) seem to give me what I want.
More to come
