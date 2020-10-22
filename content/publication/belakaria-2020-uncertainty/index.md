---
# Documentation: https://wowchemy.com/docs/managing-content/

title: Uncertainty-Aware Search Framework for Multi-Objective Bayesian Optimization.
subtitle: ''
summary: ''
authors:
- Syrine Belakaria
- Aryan Deshwal
- Nitthilan Kannappan Jayakodi
- Janardhan Rao Doppa
tags: []
categories: []
date: '2020-01-01'
lastmod: 2020-10-20T19:56:10-07:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ''
  focal_point: ''
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
publishDate: '2020-10-21T02:56:09.853848Z'
publication_types:
- '1'
abstract: 'We consider the problem of constrained multi-objective (MO) blackbox optimization using expensive function evaluations, where the goal is to approximate the true Pareto set of solutions satisfying a set of constraints while minimizing the number of function evaluations. We propose a novel framework named Uncertainty-aware Search framework for Multi-Objective Optimization with Constraints (USeMOC) to efficiently select the sequence of inputs for evaluation to solve this problem. The selection method of USeMOC consists of solving a cheap constrained MO optimization problem via surrogate models of the true functions to identify the most promising candidates and picking the best candidate based on a measure of uncertainty. We applied this framework to optimize the design of a multi-output switched-capacitor voltage regulator via expensive simulations. Our experimental results show that USeMOC is able to achieve more than 90 % reduction in the number of simulations needed to uncover optimized circuits.'
publication: '*AAAI*'
url_pdf: https://arxiv.org/pdf/2008.07029.pdf
#url_code: "http"
#url_doi: "hi"
---
