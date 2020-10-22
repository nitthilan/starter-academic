---
# Documentation: https://wowchemy.com/docs/managing-content/

title: 'PETNet: Polycount and Energy Trade-off Deep Networks for Producing 3D Objects
  from Images'
subtitle: ''
summary: ''
authors:
- Nitthilan Kanappan Jayakodi
- Janardhan Rao Doppa
- Partha Pratim Pande
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
publishDate: '2020-10-21T02:56:10.466362Z'
publication_types:
- '1'
abstract: 'We consider the task of predicting 3D object shapes from color images on mobile platforms, which has many real-world applications including augmented reality (AR), virtual reality (VR), and robotics. Recent work has developed a Graph Convolution Network (GCN) based approach to produce 3D object shapes in the form of a triangular mesh of increasing polycount (no. of triangles in the mesh). In this paper, we propose a novel approach to trade-off polycount of a 3D object shape for the energy consumed at run-time called Polycount-Energy Trade-off networks (PETNet). The key idea behind PETNets is to design an architecture of increasing complexity with a comparator module and leveraging the pre-trained GCN to perform input-specific adaptive predictions. We perform experiments using pre-trained GCN on the ShapeNet dataset. Results show that with the optimized PETNets, we can get up to 20%-37% gain in energy for negligible loss (0.01 to 0.02) in accuracy, and provides a fine-grained control on performance when compared to a fixed level performance with the state-of-the-art Pixel2Mesh network.'
publication: '*2020 57th ACM/IEEE Design Automation Conference (DAC)*'
url_pdf: https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9218525https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9218525

---
