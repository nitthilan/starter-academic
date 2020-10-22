---
# Documentation: https://wowchemy.com/docs/managing-content/

title: Active anomaly detection via ensembles
subtitle: ''
summary: ''
authors:
- Shubhomoy Das
- Md Rakibul Islam
- Nitthilan Kannappan Jayakodi
- Janardhan Rao Doppa
tags: []
categories: []
date: '2018-01-01'
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
publishDate: '2020-10-21T02:56:08.304898Z'
publication_types:
- '2'
abstract: 'In critical applications of anomaly detection including computer security and fraud prevention, the anomaly detector must be configurable by the analyst to minimize the effort on false positives. One important way to configure the anomaly detector is by providing true labels for a few instances. We study the problem of label-efficient active learning to automatically tune anomaly detection ensembles and make four main contributions. First, we present an important insight into how anomaly detector ensembles are naturally suited for active learning. This insight allows us to relate the greedy querying strategy to uncertainty sampling, with implications for label-efficiency. Second, we present a novel formalism called compact description to describe the discovered anomalies and show that it can also be employed to improve the diversity of the instances presented to the analyst without loss in the anomaly discovery rate. Third, we present a novel data drift detection algorithm that not only detects the drift robustly, but also allows us to take corrective actions to adapt the detector in a principled manner. Fourth, we present extensive experiments to evaluate our insights and algorithms in both batch and streaming settings. Our results show that in addition to discovering significantly more anomalies than state-of-the-art unsupervised baselines, our active learning algorithms under the streaming-data setup are competitive with the batch setup.'
publication: '*arXiv preprint arXiv:1809.06477*'
url_pdf: https://arxiv.org/pdf/1809.06477.pdf
---
