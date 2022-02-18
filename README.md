# Single Image Super-Resolution Quality Assessment: A Real-World Dataset, Subjective Studies, and An Objective Metric
This is the brief description of *RealSRQ* dataset and *KLTSRQA* software. For more details, please refer to our paper:  
Single Image Super-Resolution Quality Assessment: A Real-World Dataset, Subjective Studies, and An Objective Metric, Qiuping Jiang, Zhentao Liu, Ke Gu, Feng Shao, Xinfeng Zhang, Hantao Liu, Weisi Lin, IEEE Transactions on Image Processing, 2022.  
You can change our program as you like and use it anywhere, but please refer to its original source and cite our paper. The following is a brief description of our work, please refer to our paper for more details.

# Abstract
Numerous single image super-resolution (SISR) algorithms have been proposed to reconstruct a high-resolution (HR) image from its low-resolution (LR) observation. However, the majority of these algorithms are only validated on synthetic data. So far, the lack of comprehensive human subjective study on large-scale real-world SISR datasets and accurate objective SISR quality assessment metrics makes it unreliable to truly understand the performance of different SISR algorithms on real-world data. We make the following attemps tackle these two issues. Firstly, we construct a real-world SISR quality dataset (i.e., *RealSRQ*) and conduct human subjective studies to compare the performance of the representative SISR algorithms. Secondly, we propose a objective metric, i.e., *KLTSRQA*, based on the Karhunen-Loeve Transform (KLT) to evaluate the quality of real-world SISR images in a no-reference (NR) manner. Experiments on our constructed *RealSRQ* and the latest synthetic SISR quality dataset (i.e., *QADS*) have demonstrated the superiority of our proposed *KLTSRQA* metric, achieving higher consistency with human subjective scores than relevant existing NR image quality assessment (NR-IQA) metrics.

# RealSRQ: A Real-World SISR Quality Dataset
## Real-Wold LR-HR Image Pairs
We aim to compare the performance of different SISR algorithms for real-world LR images. In this work, we collect the real-world LR images either from the RealSR dataset or captured by ourselves following the same method in RealSR, i.e., adjust the focal length of a fixed digital single-lens reflex camera (i.e., Canon 5D3). For each scene, images are taken using four focal lengths: 105mm, 50mm, 35mm, and 28mm. Images taken by the largest focal length are used to generate the HR images, and images taken by the other three focal lengths are used to generate the three LR versions. Overall, we collect 60 HR images and corresponding 60 LR images at three scaling factors, i.e., LR2, LR3, and LR4 respectively.
## SISR Algorithms
In this study, we evaluate 10 representative SISR algorithms, include BCI, ASDS, SPM, Aplus, AIS, SRCNN, CSCN, VDSR, SRGAN, and USRnet. The former five methods are non-deep methods while the latter five methods are deep learning-based SISR methods, and covers recent major publications in the field. As a result, we finally obtain 1620 SR images in total. The following table provides more details. 

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Table1.PNG" width="400" height="190"/><br/>

## Global Ranking of SISR Algorithms
We conduct a large scale pairwise comparison subjective study and perform a comprehensive analysis to quantify the performance of the SISR algorithms that we selected. We only generate comparison pairs from the same scene and the same scaling factor. We adopt the Bradley-Terry model to derive the global ranking of SISR algorithms from the corresponding pairwise comparison results. By applying the B-T model on each group, we can get a B-T score for each SISR result in this group. Then, we rank the evaluated SISR results/algorithms based on the average B-T scores, as shown in the following figure. It is easily to find that ASDS gets the highest B-T score at all scaling factors.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig2.PNG" width="863" height="227"/><br/>

For more comprehensive analysis on the subjective ratings, please refer to our paper.

# KLTSRQA: An Objective NR Quality Metric for SISR
## KLTSRQA
The flow chart of *KLTSRQA* is depicted in the following figure. The input of *KLTSRQA* is a to-be-evaluated SISR image and the output is an estimated quality score. For an input SISR image in the RGB format, we first convert it into the opponent color space and then perform a local mean subtraction and divisive normalization on each color channel to obtain three mean subtracted contrast normalized (MSCN) coefficient maps. The KLT is performed on the corresponding MSCN maps using the KLT kernels that we have constructed offline. Therefore, we can obtain three KLT coefficient matrices corresponding to the three opponent color channels. Based on the obtained KLT coefficient matrix for each channel, quality-aware feature extraction is performed from two aspects. On the first aspect, we use the asymmetric generalized Gaussian distribution (AGGD) model to fit the KLT coefficients in different spectral components and the estimated AGGD parameters are taken as the first part of features. On the second aspect, we compute the energy of the KLT coefficients in different spectral components as the second part of features. These two parts of features are combined together and aggregated over three channels to yield a final quality-aware feature vector for quality score prediction via the SVMrank model.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig8.PNG" width="618" height="288"/><br/>

## Experimental Results
### Algorithm Performance Test on RealSRQ
First, we test the performance of *KLTSRQA* on *RealSRQ*. To demonstrate the superiority of our method, 15 existing relevant NR-IQA metrics for comparison. The selected 15 NR-IQA metrics are GM-LOG, BLIINDS-II, CurveletQA, BRISQUE, OG-IQA, SSEQ, DIIVINE, RISE, BMPRI, FRIQUEE, NIQE, ILNIQE, HVS-MaxPol, PCRL, and SR-metric. Among these methods, NIQE, ILNIQE, and HVS-MaxPol are training-free while the rests are all training-based. For all the training-based methods, the regression functions are all implemented by SVMrank for fair comparison. The performance results of these algorithms are shown in the following table. As shown, *KLTSRQA* achieves the best performance in terms of all performance criteria, i.e., KROCC, SROCC, PLCC, and RMSE, at all three scaling factors. 

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Table3.PNG" width="739" height="287"/><br/>

The scatter plots of different metrics are shown in the following figure. We can observe that the proposed *KLTSRQA* metric is more in line with subjective B-T scores.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig9.PNG" width="756" height="576"/><br/>

### Algorithm Performance Test on QADS
In addition to *RealSRQ*, we also conduct performance test on a recently published synthetic SISR dataset *QADS* to more comprehensively validate the performance of *KLTSRQA*. The numerical performance results are shown in the following table. *KLTSRQA* still achieves the best numerical performance results (i.e., the highest PLCC, KROCC, and SROCC values, while the lowest RMSE value) on *QADS*. 

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Table4.PNG" width="320" height="340"/><br/>

The scatter plots are shown in the following figure. The scatter plot of *KLTSRQA* is also highly in line with the subjective scores, which further demonstrates its superiority and good robustness on different datasets.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig11.PNG" width="756" height="576"/><br/>

### Running Time
We test the running time of different NR-IQA metrics with the same setting and platform. The testing image is a 1200 × 800 color image in the RGB format. The experiments are all conducted on a PC with an AMD Ryzen 7 4800H@2.9GHZ CPU and 16GB RAM. The software platform is MATLAB R2018a. The running time comparison of different NR-IQA metrics can be found in the following table. It is observed that the proposed *KLTSRQA* is highly efficient, i.e., it only requires less than 0.5 second to process a 1200 × 800 color image.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Table5.PNG" width="1278" height="57"/><br/>

# Contact Us
If you have any problem of our program, please feel free to contact with the authors: jiangqiuping@nbu.edu.cn, zhentaolau@163.com.

# Download
You can download our constructed dataset and proposed software from  
BaiduYun disk: [*RealSRQ-KLTSRQA-released*](https://pan.baidu.com/s/15ZgfpW1b2_gMAETBUeszSg) (key:1121)  
Google Drive: 

