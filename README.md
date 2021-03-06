# [Learning Deep CNN Denoiser Prior for Image Restoration](http://www4.comp.polyu.edu.hk/~cslzhang/paper/IRCNN_CVPR17.pdf)


# Abstract
Model-based optimization methods and discriminative learning methods have been the two dominant strategies for solving various inverse problems in low-level vision.
Typically, those two kinds of methods have their respective merits and drawbacks, e.g., model-based optimization methods are flexible for handling different inverse problems but are usually time-consuming with sophisticated priors for the purpose of good performance; in the meanwhile, discriminative learning methods have fast testing speed but their application range is greatly restricted by the specialized task.
Recent works have revealed that, with the aid of variable splitting techniques, denoiser prior can be plugged in as a modular part of model-based optimization methods to solve other inverse problems (e.g., deblurring). Such an integration induces considerable advantage when the denoiser is obtained via discriminative learning. However, the study of integration with fast discriminative denoiser prior is still lacking. To this end, this paper aims to train a set of fast and effective CNN (convolutional neural network) denoisers and integrate them into model-based optimization method to solve other inverse problems. Experimental results demonstrate that the learned set of denoisers can not only achieve promising Gaussian denoising results but also can be used as prior to deliver good performance for various low-level vision applications.

# Basic Idea
With the aid of variable splitting techniques, such as alternating direction method of multipliers (ADMM) method and half quadratic splitting (HQS) method, it is possible to deal
with fidelity term and regularization term of general image restoration formulation separately, and particularly, the regularization term only corresponds to a denoising subproblem. 
Consequently, this enables an integration of any discriminative denoisers into model-based optimization methods to solve various image restoration tasks, such as 
- **Image Deblurring**
- **Image Inpainting**
- **Single Image Super-Resolution** 
- **Color Image Demosaicking**


# Image Deblurring
 The left is the blurred image. The right is the deblurred image by IRCNN with estimated kernels by other blind deblurring methods.
- Deblur_set1

<img src="testsets/Deblur_set1/Blurry4_1.png" width="400px"/> <img src="testsets/Deblur_set1/Blurry4_1_output_ircnn.png" width="400px"/>

- Deblur_set2

<img src="testsets/Deblur_set2/im04_ker01.png" width="400px"/> <img src="testsets/Deblur_set2/im04_ker01_ircnn.png" width="400px"/>

- Deblur_set3

<img src="testsets/Deblur_set3/2013622235456945_blur_79.png" width="400px"/> <img src="testsets/Deblur_set3/2013622235456945_blur_79_ircnn_Isigma_1_Msigma_1.png" width="400px"/>

<img src="testsets/Deblur_set3/color_patch_blur_99.png" width="400px"/> <img src="testsets/Deblur_set3/color_patch_blur_99_ircnn_Isigma_1_Msigma_1.png" width="400px"/>

<img src="testsets/Deblur_set3/IMG_1240_blur.png" width="400px"/> <img src="testsets/Deblur_set3/IMG_1240_blur_ircnn_Isigma_2_Msigma_7.png" width="400px"/>



Use [Demo_deblur_real_application.m](Demo_deblur_real_application.m) to test IRCNN for image deblurring with estimated kernel by other blind deblurring methods.

# Image Inpainting

The left is the masked image. The right is the recovered image by IRCNN.

- Inpaint_set1

<img src="testsets/Inpaint_set1/butterfly_color_80_masked.png" width="400px"/> <img src="testsets/Inpaint_set1/butterfly_color_80_ircnn.png" width="400px"/>

<img src="testsets/Inpaint_set1/butterfly_gray_75_masked.png" width="400px"/> <img src="testsets/Inpaint_set1/butterfly_gray_75_ircnn.png" width="400px"/>

<img src="testsets/Inpaint_set1/09_50_masked.png" width="400px"/> <img src="testsets/Inpaint_set1/09_50_ircnn.png" width="400px"/>

- Inpaint_set2

<img src="testsets/Inpaint_set2/3ch.png" width="400px"/> <img src="testsets/Inpaint_set2/3ch_ircnn.png" width="400px"/>

<img src="testsets/Inpaint_set2/new.png" width="400px"/> <img src="testsets/Inpaint_set2/new_ircnn.png" width="400px"/>

Use [Demo_inpaint.m](./Demo_inpaint.m) and [Demo_inpaint_real_application.m](Demo_inpaint_real_application.m) to produce the above results.

# Single Image Super-Resolution (SISR)
```
The left is the zoomed LR image (x3) with motion blur kernel, the right is the super-resolved image (x3) by IRCNN.
```
<img src="figs/LR1.png" width="400px"/> <img src="figs/LR1_IRCNN.png" width="400px"/>

The left is the low-resolution (LR) image. The right is the super-resolved image by IRCNN.

- SISR_set1, synthetic LR image SR

<img src="testsets/SISR_set1/LR3_noisy_x2.png" width="160px"/> <img src="testsets/SISR_set1/LR3_noisy_x2_ircnn_x2.png" width="320px"/>

<img src="testsets/SISR_set1/LR1_motion_x2.png" width="240px"/> <img src="testsets/SISR_set1/LR1_motion_x2_ircnn_x2.png" width="480px"/>

- SISR_set2, real LR image SR

<img src="testsets/SISR_set2/chip.png" width="109px"/> <img src="testsets/SISR_set2/chip_ircnn_x2.png" width="218px"/> <img src="testsets/SISR_set2/chip_ircnn_x4.png" width="436px"/>

<img src="testsets/SISR_set2/David_Hilbert.png" width="220px"/> <img src="testsets/SISR_set2/David_Hilbert_ircnn_x2.png" width="440px"/>

<img src="testsets/SISR_set2/Frog.png" width="266px"/> <img src="testsets/SISR_set2/Frog_ircnn_x2.png" width="532px"/>

Use [Demo_SISR_direct_downsampler_real_application.m](./Demo_SISR_direct_downsampler_real_application.m) to produce the above SISR results.

<img src="figs/sr1.png" width="820px"/>

# Color Image Demosaicking

The left is the mosaiced image. The right is the demosaiced image by IRCNN.

- Set18 (McMaster, IMAX)

<img src="figs/01_mosaik.png" width="400px"/> <img src="figs/01_ircnn.png" width="400px"/>

- Set24 (Kodak)

<img src="figs/kodim19_mosaik.png" width="400px"/> <img src="figs/kodim19_ircnn.png" width="400px"/>

Use [Demo_demosaiking.m](./Demo_demosaiking.m) to produce the above results.

# Requirements and Dependencies
- MATLAB R2015b
- [Cuda](https://developer.nvidia.com/cuda-toolkit-archive)-8.0 & [cuDNN](https://developer.nvidia.com/cudnn) v-5.1
- [MatConvNet](http://www.vlfeat.org/matconvnet/)

# Citation

```
 @inproceedings{zhang2017learning,
   title={Learning Deep CNN Denoiser Prior for Image Restoration},
   author={Zhang, Kai and Zuo, Wangmeng and Gu, Shuhang and Zhang, Lei},
   booktitle={IEEE Conference on Computer Vision and Pattern Recognition},
   pages={3929--3938},
   year={2017},
 }
 ```
