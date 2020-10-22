---
# Documentation: https://wowchemy.com/docs/managing-content/

title: 'Trading-off accuracy and energy of deep inference on embedded systems: A co-design
  approach'
subtitle: ''
summary: ''
authors:
- Nitthilan Kannappan Jayakodi
- Anwesha Chatterjee
- Wonje Choi
- Janardhan Rao Doppa
- Partha Pratim Pande
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
publishDate: '2020-10-21T02:56:08.017270Z'
publication_types:
- '2'
abstract: 'Deep neural networks have seen tremendous success for different modalities of data including images, videos, and speech. This success has led to their deployment in mobile and embedded systems for real-time applications. However, making repeated inferences using deep networks on embedded systems poses significant challenges due to constrained resources (e.g., energy and computing power). To address these challenges, we develop a principled co-design approach. Building on prior work, we develop a formalism referred to as Coarse-to-Fine Networks (C2F Nets) that allow us to employ classifiers of varying complexity to make predictions. We propose a principled optimization algorithm to automatically configure C2F Nets for a specified trade-off between accuracy and energy consumption for inference. The key idea is to select a classifier on-the-fly whose complexity is proportional to the hardness of the input example: simple classifiers for easy inputs and complex classifiers for hard inputs. We perform comprehensive experimental evaluation using four different C2F Net architectures on multiple real-world image classification tasks. Our results show that optimized C2F Net can reduce the Energy Delay Product (EDP) by 27 to 60 percent with no loss in accuracy when compared to the baseline solution, where all predictions are made using the most complex classifier in C2F Net.'
publication: '*IEEE Transactions on Computer-Aided Design of Integrated Circuits and
  Systems*'
url_code: https://github.com/nitthilan/ml_tutorials
url_pdf: https://arxiv.org/pdf/1901.10584.pdf
---
