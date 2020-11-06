---
title: AI Resources (Under Development)
# View.
#   1 = List
#   2 = Compact
#   3 = Card
#   4 = Citation
view: 4

# Optional header image (relative to `static/media/` folder).
header:
  caption: ""
  image: ""
---

###### Sections       
[About](#about) - [Significant Areas](#significant-areas)-[Current Task List](#current-task-list) - [Tutorials](#tutorials) - [Applications](#applications) - [Prominent Papers](#prominent-papers)

###### About
Inspired from Pixar, Dreamworks, Sony and other animation studios. The general time required to produce an animated feature from conception to final rendered version has a long production time. 
Can Artificial Intelligence based solutions help in reducing this time line? 

The current advancements in deep learning in the area of GAN, Neural Rendering help to automate many processes like creating 3D models, animating 3d model motion. 

Project Ideas : [Multi view based 3D models](#multi-view-based-3d-models) - Virtual Studio - Human Models

###### Multi view based 3D models
- AI Sculptor: Assuming the rays as a nail, we like to sculpt a 3D model based on multiple input views. We use the NSVF as our based code. The list of problems we are planning to attack:
	- Using PSNR or SSIM to identify areas in the learnt model which are not properly learnt and using this guide the rays to be used for learning. 
		- Create a weigting map of the areas which are lacking detail
		- Sample rays based on this weighting map within a picture
		- Sample rays based on weighting map of all the pictures
		- Split voxels adaptively based on the PSNR and SSIM distribution
	- Progressively learning model using smaller images and gradually increasing the image dimension as we increase the model accuracy. The aim is to reduce the training time of the 3D model.
		- Estimating the bounding box automatically based on the camera position
		- Use images from smaller size along widthxheight probably rations 2,4,8
		- Select a small subset of camera postions to start with and gradually increase with iterations
		- Allocate initial voxel size based on all the camera postions and interpixel ray distance and then as the image dimensions increase the voxel size would decrease accordingly
	- Culling Voxels - This reduces the number voxels used for representing the object. This helps in reduction of the memory .Voxels in the bounding box which are not touched by the rays. Two major regions 
		- Voxels inside the object which are not reached by the rays
		- Voxels outside the object region which are not touched by the training rays
- NeRF in Motion: Encoding motion for objects in a neural scene. There are diffferent ideas for it.
	- NSVF uses Hyper networks to encode every network encode for each time step. [SRN](https://arxiv.org/pdf/1906.01618.pdf)
	- Like mesh objects, can Bones, rigging and weighting be added for the objects thereby making it configurable [Bone structure](https://www.peachpit.com/articles/article.aspx?p=483793), [Blog](https://blog.machinimatrix.org/avastar/features/rigging-and-weighting/3/), 
- Few Shot Learning:
	- Understanding GPT3: [Paper](https://arxiv.org/pdf/2005.14165.pdf), [GPT2 Blog](https://openai.com/blog/better-language-models/), [GPT2 Paper](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf), [Youtube](https://www.youtube.com/watch?v=_8yVOC4ciXc&ab_channel=Computerphile), [Youtube2](https://www.youtube.com/watch?v=SY5PvZrJhLE&ab_channel=YannicKilcher), 
	- Transformers for 3d model - [Perspective Transformer Nets](https://papers.nips.cc/paper/6206-perspective-transformer-nets-learning-single-view-3d-object-reconstruction-without-3d-supervision.pdf), [Set Transformer](http://proceedings.mlr.press/v97/lee19d/lee19d.pdf), [Spatial Transformer for 3D Point Clouds](https://arxiv.org/pdf/1906.10887.pdf)
- Active learning for 3d object reconstruction
- Structure from motion using deep learning: [Turntable](https://www.robots.ox.ac.uk/~vgg/publications/1998/Fitzgibbon98a/fitzgibbon98a.pdf)
	- Can NeRF be modeled to run without the camera parameters? Since we are modelling the neural network as a funtioin of x,y,z can we learn using SGD the model without the camera parameters?
	- Fix one camera position. Model the 3D model as function of relative camera parrameter. Try minimising the error of images while we learn the error from different projections

###### Significant Areas
- Bayesian Optimzation based GAN latent variable search
- Bayesian Neural network based BO 
- StyleGAN
- Camera pose estimate
- Fourier feature networks
- Photogrammetry - [software](https://all3dp.com/1/best-photogrammetry-software/)
- Part segmentation
- HairNet
- Sculpting
- SMPL
- Image Harmonization
- Pose Transfer
- Multi-view rendering
- HyperNetworks
- Continous Learning - [Iman](https://imirzadeh.me/#contact), [paper](https://arxiv.org/pdf/2006.06958.pdf), [Review Paper](https://www.sciencedirect.com/science/article/pii/S0893608019300231), [Tackling catastropic forgetting](https://arxiv.org/pdf/2007.00487.pdf), [Incremental learning](https://arxiv.org/pdf/2004.00713.pdf)
- [3D Machine Learning Github](https://github.com/timzhang642/3D-Machine-Learning)

###### Prominent Papers
- NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis: [paper](https://arxiv.org/pdf/2003.08934.pdf), [code](https://github.com/kwea123/nerf_pl), [mesh reconstruction](https://github.com/kwea123/nerf_pl/blob/master/README_mesh.md), [color reproduction](https://github.com/bmild/nerf/issues/44), [PyMcubes](https://github.com/pmneila/PyMCubes)
- Neural Sparse Voxel Fields: [paper](https://arxiv.org/pdf/2007.11571.pdf)
- Fourier Features Let Networks Learn High Frequency Functions in Low Dimensional Domains: [paper](https://arxiv.org/pdf/2006.10739.pdf)
- Generating Diverse High-Fidelity Images with VQ-VAE-2: [paper](https://arxiv.org/pdf/1906.00446.pdf)
- NeRF in the Wild: Neural Radiance Fields for Unconstrained Photo Collections: [paper](https://arxiv.org/pdf/2008.02268.pdf)
- Neural Rendering: [project](https://github.com/weihaox/awesome-neural-rendering)
- Nerf++: [Code](https://github.com/Kai-46/nerfplusplus)

###### To Be Read Papers
- [Interactive Video StylizationInteractive Video Stylization](https://ondrejtexler.github.io/patch-based_training/), [Resolution Dependent GAN](https://arxiv.org/pdf/2010.05334.pdf), [Video Completion](http://chengao.vision/FGVC/),[Latent Space of Generative Networks](https://arxiv.org/pdf/1707.05776.pdf), [Bayesian Deep Learning for Computer Vision](https://arxiv.org/pdf/1703.04977.pdf), [Real Image Editing GAN](https://genforce.github.io/idinvert/), [Rewriting a Deep Generative Model](https://rewriting.csail.mit.edu/)
- Softwares: [AI Vdo](https://www.synthesia.io/), [CineTracer](https://www.cinetracer.com/),[GPU Sharing](https://vast.ai/),[SpyFU](https://www.spyfu.com/), [OBS Studio](https://obsproject.com/)

###### Current Task List
-

###### Tutorials
- GAN basics,
- Running models on GPU
- Framework - Pytorch, Keras, numpy, Pytorch3D
- AlphaZero, 
- CPISADGAN
- BO
- [MultiView Geometry](https://github.com/DeepRobot2020/books/blob/master/Multiple%20View%20Geometry%20in%20Computer%20Vision%20(Second%20Edition).pdf), [Camera Basics](http://ksimek.github.io/2012/08/14/decompose/), [Rotation Matrix](https://mathworld.wolfram.com/RotationMatrix.html), [Projective, Affine, Euclidean Geometry](http://robotics.stanford.edu/~birch/projective/node2.html), [NDC Co-ordinate Systems](https://learnopengl.com/Getting-started/Coordinate-Systems)

###### Applications

###### Graphics related
- [Omniverse](https://www.nvidia.com/en-us/design-visualization/omniverse/), [Signed Distance Field Collision](https://mmacklin.com/sdfcontact.pdf), [Specular Manifold Sampling](http://rgl.epfl.ch/publications/Zeltner2020Specular), [Detailed Rigid Body Simulation](https://matthias-research.github.io/pages/publications/PBDBodies.pdf)


### Sections       
[Children resources](#children-resources) - [Videos](#videos) - [Accelerators](#accelerators) - [Channels followed](#channels-followed) - [GPU and CUDA resource](#gpu-and-cuda-resource) - [Projects](#projects)

###### Tutorials
- [AI pay grades](https://aipaygrad.es/)

###### Children resources

- [ecraft2learn](https://ecraft2learn.github.io/ai/)
- [mit](https://www.media.mit.edu/posts/kids-ai-devices/)
- [machinelearningforkids](https://machinelearningforkids.co.uk/#!/links#top)

###### Videos

- [Heroes of Deep Learning: Andrew Ng interviews Pieter Abbeel](https://www.youtube.com/watch?v=dmkPJpWCVcI)
- [Deepmind opensources starcraft II ai](https://www.youtube.com/watch?v=St5lxIxYGkI)
- [OpenAI bots beats DOTA Worl champion](https://www.youtube.com/watch?v=cLC_GHZCOVQ)
- [Deepmind and UCL course work](https://www.youtube.com/watch?v=_aUq7lmMfxo)


###### List of topics to be covered

###### Good resources  

- [Sutton Book](http://incompleteideas.net/sutton/book/the-book-2nd.html): [Book Draft](http://incompleteideas.net/sutton/book/bookdraft2016sep.pdf), [Code And Examples](https://github.com/ShangtongZhang/reinforcement-learning-an-introduction)
- [Deep Mind: RL Course by David Silver](https://www.youtube.com/watch?v=2pWv7GOvuf0) - First of a 10 lecture series - <http://www0.cs.ucl.ac.uk/staff/d.silver/web/Teaching.html>
 


###### Accelerators

- [betalist](https://betalist.com/)
- [angel](https://angel.co/)
- [crunchbase](https://www.crunchbase.com/)
- [producthunt](https://www.producthunt.com/)
- [startupschool](https://www.startupschool.org/)
- [disneyaccelerator](https://disneyaccelerator.com/)

###### Job Options

- [E3](https://e3expo.com/)
- [CVPR](http://cvpr2020.thecvf.com/jobs)
- [Siggraph](https://s2020.siggraph.org/)
- [cartoon network animation expo](https://www.ctnanimationexpo.com/index.php)

###### Internships
- Studio list - Pixar, nickelodean, laika, dreamworks, bluesky, warner brothers, cartoon network, Blizzard
- [How to get a pixar internship](https://www.youtube.com/watch?v=44DdiybwJ8c)
- [Animation colleges](https://www.animationcareerreview.com/articles/walt-disney-animation-studios-career-profile#:~:text=According%20to%20the%20company%20website,Maya%20or%20a%20similar%20program.) - [conceptdesignacad](http://conceptdesignacad.com/)
- [How to get a job at Blizzard](https://www.youtube.com/watch?v=dY-Ts69F4Xo)


###### Portfolio creation
- [DevianArt](https://www.deviantart.com/), Instagram, YouTube
- List of inspiring artists: bobby pontillas, rafael grassetti [human anatomy](https://gumroad.com/grassettiart), [youtube](https://www.youtube.com/watch?v=VmUikhiWu8c), Laura Price [MY ART JOURNEY](https://www.youtube.com/watch?v=lfZ8HKUhxak), [Michael Vicente](https://www.youtube.com/watch?v=dY-Ts69F4Xo), [Ross draws](https://www.youtube.com/channel/UCLEVrhumRsK67JkP3G4w5cQ/videos)
- [Polycount](https://polycount.com/forum), [zbrush central](https://www.zbrushcentral.com/t/gallery/227023), [artstation](https://www.artstation.com/)
- Books - [Composing Pictures](https://www.amazon.com/dp/B00LKL6Q3S/ref=dp-kindle-redirect?_encoding=UTF8&btkr=1), [illusion of life](https://www.amazon.com/Illusion-Life-Disney-Animation/dp/0786860707), [Animators survival kit](https://www.amazon.com/Animators-Survival-Kit-Expanded-Principles/dp/0571238343)

###### Channels followed

- [DeepAI: The front page of A.I.](https://deepai.org/)
- [Made With ML](https://madewithml.com/)


###### GPU and CUDA resource

- [AWS](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/accelerated-computing-instances.html): 
	- p2 - NVIDIA Tesla K80 - 2 x 2496
	- G3 - NVIDIA Tesla M60 - 4096 NVIDIA CUDA® cores (2048 per GPU)
	- G2 - NVIDIA GRID K520 GPUs - 3072 core
	- CG1 -  NVIDIA Tesla M2050

- [NVIDIA Grant](https://developer.nvidia.com/academic_gpu_seeding)
	- NVIDIA Quadro M5000 - 2048 [GeForce Titan Xp, Quadro P5000, NVIDIA M5000 specification]
	- [GTX 1080i](https://www.nvidia.com/en-us/geforce/products/10series/geforce-gtx-1080-ti/) - 3584 - 700$
	- GTX 1080 - 2,560 - 500$
	- GTX 1070 - 1920 - 390
	- Titan X pascal - 3584
	- [Jetson](https://www.phoronix.com/scan.php?page=article&item=jetson-tegra-x2&num=1)
- EGPU: [egpu](https://egpu.io/), [9to5mac](https://9to5mac.com/2017/04/11/hands-on-powering-the-macbook-pro-with-an-egpu-using-nvidias-new-pascal-drivers/)

