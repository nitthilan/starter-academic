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
- Neural Fields Rendering System: 
Requirements:
	- Store objects as neural network 
		- It could be a single neural network for each object
		- multiple obejcts encoded in the same network using embedding as input.
		- Store embeedding for each voxel and a common neural network. A generalized marching cubes algorithm. 
		- A hybrid progressive representation
			- A global embedding for overall structure and progressive embedding for successive voxel breaking to refine the shape to increased quality
			- DeepLS, SDF (It has a different embedding compared to NSVF). It tried to learn NN to learn smaller edges. Heirarchical NeRF -> NSVF
		- Can transformer networks be used instead of NN?
	- Learning material properties: [Nerf Issues](https://github.com/bmild/nerf/issues/23)
		- Looks like there is a solution which uses Albedo and Illumination in CVPR. Environment maps are used to replicate theillumination problem
		- Light could be used as a dot product i.e. a NN which takes the direction of light, direction of incident ray and material properties at that point and produces the output at that point
	- 

##### Current Task List
- Modify NSVF - embedding and voxel culling
- Modify NeRF - to support SDF experiments, add support of embedding for individual shape using DeepSDF idea

##### List of ideas:
- SDF helps in physics based simulations i.e. they help in contact detection between objects and hence in object object touching etc - so may help in hair, cloth simulations
	- Experiment with Occupancy and SDF variations
- Can we split objects into separate objects which and then join them together later [Graffe paper]. Create a system which can align objects as different poses and translation and camera pose
- Use Nerf++ to encode forground and background object
- NeRF for Human shapes: Fashion related human modeling design and animation. 
	- Garment Hair 3D geometry and charater animation.
	- Nerf setup for hair and cloth simulation. Interpreenetation of hair strands into head and sholder
- Learn a prior using NeRF and learn embeddings using a single input image [PiFU]. 
	- Used trained NN and extract embeddings based on input image. Heirarchical NerF -> NSVF
- Can Embedding be learnt for different parts like face, hands clothers. Can we use Pose as input - CPIGAN
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
- 
- NeRF in Motion: Encoding motion for objects in a neural scene. There are diffferent ideas for it.
	- Datasets: [D-NeRF: Neural Radiance Fields for Dynamic Scenes](https://arxiv.org/pdf/2011.13961.pdf) - Extends the dataset of NERF to dynamics, [RigNET](https://zhan-xu.github.io/rig-net/), [People Snapshot Dataset](https://graphics.tu-bs.de/people-snapshot) - [Video Based Reconstruction of 3D People Models](http://gvv.mpi-inf.mpg.de/projects/wxu/VideoAvatar/content/video_shapes.pdf), [BUFF: Bodies Under Flowing Fashion](http://buff.is.tue.mpg.de/) - [Detailed, accurate, human shape estimation from clothed {3D} scan sequences](https://ps.is.tuebingen.mpg.de/publications/shape_under_cloth-cvpr17), [PiFuHD](https://arxiv.org/pdf/2004.00452.pdf) - [renderpeople](https://renderpeople.com/free-3d-people/), [HDRI Haven](https://hdrihaven.com/), [cape](https://cape.is.tue.mpg.de/downloads), [code](https://github.com/QianliM/CAPE), [utils](https://github.com/QianliM/cape_utils/)
	- Using normalized coordinate system i.e. map actual values to normalised value to then learn a warping function which adds on to it and then render it f(X(x), Y(y), Z(z)). Maps (x,y,z) for each time step. Learn how bones are mapped to mesh pixels. Find the transformation function) - Motion Capture based rendering system
		- [Deformable Neural Radiance Fields](https://arxiv.org/pdf/2011.12948.pdf)
		- [Space-time Neural Irradiance Fields for Free-Viewpoint Video](https://arxiv.org/pdf/2011.12950.pdf)
		- [Neural Radiance Flow for 4D View Synthesis and Video Processing](https://arxiv.org/pdf/2012.09790.pdf)
		- [Deformable Neural Radiance Fields](https://storage.googleapis.com/nerfies-public/videos/nerfies_paper.pdf) - [project](https://nerfies.github.io/)
		- [D-NeRF: Neural Radiance Fields for Dynamic Scenes](https://arxiv.org/pdf/2011.13961.pdf)
		- [DeRF: Decomposed Radiance Fields](https://arxiv.org/pdf/2011.12490.pdf)
	- NSVF uses Hyper networks to encode every network encode for each time step. [SRN](https://arxiv.org/pdf/1906.01618.pdf)
	- Like mesh objects, can Bones, rigging and weighting be added for the objects thereby making it configurable [Bone structure](https://www.peachpit.com/articles/article.aspx?p=483793), [Blog](https://blog.machinimatrix.org/avastar/features/rigging-and-weighting/3/), 
- Embedding or Latent variable to control different aspects of a 3D generation
	- Shape is encoded as a latent vector and then a shape with the (xyz) is used for predicting shape - [ShaRF: Shape-conditioned Radiance Fields from a Single View](https://arxiv.org/pdf/2102.08860.pdf), 
	- Conditioned on the image the generate embedding for each voxel which could be used as input along with xyz - [pixelNeRF: Neural Radiance Fields from One or Few Images](https://arxiv.org/pdf/2012.02190.pdf) - [Code](https://github.com/sxyu/pixel-nerf)
- Relighting of models:
	- [X-Fields: Implicit Neural View-, Light- and Time-Image Interpolation](http://xfields.mpi-inf.mpg.de/), [Deep Relightable Textures](http://gvv.mpi-inf.mpg.de/projects/DeepRelightableTextures/), [Deferred Neural Rendering: Image Synthesis using Neural Textures](https://arxiv.org/pdf/1904.12356.pdf)
- Few Shot Learning:
	- Learning priors using bayesian neural networks: [Uncertainity Quantification](https://en.wikipedia.org/wiki/Uncertainty_quantification), [Weight Uncertainity in NN](https://arxiv.org/abs/1505.05424), [Variational Inference in Bayesian NN](http://krasserm.github.io/2019/03/14/bayesian-neural-networks/) - The idea is to train priors of shapes using neural networks and then try to learn the representation using a single image input. The prior stores range of uncertainity in the variance of the weights and tries to find the right instance value using a single image input. We try to replace a NN in NeRF to a Baysian NN and try to model the uncertainity in shape as the weights of the bayesian-neural-networks
	- Understanding GPT3: [Paper](https://arxiv.org/pdf/2005.14165.pdf), [GPT2 Blog](https://openai.com/blog/better-language-models/), [GPT2 Paper](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf), [Youtube](https://www.youtube.com/watch?v=_8yVOC4ciXc&ab_channel=Computerphile), [Youtube2](https://www.youtube.com/watch?v=SY5PvZrJhLE&ab_channel=YannicKilcher), 
	- Transformers for 3d model - [Perspective Transformer Nets](https://papers.nips.cc/paper/6206-perspective-transformer-nets-learning-single-view-3d-object-reconstruction-without-3d-supervision.pdf), [Set Transformer](http://proceedings.mlr.press/v97/lee19d/lee19d.pdf), [Spatial Transformer for 3D Point Clouds](https://arxiv.org/pdf/1906.10887.pdf)
	- [Possible continous learning](https://leggedrobotics.github.io/rl-blindloco/)
- Active learning for 3d object reconstruction
- Structure from motion using deep learning: [Turntable](https://www.robots.ox.ac.uk/~vgg/publications/1998/Fitzgibbon98a/fitzgibbon98a.pdf)
	- Can NeRF be modeled to run without the camera parameters? Since we are modelling the neural network as a funtioin of x,y,z can we learn using SGD the model without the camera parameters?
	- Fix one camera position. Model the 3D model as function of relative camera parrameter. Try minimising the error of images while we learn the error from different projections.
- Splitting light, view and time and directly rendering 2D images - X-field - [paper](https://arxiv.org/pdf/2010.00450.pdf), [code](https://github.com/m-bemana/xfields)
- Compress 3D shape representation by using entries from a codebook like the idea in VQVAE - https://arxiv.org/pdf/1711.00937.pdf,

- Depth/Height map as implicit functions : 
	- Using a base template and encoding the shape as a structure over the template - [Learning Shape Templates with Structured Implicit Functions](https://openaccess.thecvf.com/content_ICCV_2019/papers/Genova_Learning_Shape_Templates_With_Structured_Implicit_Functions_ICCV_2019_paper.pdf), [code](https://github.com/google/ldif)
	- Human models: Converting 3d model to 2d surface plane - developable surface SMPL
		- [SMPL to UV mapping](https://github.com/facebookresearch/DensePose/issues/116), [UV map to SMPL model](https://github.com/Lotayou/densebody_pytorch/issues/41), [How to get UV coordinates for the template](https://github.com/CalciferZh/SMPL/issues/5)
	- [Fitting code](https://github.com/vchoutas/smplify-x/blob/master/smplifyx/fitting.py)
		- [Tutorial](https://medium.com/@apofeniaco/p3d-body-detection-with-smplify-x-ced6c38871df), [code sample](https://github.com/ortegatron/playing_smplifyx/tree/master/smplifyx)
		- [OpenPose](https://github.com/CMU-Perceptual-Computing-Lab/openpose)
		- [Converting from local to global](https://www.dropbox.com/scl/fi/zkatuv5shs8d4tlwr8ecc/Change-parameters-to-new-coordinate-system.paper?dl=0&rlkey=lotq1sh6wzkmyttisc05h0in0)
	- [Understanding SMPL](https://khanhha.github.io/posts/SMPL-model-introduction/), [SMPLX](https://github.com/vchoutas/smplx)
	- [Transfering between SMPL-SMPLX-SMPLH-FLAME-MANO](https://github.com/vchoutas/smplx/tree/master/transfer_model)
	- SMPL - [Papers](http://files.is.tue.mpg.de/black/papers/SMPL2015.pdf), [project](https://smpl.is.tue.mpg.de/) - SMPLX - [paper](https://ps.is.tuebingen.mpg.de/uploads_file/attachment/attachment/497/SMPL-X.pdf), [supp](https://ps.is.tuebingen.mpg.de/uploads_file/attachment/attachment/498/SMPL-X-supp.pdf), [project](https://smpl-x.is.tue.mpg.de/)
	- Face Fitting - [Flame fitting](https://github.com/Rubikplayer/flame-fitting), [FLAME](https://flame.is.tue.mpg.de/)
	- Approximating 3d shapes with blobs/ellipsoids - [project](https://github.com/google/ldif), [Local Deep Implicit Functions for 3D Shape](https://arxiv.org/pdf/1912.06126.pdf), [Learning Shape Templates with Structured Implicit Functions](https://openaccess.thecvf.com/content_ICCV_2019/papers/Genova_Learning_Shape_Templates_With_Structured_Implicit_Functions_ICCV_2019_paper.pdf)
- Online 3d models - Dataset - [Turbosquid](https://www.turbosquid.com/3d-model/chair), [sketchfab](https://sketchfab.com/tags/freemodel), [Pixologic, Zbrush](http://pixologic.com/turntable/?page=2)
- Synching two cameras - [libsoftwaresync](https://github.com/google-research/libsoftwaresync) - 
Code list:
- https://github.com/shunsukesaito/PIFu
- https://github.com/facebookresearch/pifuhd
- https://github.com/kwea123/nerf_pl
- https://github.com/facebookresearch/NSVF

Nerf Universe:
- Basic Nerf

- Ability to choose appropriate texture and material properties based on BRDF

###### Prominent Papers
- [Arxiv - Computer Vision](https://arxiv.org/list/cs.CV/pastweek?show=490)
- [Nerf - citations](https://scholar.google.com/scholar?cites=9378169911033868166&as_sdt=5,48&sciodt=0,48&hl=en)
- [NSVF - citations](https://scholar.google.com/scholar?cites=8122086353742917335&as_sdt=5,48&sciodt=0,48&hl=en)
- [NeRF Explosion 2020](https://dellaert.github.io/NeRF/)
- [Awesome NeRF](https://github.com/yenchenlin/awesome-NeRF)
- NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis: [paper](https://arxiv.org/pdf/2003.08934.pdf), [code](https://github.com/kwea123/nerf_pl), [mesh reconstruction](https://github.com/kwea123/nerf_pl/blob/master/README_mesh.md), [color reproduction](https://github.com/bmild/nerf/issues/44), [PyMcubes](https://github.com/pmneila/PyMCubes)
- Neural Sparse Voxel Fields: [paper](https://arxiv.org/pdf/2007.11571.pdf)
- Fourier Features Let Networks Learn High Frequency Functions in Low Dimensional Domains: [paper](https://arxiv.org/pdf/2006.10739.pdf)
- Generating Diverse High-Fidelity Images with VQ-VAE-2: [paper](https://arxiv.org/pdf/1906.00446.pdf)
- NeRF in the Wild: Neural Radiance Fields for Unconstrained Photo Collections: [paper](https://arxiv.org/pdf/2008.02268.pdf)
- Neural Rendering: [project](https://github.com/weihaox/awesome-neural-rendering)
- [Nerf++](https://github.com/Kai-46/nerfplusplus) - [paper](https://arxiv.org/pdf/2010.07492.pdf)
- [iNerf](https://arxiv.org/pdf/2102.07064.pdf), [Nerf--](https://arxiv.org/pdf/2102.07064.pdf)
- [FroDo](https://research.fb.com/wp-content/uploads/2020/05/FroDO-From-Detections-to-3D-Objects.pdf)
- [PIFuHD](https://arxiv.org/pdf/2004.00452.pdf)
- [PIFu](https://arxiv.org/pdf/1905.05172.pdf)
- [GIRAFFE: Representing Scenes as Compositional Generative Neural Feature Fields](https://arxiv.org/pdf/2011.12100.pdf)
	- [GRAF](http://www.cvlibs.net/publications/Schwarz2020NEURIPS.pdf) - [project](https://avg.is.tuebingen.mpg.de/publications/schwarz2020neurips) - [code](https://github.com/autonomousvision/graf)
- [Optimizing the Latent Space of Generative Networks](http://proceedings.mlr.press/v80/bojanowski18a/bojanowski18a.pdf)

- [SFM - Structure from motion](https://demuc.de/papers/schoenberger2016sfm.pdf)
	- [Pixelwise View Selection for Unstructured Multi-View Stereo](https://www.cs.unc.edu/~ezheng/resources/mvs_2016/eccv2016.pdf)
	- [COLMAP Documentation](https://colmap.github.io/tutorial.html) - [Dense Reconstruction - multi-view](https://colmap.github.io/faq.html#reconstruct-sparse-dense-model-from-known-camera-poses) - [FAQ](https://colmap.github.io/faq.html#)
	- Structure From Motion - [RANSAC](http://homepages.inf.ed.ac.uk/rbf/CVonline/LOCAL_COPIES/FISHER/RANSAC/), [RANSAC1](http://www.cse.yorku.ca/~kosta/CompVis_Notes/ransac.pdf), [five-point relative pose problem](https://www.rose-hulman.edu/class/cs/csse461/handouts/Day37/SINGLES2.pdf)
	- [tutorial](https://colmap.github.io/tutorial.html)
	- undistort images - making lines straight - usually lens causes distortion - [camera calibration](https://stackoverflow.com/questions/39530110/camera-calibration-for-structure-from-motion-with-opencv-python)
	- patchmatch stereo algorithm - [Stereo Matching](http://www.bmva.org/bmvc/2011/proceedings/paper14/paper14.pdf), [wiki](https://en.wikipedia.org/wiki/PatchMatch), [code](https://github.com/ivanbergonzani/patch-match-stereo), 
	- stereo_fusion algorithms - [slide](https://www.cs.princeton.edu/courses/archive/fall07/cos429/slides/stereo.pdf)
	- poisson mesh reconstruction - [slide](http://hhoppe.com/poissonrecon.pdf)
- Computer Vision Course [2019](https://slazebni.cs.illinois.edu/spring19/) - [13 Alignment](https://slazebni.cs.illinois.edu/spring19/lec13_alignment.pdf), [14 Calibration](https://slazebni.cs.illinois.edu/spring19/lec14_calibration.pdf), [15 Single View](https://slazebni.cs.illinois.edu/spring19/lec15_single_view.pdf), [16 Epipolar](https://slazebni.cs.illinois.edu/spring19/lec16_epipolar.pdf), [17 SFM](https://slazebni.cs.illinois.edu/spring19/lec17_sfm.pdf), [18 Stereo](https://slazebni.cs.illinois.edu/spring19/lec18_stereo.pdf), [19 Multiview stereo](https://slazebni.cs.illinois.edu/spring19/lec19_multiview_stereo.pdf)

- [DeepSDF](https://openaccess.thecvf.com/content_CVPR_2019/papers/Park_DeepSDF_Learning_Continuous_Signed_Distance_Functions_for_Shape_Representation_CVPR_2019_paper.pdf) - [Code](https://github.com/facebookresearch/DeepSDF) - [Supp](https://openaccess.thecvf.com/content_CVPR_2019/supplemental/Park_DeepSDF_Learning_Continuous_CVPR_2019_supplemental.pdf)
- [Nerf-W](https://arxiv.org/pdf/2008.02268.pdf) - Nerf in the wild
- [Scene Representation Networks: Continuous 3D-Structure-Aware Neural Scene Representations](https://papers.nips.cc/paper/2019/file/b5dc4e5d9b495d0196f61d45b26ef33e-Paper.pdf)
- [State of the Art on Neural Rendering](https://arxiv.org/pdf/2004.03805.pdf)
- [Local Deep Implicit Functions for 3D Shape](https://github.com/google/ldif)
- [Deformed Implicit Field: Modeling 3D Shapes with Learned Dense Correspondence](https://arxiv.org/pdf/2011.13650.pdf)
- [Stable View Synthesis](https://arxiv.org/pdf/2011.07233.pdf)
	- [Free View Synthesis](http://vladlen.info/papers/FVS.pdf) - [code](https://github.com/intel-isl/FreeViewSynthesis)
- [SDF-SRN: Learning Signed Distance 3D Object Reconstruction from Static Images](https://papers.nips.cc/paper/2020/file/83fa5a432ae55c253d0e60dbfa716723-Paper.pdf)
- [MetaSDF: Meta-learning Signed Distance Functions](https://arxiv.org/pdf/2006.09662.pdf)
- [SDFDiff: Differentiable Rendering of Signed Distance Fields for 3D Shape Optimization](http://www.cs.umd.edu/~yuejiang/papers/SDFDiff.pdf) - [code](https://github.com/YueJiang-nj/CVPR2020-SDFDiff)
	- [Implicit function](https://www.cs.princeton.edu/courses/archive/spring14/cos426/lectures/09-implicit.pdf)
- [Vladlen Koltun: Towards Photorealism](https://www.youtube.com/watch?v=Rd0nBO6--bM), [contact](http://vladlen.info/contact/)



- Understanding illumination: Differenctiable renderer idea, [Two-shot Spatially-varying BRDF and Shape Estimation](https://arxiv.org/pdf/2004.00403.pdf) [code](https://github.com/NVlabs/two-shot-brdf-shape)
	- Deep Learning Papers: [NeRD: Neural Reflectance Decomposition from Image Collections](https://arxiv.org/pdf/2012.03918.pdf) - [project](https://markboss.me/publication/2021-nerd/), [NeRV: Neural Reflectance and Visibility Fields for Relighting and View Synthesis](https://arxiv.org/pdf/2012.03927.pdf) - [project](https://pratulsrinivasan.github.io/nerv/)
	- Tutorial on Spherical Gaussians - [SG SERIES PART 1-6](https://mynameismjp.wordpress.com/2016/10/09/sg-series-part-1-a-brief-and-incomplete-history-of-baked-lighting-representations/), [Spherical Harmonic Lighting: The Gritty Details](http://www.cse.chalmers.se/~uffe/xjobb/Readings/GlobalIllumination/Spherical%20Harmonic%20Lighting%20-%20the%20gritty%20details.pdfs), [Cook Torrence Model](http://www.codinglabs.net/article_physically_based_rendering_cook_torrance.aspx), [Environment mapping Slides](https://cseweb.ucsd.edu/classes/wi18/cse167-a/lec13.pdf)
	- [A Reflectance Model for Computer Graphics](https://inst.eecs.berkeley.edu/~cs294-13/fa09/lectures/cookpaper.pdf), [Bidirectional reflectance distribution function - BRDF](https://en.wikipedia.org/wiki/Bidirectional_reflectance_distribution_function) - [Phong Refelection model](https://en.wikipedia.org/wiki/Phong_reflection_model) - [Cook–Torrance model](https://en.wikipedia.org/wiki/Specular_highlight#Cook%E2%80%93Torrance_model), [Physically-Based Shading at Disney](https://static1.squarespace.com/static/58586fa5ebbd1a60e7d76d3e/t/593a3afa46c3c4a376d779f6/1496988449807/s2012_pbs_disney_brdf_notes_v2.pdf), [Disney BRDF Base color Metallic parametrization](https://www.alexandre-pestana.com/disney-principled-brdf-implementation/), [An Efficient Representation for Irradiance Environment Maps](https://cseweb.ucsd.edu/~ravir/papers/envmap/), [On the Relationship between Radiance and Irradiance: Determining the illumination from images of a convex Lambertian object](https://cseweb.ucsd.edu/~ravir/papers/invlamb/), [Physically based rendering (PBR)](http://www.codinglabs.net/article_physically_based_rendering.aspx), [OpenGL PBR](https://learnopengl.com/PBR/Theory),
	- Material Editing - [Photorealistic Material Editing Through Direct Image Manipulation](https://users.cg.tuwien.ac.at/~zsolnai/wp/wp-content/uploads/2019/09/pme.pdf), [Gaussian Material Synthesis](https://users.cg.tuwien.ac.at/zsolnai/gfx/gaussian-material-synthesis/)

	- Not Read, Probably good:
		- [Neural Reflectance Fields for Appearance Acquisition](https://arxiv.org/pdf/2008.03824.pdf) - [author](http://cseweb.ucsd.edu/~bisai/)
		- [All-Frequency Rendering of Dynamic, Spatially-Varying Reflectance](https://www.microsoft.com/en-us/research/wp-content/uploads/2009/12/sg.pdf), [tutorial slide](https://www.slideserve.com/calder/all-frequency-rendering-of-dynamic-spatially-varying-reflectance) - tutorials on using Spherical Gaussians for BRDF and Environment illumination - [Portrait Neural Radiance Fields from a Single Image](https://arxiv.org/pdf/2012.05903.pdf)
	- [Physics based Methods in Vision](http://www.cs.cmu.edu/afs/cs/academic/class/16823-s16/www/pdfs/)
	- [Ligting basics](https://dreamfarmstudios.com/blog/the-ultimate-guide-to-lighting-fundamentals-for-3d/), [Video](https://www.facebook.com/BusinessInsiderIndia/videos/366771777864939), [3D Texturing](https://dreamfarmstudios.com/blog/getting-to-know-3d-texturing-in-animation-production/)

- Online 3D model assets:
	- [TurboSquid](https://www.turbosquid.com/) - Using professional models. This is a good reference
	- Environmental Maps - [HDRI Haven](https://hdrihaven.com/hdris/)
- Depth Estimation from input image: [MiDaS](https://arxiv.org/pdf/1907.01341v3.pdf), [code](https://github.com/intel-isl/MiDaS),[latest code](https://pytorch.org/hub/intelisl_midas_v2/) - Perpetual View Generation - [Infinite Nature](https://infinite-nature.github.io/)
	- [One Shot 3D Photography](https://facebookresearch.github.io/one_shot_3d_photography/), [code](https://github.com/facebookresearch/one_shot_3d_photography), 

- Local Deep Implicit Functions for 3D Shape - [code](https://github.com/google/ldif), [paper](https://arxiv.org/pdf/1912.06126.pdf) - Learning a transformation matrix to approximate a gaussian function to define an implicit function. [Learning Shape Templates with Structured Implicit Functions](https://arxiv.org/pdf/1904.06447.pdf) - Can we use this to approximate shapes
- Understanding SDF based operations - ray marching and sdf - [article1](http://jamie-wong.com/2016/07/15/ray-marching-signed-distance-functions/), [article2](https://www.iquilezles.org/www/articles/distfunctions/distfunctions.htm), [SDF renderiing](https://www.cl.cam.ac.uk/teaching/1819/FGraphics/1.%20Ray%20Marching%20and%20Signed%20Distance%20Fields.pdf), [Sphere Tracing](http://graphics.stanford.edu/courses/cs348b-20-spring-content/uploads/hart.pdf)
- canonical coordinates 3d model, quaternion representation of rotation
- Adding secondary motion - [Complementary Dynamics](https://www.dgp.toronto.edu/projects/complementary-dynamics/)
- Not read: [Learning to Recover 3D Scene Shape from a Single Image](https://arxiv.org/pdf/2012.09365.pdf), [Iso-Points: Optimizing Neural Implicit Surfaces with Hybrid Representations](https://arxiv.org/pdf/2012.06434.pdf), [Object-Centric Neural Scene Rendering](https://arxiv.org/pdf/2012.08503.pdf), [computer assisted prog](https://capworkshop.github.io/), [signed-distance-SRN](https://github.com/chenhsuanlin/signed-distance-SRN), [differentiable_volumetric_rendering](https://github.com/autonomousvision/differentiable_volumetric_rendering), 

- Quaternions - [ref1](https://jinyongjeong.github.io/Download/SE3/jlblanco2010geometry3d_techrep.pdf), [ref2](https://maxime-tournier.github.io/notes/quaternions.html), [SE(3) transform](https://www.seas.upenn.edu/~meam620/slides/kinematicsI.pdf)

- [StyleGAN](https://arxiv.org/abs/1812.04948), [StyleFlow](https://rameenabdal.github.io/StyleFlow/)

- [NeRF−−: Neural Radiance Fields Without Known Camera Parameters](https://arxiv.org/pdf/2102.07064.pdf)
- Companies - [Teriflix](https://www.teriflix.com/), [Searching for artist](https://www.artella.com/), [paperboatstudios](https://paperboatstudios.co/index), [studiodurga](https://www.studiodurga.com/)


AI Sculptor: Assuming the rays as a nail, we like to sculpt a 3D model based on multiple input views. We use the NSVF as our based code. The list of problems we are planning to attack:
	- Marching cubes would fail to recover the surface since the function learns only the boundary and does not learn inside the object. So a different learning algorithm is required for learning the 3D mesh object. We need to find a better algorithm to extract the 3D mesh and surface information. 
		- A soluttion would be to shoot rays from different directions and choose only those points which have normals which are parallel to the ray of intersection. Use these points as an input to creat a point cloud and then convert this point cloud to a mesh using [pointcloud2mesh](https://towardsdatascience.com/5-step-guide-to-generate-3d-meshes-from-point-clouds-with-python-36bad397d8ba) algorithms, [Surface Reconstruction](https://www.cgal.org/)
	- Alternative representation: Signed Distance field representation has better representation of objects than transparency representation. Can we use SDF instead of transparency? Define a rendering function using SDF. Use this function instead of transparency based rendering function and then use it to represent Neural scene [DeepSDF](https://openaccess.thecvf.com/content_CVPR_2019/papers/Park_DeepSDF_Learning_Continuous_Signed_Distance_Functions_for_Shape_Representation_CVPR_2019_paper.pdf), [DeepLS](https://arxiv.org/pdf/2003.10983.pdf), [Papier-Machˆe](https://arxiv.org/pdf/1802.05384.pdf), [Occupancy Networks](https://openaccess.thecvf.com/content_CVPR_2019/papers/Mescheder_Occupancy_Networks_Learning_3D_Reconstruction_in_Function_Space_CVPR_2019_paper.pdf)
	- Heirarchical representation: Nerf/DeepSDF use NN to represent the whole scene. NSVF/DeepLS use local embedding information to represent shapes in voxels. Can a heirarchchical representation of latent variables be used to represnet the whole shape to get consistent representation.
	- Can the shape information used as code in DeepSDF be used in NERF/NSVF kind of setup to reduce the number of images to encode a scene directly from a siingle image
	- Physics simulation using NeRF: [Real Time Fluid simulation](https://users.cg.tuwien.ac.at/zsolnai/gfx/fluid_control_msc_thesis/), [Learning to simulate](https://arxiv.org/pdf/2002.09405.pdf)


###### List of questions
- multiresolution in signed distance function, how are multiple objects composed using SDF, What is the maximum capacity of NN?, occupancy vs sdf comparison
- a KD-tree - nearest neighbor algorithm -
- distance transform for any watertight shapes
- Weight normalization: A simple reparameterization to accelerate training of deep neural networks. - speed up training instead of batch normalization
- H.P.: Multi-level partition of unity implicits. - Splitting a volume into smaller regions and trying to generate to whole shape based on sum of smaller regions - weighting function is 1 when you are within the region - https://www.cc.gatech.edu/~turk/my_papers/mpu_implicits.pdf - https://en.wikipedia.org/wiki/Partition_of_unity 
- datasets: https://3dwarehouse.sketchup.com/, http://graphics.stanford.edu/data/3Dscanrep/

##### Other queries
- [AI Economist](https://blog.einstein.ai/the-ai-economist/)
- [DALL·E: Creating Images from Text](https://openai.com/blog/dall-e/)
- [Transformers are Graph Neural Networks](https://thegradient.pub/transformers-are-graph-neural-networks/)
- [Immersive Light Field Video with a Layered Mesh Representation](https://storage.googleapis.com/immersive-lf-video-siggraph2020/ImmersiveLightFieldVideoWithALayeredMeshRepresentation.pdf)
- [EFFICIENT CONTINUAL LEARNING WITH MODULAR NETWORKS AND TASK-DRIVEN PRIORS](https://arxiv.org/pdf/2012.12631.pdf)
- [IIRC: Incremental Implicitly-Refined Classification](https://arxiv.org/pdf/2012.12477.pdf)
- A algorithm to solve generic problems: [C-Space Tunnel Discovery for Puzzle Path Planning](https://xinyazhang.gitlab.io/puzzletunneldiscovery/), [More Puzzles](https://gitlab.com/xinyazhang/puzzle-geometry/-/tree/master/), [paper](https://xinyazhang.gitlab.io/puzzletunneldiscovery/assets/MainPaper.pdf) - Concentrate on the different planning algorithms. The baisc idea would be to find tunnels (i.e. narrow points which could possibly leead to a solution). Then have a duble tree starting from Start and reversely from goal. This could be done for every tunnel point. This stage is the blooming stage. You could approximate the value of the tree using neural networks. Try finding links from the bloomed tree and the successive tunnel paths. IF we find a route find the optimal route from start to end - Probabilistic Roadmap Path Planning [PRM Planner](http://www.cs.columbia.edu/~allen/F15/NOTES/Probabilisticpath.pdf), [PRM1](https://people.eecs.berkeley.edu/~pabbeel/cs287-fa11/slides/MotionPlanning-v1.pdf), [RDT-Based Methods](http://planning.cs.uiuc.edu/node772.html) - dual-tree RDT algorithm 
- [Interlinked SPH Pressure Solvers for Strong Fluid-Rigid Coupling](https://cg.informatik.uni-freiburg.de/publications/2019_TOG_strongCoupling.pdf), 


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


###### To Be Read Papers
- [Interactive Video StylizationInteractive Video Stylization](https://ondrejtexler.github.io/patch-based_training/), [Resolution Dependent GAN](https://arxiv.org/pdf/2010.05334.pdf), [Video Completion](http://chengao.vision/FGVC/),[Latent Space of Generative Networks](https://arxiv.org/pdf/1707.05776.pdf), [Bayesian Deep Learning for Computer Vision](https://arxiv.org/pdf/1703.04977.pdf), [Real Image Editing GAN](https://genforce.github.io/idinvert/), [Rewriting a Deep Generative Model](https://rewriting.csail.mit.edu/)
- Softwares: [AI Vdo](https://www.synthesia.io/), [CineTracer](https://www.cinetracer.com/),[GPU Sharing](https://vast.ai/),[SpyFU](https://www.spyfu.com/), [OBS Studio](https://obsproject.com/)
- [Neural Sampling](https://research.fb.com/wp-content/uploads/2020/06/Neural-Supersampling-for-Real-time-Rendering.pdf)
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
- Character creation: [Reallusion](https://www.reallusion.com/), [Adobe Fuse/Mixamo](https://www.mixamo.com/fuse/1.3/eol)


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

