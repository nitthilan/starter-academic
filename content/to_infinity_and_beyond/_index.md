---
title: To Infinity And Beyond
# View.
#   1 = List
#   2 = Compact
#   3 = Card
#   4 = Citation
view: 1
---

[About](#about) - [3D Volumetric Video System](#Deep-Neural-Radiance-Field-based-3D-Volumetric-Video-Capture-Rendering-and-Streaming) - [Drawbacks](#drawbacks) - [Problems](#problems-working-on) - [References](#references) 

##### About
More and more AR and VR devices becoming ubiquitous and advancement in animation, we see a shift in the way people consume content. Instead of using mobile, tablet and TV screens, more and more immersive 3D volumetric displays using AR/VR devices like Oculus, Holo Lens, Vive are getting used. This inturn increases the demand for generation and consumption of immersive content for various applications like live action sports, music concerts, performances or virtual worlds where consumers can interact and hang out with their favorites artists, sportsman or teleport themselves to exotic locations

Being interested in application of AI/ML in the area of 3D graphics and animation and having a background in video encoding for conferencing, transmission and storage am proposing a low cost consumer grade volumetric video capture, storage, renderer and streaming solution for AR/VR end devices


##### Deep Neural Radiance Field based 3D Volumetric Video Capture, Rendering and Streaming

![screen reader text](volumetric_video.png "Neural Body")


To provide a user with a immersive experience, the whole media pipeline from capture, storage, rendering and streaming should be capable of handling 3D volumetric data. First, to capture 3D volumetric data, we would require a multi-camera system, which capture the action from different views. Further, we breakdown the scene into a less important background region, a center stage foreground area where the actual action happens. This helps in encoding the background with less detail and forground with higher precision. Further, to enhance the quality, we separate objects into rigid and non-rigid human bodies. In effect, we split the scene into three prominent regions (a) Foreground Rigid Bodies (b) Foreground Non-Rigid (Human) Bodies (c) Background Region. Unlike, other solutions which encode these objects as meshes and textures, we propose a Deep learning based neural radiance field solution for each of these regions. Further, the immersive visualization is provided to the user by compositing the three regions into a stereo 360 degree panoromic image for each time instant and stream it to a Unity VR app running on a VR headset. Based on these features, we breakdown our system into the following components:

###### (a) Multi-view capture system

We design a capture system which ranges from 1 to N monocular RGB cameras. This could be as simple as multiple mobile cameras capturing a performance or scene from different angles. This setup enables general users to create content that could be immersively consumed. The capture is synchronized so that multiple captures can be correlated for a particular time instance across different cameras. These different video streams are then uploaded to the cloud server.

###### (b) Split neural encoder, renderer and compositor

The next stage, involves splitting the data into foreground and background, rigid and non-rigid (human) bodies. Each of these components are then encoded seprately into a deep neural network as neural radiance fields. Background region is encoded using Nerf++ based network. The foreground requires optimized rendering (or inference) and many solution options are to be investigated. Some of the options are KiloNerf, PlenOctrees. Finally, the non-rigid body is encoded using Neural body based network solutions. The scene is composited by rendering the individual neural networks encoded for the three separate regions based on the position and viewing angle feedback from the user. This composited stereo 360 degree panoroma image is then possed on to the next stage to be compressed and streamed


###### (c) 360 Stereo video encoder 

The final stage, encodes the composited stereo image and compresses it into a video stream (H264, MPEG, MJPEG) and streamed to the VR headset. A Unity based VR app, displays the compressed stream on the skybox shader to provide a immersive visualization of the captured sequence to the end user


##### Current status

- Individual modules are available for each module
- In the process of creating a MVP to demo the end-to-end solution
- Anyone interested in the following problems can reach me nitthilan@gmail.com

##### Drawbacks

- The encoding (or storage) is time consuming since it depends on the training time which is at present in the order of hours
- The streaming delay would still be significant since it is done through the cloud


##### Reference
- [NeRF: Neural Radiance Fields](https://github.com/bmild/nerf)
- [Neural Body: Implicit Neural Representations with Structured Latent Codes for Novel View Synthesis of Dynamic Humans](https://github.com/zju3dv/neuralbody)
- [Neural Sparse Voxel Fields (NSVF)](https://github.com/facebookresearch/NSVF)
- [NeRF++: Analyzing and Improving Neural Radiance Fields](https://github.com/Kai-46/nerfplusplus)
- [PlenOctrees: For Real-time Rendering of Neural Radiance Fields](https://alexyu.net/plenoctrees/)
- [KiloNeRF: Speeding up Neural Radiance Fields with Thousands of Tiny MLPs](https://github.com/creiser/kilonerf)
- [VIBE: Video Inference for Human Body Pose and Shape Estimation](https://github.com/mkocabas/VIBE)
- [SMPLify-X](https://github.com/vchoutas/smplify-x), [SMPL-X](https://smpl-x.is.tue.mpg.de/), [SMPL](https://smpl.is.tue.mpg.de/)
- [FrankMocap: A Strong and Easy-to-use Single View 3D Hand+Body Pose Estimator](https://github.com/facebookresearch/frankmocap)
- [End-to-end Recovery of Human Shape and Pose](https://github.com/akanazawa/hmr), [SPIN: SMPL oPtimization IN the loop](https://github.com/nkolot/SPIN)
- [Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/)
- [Controllable Person Image Synthesis with Attribute-Decomposed GAN](https://github.com/menyifang/ADGAN)
- [PIFuHD: Multi-Level Pixel-Aligned Implicit Function for High-Resolution 3D Human Digitization (CVPR 2020)](https://github.com/facebookresearch/pifuhd)
- [Debugging networks](https://jonathan-hui.medium.com/debug-a-deep-learning-network-part-5-1123c20f960d)
-  [On the Continuity of Rotation Representations in Neural Networks](https://arxiv.org/pdf/1812.07035.pdf), [Tutorial blog](https://towardsdatascience.com/better-rotation-representations-for-accurate-pose-estimation-e890a7e1317f)

