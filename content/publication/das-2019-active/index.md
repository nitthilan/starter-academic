---
# Documentation: https://wowchemy.com/docs/managing-content/

title: 'Active Anomaly Detection via Ensembles: Insights, Algorithms, and Interpretability'
subtitle: ''
summary: ''
authors:
- Shubhomoy Das
- Md Rakibul Islam
- Nitthilan Kannappan Jayakodi
- Janardhan Rao Doppa
tags: []
categories: []
date: '2019-01-01'
lastmod: 2020-10-20T19:56:08-07:00
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
publishDate: '2020-10-21T02:56:08.523497Z'
publication_types:
- '2'
abstract: 'Anomaly detection (AD) task corresponds to identifying the true anomalies from a given set of data instances. AD algorithms score the data instances and produce a ranked list of candidate anomalies, which are then analyzed by a human to discover the true anomalies. However, this process can be laborious for the human analyst when the number of false-positives is very high. Therefore, in many real-world AD applications including computer security and fraud prevention, the anomaly detector must be configurable by the human analyst to minimize the effort on false positives.
In this paper, we study the problem of active learning to automatically tune ensemble of anomaly detectors to maximize the number of true anomalies discovered. We make four main contributions towards this goal. First, we present an important insight that explains the practical successes of AD ensembles and how ensembles are naturally suited for active learning. Second, we present several algorithms for active learning with tree-based AD ensembles. These algorithms help us to improve the diversity of discovered anomalies, generate rule sets for improved interpretability of anomalous instances, and adapt to streaming data settings in a principled manner. Third, we present a novel algorithm called GLocalized Anomaly Detection (GLAD) for active learning with generic AD ensembles. GLAD allows end-users to retain the use of simple and understandable global anomaly detectors by automatically learning their local relevance to specific data instances using label feedback. Fourth, we present extensive experiments to evaluate our insights and algorithms. Our results show that in addition to discovering significantly more anomalies than state-of-the-art unsupervised baselines, our active learning algorithms under the streaming-data setup are competitive with the batch setup.'
publication: '*arXiv preprint arXiv:1901.08930*'
url_pdf: https://arxiv.org/pdf/1901.08930.pdf
---
