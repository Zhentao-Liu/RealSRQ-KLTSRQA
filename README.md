# RealSRQE_KLTSRQA
This is the link of RealSRQE dataset and KLTSRQA software

RealSRQE Dataset and KLTSRQA Software release.
========================================================================

-----------COPYRIGHT NOTICE STARTS WITH THIS LINE------------

Copyright (c) 2021 Ningbo University (NBU)
All rights reserved.

Permission is hereby granted, without written agreement and without license or royalty fees, to use, copy, 
modify, and distribute this dataset and code for any purpose, provided that the copyright notice in its 
entirety appear in all copies of this database and code, the research is to be cited in the bibliography as:

1)

IN NO EVENT SHALL NBU BE LIABLE TO ANY PARTY FOR DIRECT, INDIRECT, SPECIAL, INCIDENTAL, OR 
CONSEQUENTIAL DAMAGES ARISING OUT OF THE USE OF THIS DATASET AND CODE, EVEN IF NBU 
HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

NBU SPECIFICALLY DISCLAIMS ANY WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED 
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. THE DATASET AND 
CODE PROVIDED HEREUNDER IS ON AN "AS IS" BASIS, NBU HAS NO OBLIGATION TO PROVIDE 
MAINTENANCE, SUPPORT, UPDATES, ENHANCEMENTS, OR MODIFICATIONS.

-----------COPYRIGHT NOTICE ENDS WITH THIS LINE------------%

========================================================================

Author  : Zhentao Liu et al.
Version : 1.1

This folder includes a real-world SISR image quality evaluation dataset (RealSRQE) that we constructed and 
implemantation of KLT Based Blind Image Quality Assessment (KLTSRQA) that we proposed. The dataset and 
algorithm are described in:

You can change this program as you like and use it anywhere, but please refer to its original source (cite our paper)

Document Description and Usage

Folder :
1. pristine
This folder includes all the HR images in RealSRQE. We use these HR images for KLT kernel training.

2. RealSRQE
This folder includes the dataset that we constructed. It includes HR-LR image pairs and corresponding SISR results.

M file ：
1. color_change.m
This is used for color space conversion from RGB to a perceptual quality relevant opponent color space.

2. estimateaggdparam.m
This is used for KLT coefficients AGGD parameter estimation.

3. modcrop.m
This is used to crop image border.

4. MSCN_compute.m
This is used to compute MSCN coefficients of input image.

5. patch_extract.m
This is used for image patch extraction.

6. KLT_kernel_training.m
This is used for KLT kernel training with specified kernel size.

7. KLT_feature.m
This is used for feature extraction.

8. Kernel_training_demo.m
This is a demo for kernel training. 

9. feature_extract_demo.m
This is a demo for feature extraction.

MAT file :
1. KLT_kernel_64.mat
This is our pretrained KLT kernel with size 64*64 using the images in pristine folder.

2. subj_BT_score.mat
This is the BT score of each SISR result that derived from subjective user study.

This code has been tested on Windows in MATLAB 

========================================================================
