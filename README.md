# Single Image Super-Resolution Quality Assessment: A Real-World Dataset, Subjective Studies, and An Objective Metric
This is the brief description of *RealSRQ* dataset and *KLTSRQA* software. For more details, please refer to our paper:  

Single Image Super-Resolution Quality Assessment: A Real-World Dataset, Subjective Studies, and An Objective Metric, Qiuping Jiang, Zhentao Liu, Ke Gu, Feng Shao, Xinfeng Zhang, Hantao Liu, Weisi Lin, IEEE Transactions on Image Processing, 2022.  

You can change our program as you like and use it anywhere, but please refer to its original source and cite our paper. 
# Abstract
Numerous single image super-resolution (SISR) algorithms have been proposed to reconstruct a high-resolution (HR) image from its low-resolution (LR) observation. However, the majority of these algorithms are only validated on synthetic data. So far, the lack of comprehensive human subjective study on large-scale real-world SISR datasets and accurate objective SISR quality assessment metrics makes it unreliable to truly understand the performance of different SISR algorithms on real-world data. We make the following attemps tackle these two issues. Firstly, we construct a real-world SISR quality dataset (i.e., *RealSRQ*) and conduct human subjective studies to compare the performance of the representative SISR algorithms. Secondly, we propose a objective metric, i.e., *KLTSRQA*, based on the Karhunen-Loeve Transform (KLT) to evaluate the quality of real-world SISR images in a no-reference (NR) manner. Experiments on our constructed *RealSRQ* and the latest synthetic SISR quality dataset (i.e., *QADS* [1]) have demonstrated the superiority of our proposed *KLTSRQA* metric, achieving higher consistency with human subjective scores than relevant existing NR image quality assessment (NR-IQA) metrics.

# RealSRQ: A Real-World SISR Quality Dataset
## Real-Wold LR-HR Image Pairs
We aim to compare the performance of different SISR algorithms for real-world LR images. In this work, we collect the real-world LR images either from the *RealSR* dataset [2] or captured by ourselves following the same method in *RealSR*, i.e., adjust the focal length of a fixed digital single-lens reflex camera (i.e., Canon 5D3). For each scene, images are taken using four focal lengths: 105mm, 50mm, 35mm, and 28mm. Images taken by the largest focal length are used to generate the HR images, and images taken by the other three focal lengths are used to generate the three LR versions. Overall, we collect 60 HR images and corresponding 60 LR images at three scaling factors, i.e., LR2, LR3, and LR4 respectively.
## SISR Algorithms
In this study, we evaluate 10 representative SISR algorithms, include BCI, ASDS [3], SPM [4], Aplus [5], AIS [6], SRCNN [7], CSCN [8], VDSR [9], SRGAN [10], and USRnet [11]. The former five methods are non-deep methods while the latter five methods are deep learning-based SISR methods, and covers recent major publications in the field. As a result, we finally obtain 1620 SR images in total. The following table provides more details. 

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Table1.PNG" width="400" height="190"/><br/>

# KLTSRQA: An Objective NR Quality Metric for SISR
The flow chart of *KLTSRQA* is depicted in the following figure. The input of *KLTSRQA* is a to-be-evaluated SISR image and the output is an estimated quality score. For an input SISR image in the RGB format, we first convert it into the opponent color space and then perform a local mean subtraction and divisive normalization on each color channel to obtain three mean subtracted contrast normalized (MSCN) coefficient maps. The KLT is performed on the corresponding MSCN maps using the KLT kernels that we have constructed offline. Therefore, we can obtain three KLT coefficient matrices corresponding to the three opponent color channels. Based on the obtained KLT coefficient matrix for each channel, quality-aware feature extraction is performed from two aspects. On the first aspect, we use the asymmetric generalized Gaussian distribution (AGGD) model to fit the KLT coefficients in different spectral components and the estimated AGGD parameters are taken as the first part of features. On the second aspect, we compute the energy of the KLT coefficients in different spectral components as the second part of features. These two parts of features are combined together and aggregated over three channels to yield a final quality-aware feature vector for quality score prediction via the SVMrank model.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig8.PNG" width="618" height="288"/><br/>

# Contact Us
If you have any problem of our program, please feel free to contact with the authors: jiangqiuping@nbu.edu.cn, zhentaolau@163.com.

# Download
You can download our constructed dataset and proposed software from  
BaiduYun disk: [*RealSRQ-KLTSRQA-released*](https://pan.baidu.com/s/15ZgfpW1b2_gMAETBUeszSg) (key:1121)  
Google Drive: [*RealSRQ-KLTSRQA-released*](https://drive.google.com/drive/folders/1VTMBmxkZkZtbv_ONMME-7TRyfXNfRw9p?usp=sharing)

# Reference
[1] F. Zhou, R. Yao, B. Liu, and G. Qiu, “Visual quality assessment for super-resolved images: Database and method,” IEEE Transactions on Image Processing, vol. 28, no. 7, pp. 3528–3541, 2019.  
[2] J. Cai, H. Zeng, H. Yong, Z. Cao, and L. Zhang, “Toward real-world single image super-resolution: A new benchmark and a new model,” in 2019 IEEE/CVF International Conference on Computer Vision (ICCV), 2019, pp. 3086–3095.  
[3] W. Dong, L. Zhang, G. Shi, and X. Wu, “Image deblurring and super-resolution by adaptive sparse domain selection and adaptive regularization,” IEEE Transactions on Image Processing, vol. 20, no. 7, pp. 1838–1857, 2011.  
[4] T. Peleg and M. Elad, “A statistical prediction model based on sparse representations for single image super-resolution,” IEEE Transactions on Image Processing, vol. 23, no. 6, pp. 2569–2582, 2014.  
[5] R. Timofte, V. Desmet, and L. Van Gool, “A+: Adjusted anchored neighborhood regression for fast super-resolution,” in Asian Conference on Computer Vision, 2014, pp. 111–126.  
[6] E. Perez-Pellitero, J. Salvador, J. Ruiz-Hidalgo, and B. Rosenhahn, “Antipodally invariant metrics for fast regression-based super-resolution,” IEEE Transactions on Image Processing, vol. 25, no. 6, pp. 2456–2468, 2016.  
[7] C. Dong, C. L. Chen, K. He, and X. Tang, “Learning a deep convolutional network for image super-resolution,” in European Conference on Computer Vision, 2014, pp. 184–199.  
[8] Z. Wang, D. Liu, J. Yang, W. Han, and T. Huang, “Deep networks for image super-resolution with sparse prior,” in 2015 IEEE International Conference on Computer Vision (ICCV), 2015, pp. 370–378.  
[9] J. Kim, J. K. Lee, and K. M. Lee, “Accurate image super-resolution using very deep convolutional networks,” in 2016 IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2016, pp. 1646–1654.  
[10] C. Ledig, L. Theis, F. Husz´ar, J. Caballero, A. Cunningham, A. Acosta, A. Aitken, A. Tejani, J. Totz, Z. Wang, and W. Shi, “Photo-realistic single image super-resolution using a generative adversarial network,” in 2017 IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2017, pp. 105–114.  
[11] K. Zhang, L. Van Gool, and R. Timofte, “Deep unfolding network for image super-resolution,” in 2020 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), 2020, pp. 3214–3223.  
