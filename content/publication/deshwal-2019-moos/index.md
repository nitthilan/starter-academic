---
# Documentation: https://wowchemy.com/docs/managing-content/

title: 'MOOS: A multi-objective design space exploration and optimization framework
  for NoC enabled manycore systems'
subtitle: ''
summary: ''
authors:
- Aryan Deshwal
- Nitthilan Kanappan Jayakodi
- Biresh Kumar Joardar
- Janardhan Rao Doppa
- Partha Pratim Pande
tags: []
categories: []
date: '2019-01-01'
lastmod: 2020-10-20T19:56:09-07:00
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
publishDate: '2020-10-21T02:56:09.562376Z'
publication_types:
- '2'
abstract: 'The growing needs of emerging applications has posed significant challenges for the design of optimized manycore systems. Network-on-Chip (NoC) enables the integration of a large number of processing elements (PEs) in a single die. To design optimized manycore systems, we need to establish suitable trade-offs among multiple objectives including power, performance, and thermal. Therefore, we consider multi-objective design space exploration (MO-DSE) problems arising in the design of NoC-enabled manycore systems: placement of PEs and communication links to optimize two or more objectives (e.g., latency, energy, and throughput). Existing algorithms to solve MO-DSE problems suffer from scalability and accuracy challenges as size of the design space and the number of objectives grow. In this paper, we propose a novel framework referred as Multi-Objective Optimistic Search (MOOS) that performs adaptive design space exploration using a data-driven model to improve the speed and accuracy of multi-objective design optimization process. We apply MOOS to design both 3D heterogeneous and homogeneous manycore systems using Rodinia, PARSEC, and SPLASH2 benchmark suites. We demonstrate that MOOS improves the speed of finding solutions compared to state-of-the-art methods by up to 13X while uncovering designs that are up to 20% better in terms of NoC. The optimized 3D manycore systems improve the EDP up to 38% when compared to 3D mesh-based designs optimized for the placement of PEs.'
publication: '*ACM Transactions on Embedded Computing Systems (TECS)*'
url_pdf: https://dl.acm.org/doi/pdf/10.1145/3358206
---
