---
title: To Infinity And Beyond
# View.
#   1 = List
#   2 = Compact
#   3 = Card
#   4 = Citation
view: 1
---

[About](#about) - [MoCap SMPL-X priors](#motion-capture-using-smpl-x-priors) - [NeRF Rendering System](#neural-radiance-field-rendering-systems) - [Problems](#problems-working-on) - [References](#reference) 

##### About
Inspired from Pixar, Dreamworks, Sony and other animation studios. The general time required to produce an animated feature from conception to final rendered version has a long production time. Can Artificial Intelligence based solutions help in reducing this time line? 

The current advancements in deep learning in the area of GAN, Neural Rendering, Transformers help to automate many processes like creating 3D models, animating 3d model motion. 

###### Motion Capture using SMPL-X priors [(details)](#problems-working-on)
- Using monocular video information
![screen reader text](mocap_parkor.gif "VIBE")
- Facial, finger and full Body pose extraction
![screen reader text](mocap_smplx.jpeg "SMPLify-X")
<!-- {{< figure src="mocap_smplx.jpeg" caption="A caption" numbered="true" >}} -->

######  Neural radiance field rendering systems [(details)](#problems-working-on)
- Fast training for rigid bodies
![screen reader text](NSVF.png "NSVF")
![screen reader text](neural_body.gif "Neural Body")
- Non-rigid (human models) pose, cloth and hair feature transfer
![screen reader text](nerf_controllable_features.gif "ADGAN") ![screen reader text](nerf_pose_transfer.gif "ADGAN")


##### Problems Working On
- Shape and pose iteration for refinement of image based pose for the original dimension [link](https://github.com/nitthilan/video_pose_estimation)
	- HMR (Human mesh recovery) use CNNs and so the images are resized thus losing its prediction precision. 
	- SMPLify-X based approches are iterative and do not reach global minima faster
	- A hybrid approach which merges the both to get higher precision prediction while maintaining consistency across frames
- Multiresolution video pose estimation
	- A video has a large number of images and estimating pose for all frames would be huge
	- Pose interpolation using transformers to reduce computation
	- Transformer based approaches to use temporal consistency to get better prediction for occluded parts
	- Identify non occluded frames and interpolate intermediate frames to estimate pose
- Learning pose using videos in the wild 
	- Use 2D keypoint markers and temporal shape consistency to learn mocap information
	- Estimate facial and finger pose estimation
	- Estimate initial prediction using resized input images using neural network based approaches
	- Apply SMPLify-X based iterative approaches to refine pose using full resolution images to get precise prediction
- Facial, hand and full pose control of deformable human neural avatars
	- Extract mocap information from driver video
	- Learn neural body based avatars using SMPL-X
	- Deform SMPL-X model using the driver video
- Deformable neural cloth and hair styles extraction from video in wild
	- Use human parser to extract different clothing types and hair
	- Learn neural models for each segment extracted earlier
	- This helps in transfering information across different avatars
- Multi-resolution neural training for both rigid and non-rigid objects
	- Active learing based appraches to identify subset of images which maximize learning
	- Start with low resolution images and downsampled video
	- Choose the training subset based on the rendered quality across different view
- Voxel based latent learning [link](https://github.com/nitthilan/kilonerf_modified)
	- Learn a pre-trained network which approximates simpler shapes ata voxel level
	- Reduce training iteration time
- Neural sub-problems
	- Predicting occluded regions from known regions
	- GAN based generator for neural body

##### References:
- [VIBE: Video Inference for Human Body Pose and Shape Estimation](https://github.com/mkocabas/VIBE)
- [SMPLify-X](https://github.com/vchoutas/smplify-x)
- [FrankMocap: A Strong and Easy-to-use Single View 3D Hand+Body Pose Estimator](https://github.com/facebookresearch/frankmocap)
- [End-to-end Recovery of Human Shape and Pose](https://github.com/akanazawa/hmr)
- [NeRF: Neural Radiance Fields](https://github.com/bmild/nerf)
- [Neural Body: Implicit Neural Representations with Structured Latent Codes for Novel View Synthesis of Dynamic Humans](https://github.com/zju3dv/neuralbody)
- [KiloNeRF: Speeding up Neural Radiance Fields with Thousands of Tiny MLP](https://github.com/creiser/kilonerf)
- [Neural Sparse Voxel Fields (NSVF)](https://github.com/facebookresearch/NSVF)
- [Controllable Person Image Synthesis with Attribute-Decomposed GAN](https://github.com/menyifang/ADGAN)
- [PIFuHD: Multi-Level Pixel-Aligned Implicit Function for High-Resolution 3D Human Digitization (CVPR 2020)](https://github.com/facebookresearch/pifuhd)

