---
# Documentation: https://wowchemy.com/docs/managing-content/

title: Design and Optimization of Energy-Accuracy Tradeoff Networks for Mobile Platforms
  via Pretrained Deep Models
subtitle: ''
summary: ''
authors:
- Nitthilan Kanappan Jayakodi
- Syrine Belakaria
- Aryan Deshwal
- Janardhan Rao Doppa
tags: []
categories: []
date: '2020-01-01'
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
publishDate: '2020-10-21T02:56:08.943332Z'
publication_types:
- '2'
abstract: 'Many real-world edge applications including object detection, robotics, and smart health are enabled by deploying deep neural networks (DNNs) on energy-constrained mobile platforms. In this article, we propose a novel approach to trade off energy and accuracy of inference at runtime using a design space called Learning Energy Accuracy Tradeoff Networks (LEANets). The key idea behind LEANets is to design classifiers of increasing complexity using pretrained DNNs to perform input-specific adaptive inference. The accuracy and energy consumption of the adaptive inference scheme depends on a set of thresholds, one for each classifier. To determine the set of threshold vectors to achieve different energy and accuracy tradeoffs, we propose a novel multiobjective optimization approach. We can select the appropriate threshold vector at runtime based on the desired tradeoff. We perform experiments on multiple pretrained DNNs including ConvNet, VGG-16, and MobileNet using diverse image classification datasets. Our results show that we get up to a 50% gain in energy for negligible loss in accuracy, and optimized LEANets achieve significantly better energy and accuracy tradeoff when compared to a state-of-the-art method referred to as Slimmable neural networks.'
publication: '*ACM Transactions on Embedded Computing Systems (TECS)*'
url_code: https://github.com/nitthilan/ml_tutorials
url_pdf: https://dl.acm.org/doi/pdf/10.1145/3366636
---
