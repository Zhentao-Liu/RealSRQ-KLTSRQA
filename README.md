# Towards Evaluating Single Image Super-Resolution Algorithms: A Real-World Dataset, Subjective Studies, and An Objective Metric
This is the brief description of RealSRQ dataset and KLTSRQA software. For more details, please refer to our paper "Towards Evaluating Single Image Super-Resolution Algorithms: A Real-World Dataset, Subjective Studies, and An Objective Metric". You can change our program as you like and use it anywhere, but please refer to its original source and cite our paper.

# Abstract
Numerous single image super-resolution (SISR) algorithms have been proposed to reconstruct a high-resolution (HR) image from its low-resolution (LR) observation. However, the majority of these algorithms are only validated on synthetic data. So far, the lack of comprehensive human subjective study on large-scale real-world SISR datasets and accurate objective SISR quality assessment metrics makes it unreliable to truly understand the performance of different SISR algorithms on real-world data. We make the following attemps tackle these two issues. Firstly, we construct a real-world SISR quality dataset (i.e., *RealSRQ*) and conduct human subjective studies to compare the performance of the representative SISR algorithms. Secondly, we propose a objective metric, i.e., *KLTSRQA*, based on the Karhunen-Loeve Transform (KLT) to evaluate the quality of real-world SISR images in a no-reference (NR) manner. Experiments on our constructed *RealSRQ* and the latest synthetic SISR quality dataset (i.e., *QADS*) have demonstrated the superiority of our proposed *KLTSRQA* metric, achieving higher consistency with human subjective scores than relevant existing NR image quality assessment (NR-IQA) metrics.

# RealSRQ: A Real-World SISR Quality Dataset
## Real-Wold LR-HR Image Pairs
The complex and authentic distortions in the real-world LR images will provide a huge challenge to the SISR algorithms and quality metrics. Thus, the acquisition of real-world LR images is the keypoint in constructing *RealSRQ*. In this work, we collect the real-world LR images either from the *RealSR* dataset or captured by ourselves following the same method in *RealSR*, i.e., adjust the focal length of a fixed digital single-lens reflex camera (i.e., Canon 5D3). For each scene, images are taken using four focal lengths: 105mm, 50mm, 35mm, and 28mm. Images taken by the largest focal length are used to generate the HR images, and images taken by the other three focal lengths are used to generate the three LR versions. Overall, we collect 60 HR images and corresponding 60 LR images at three scaling factors, i.e., LR2, LR3, and LR4 respectively. According to scene type, each scene is annotated with one of the following attributes: *Building*, *Manmade*, *Natural*, *People*, *Landscape*, and *Text*.
## SISR Algorithms
In this study, we evaluate 10 representative SISR algorithms, include BCI, ASDS, SPM, Aplus, AIS, SRCNN, CSCN, VDSR, SRGAN, and USRnet. The former five methods are non-deep methods while the latter five methods are deep learning-based SISR methods, and covers recent major publications in the field. As a result, we finally obtain 1620 SR images in total. The following table provides more details. 

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Table1.PNG" width="400" height="190"/><br/>

## Human Subjective Study
We also conduct a large scale pairwise comparison subjective study and perform a comprehensive analysis to quantify the performance of the SISR algorithms that we selected. We only generate comparison pairs from the same scene and the same scaling factor. The study is performed via a customized GUI which is shown as follows.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig1.PNG" width="422" height="241"/><br/>

The top two row presents two SISR results to be compared. The HR image is shown in the bottom-left window. The bottom-right window is used to show these three images for finer comparison. Users can switch different images by pressing the three buttons "HR", "SR1", "SR2" below the bottom-right window. Finally, users can make their choices by pressing the corresponding button below the SR image windows to submit a binary preference label, i.e., "1" or "-1". There are 60 subjects participant our user study and we divide them into 6 group, i.e., 10 subjects per group. Each group is responsible for one scene type attribute group and as a result, we get 65400 votes totally. What's more, we are interesting in asking the participants "Why don't you like another picture?" to get more insight on the pros and cons of different SISR algorithms. We provide nine reasons to form the questionnaire, as shown in the following table. 

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Table2.PNG" width="410" height="219"/><br/>

## Subjective Study Result Analysis
### Global Ranking of SISR Algorithms
We adopt the Bradley-Terry model to derive the global ranking of SISR algorithms from the corresponding pairwise comparison results. By applying the B-T model on each group, we can get a B-T score for each SISR result in this group. Then, we rank the evaluated SISR results/algorithms based on the average B-T scores, as shown in the following figure. It is easily to find that ASDS gets the highest B-T score at all scaling factors.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig2.PNG" width="863" height="227"/><br/>

### Convergence Analysis
We perform convergence analysis from two perspectives: the number of votes and the number of images to demonstrate that the number of votes and images are sufficient to obtain stable subjective rating scores.
#### Number of votes
We collect 65400 votes in total. There are 27000 votes for LR2, 21600 votes for LR3 and 16800 votes for LR4. We randomly sample *a* (*a*=1000,3000,6000,9000,12000,15000) votes from all votes at each scaling factor, and compute B-T score. We repeat this process 1000 times for each *a*.  The following figure shows the mean and standard deviation of B-T scores for each *a* for LR4. Obviously, with the increasing of the number of votes, standard deviation of B-T scores decreases, indicating the subjective rating scores tend to be stable.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig3.PNG" width="409" height="291"/><br/>

#### Number of votes
We collect 60 HR images in total. We randomly sample *a* (*a*=5,15,25,35,45,55) HR images from our dataset and compute B-T score for each SISR algorithm at each scaling factor. We repeat this process 1000 times for each *a*.  The following figure shows the mean and standard deviation of B-T scores for each *a* for LR4. Obviously, with the increasing of the number of images, standard deviation of B-T Scores decreases, indicating the subjective rating scores tend to be stable.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig4.PNG" width="409" height="291"/><br/>

### Significance Test
We apply significance test to classify the evaluated algorithms based on the difference of the subjective votes. The following figure shows the grouping results for LR2. Algorithm's performance decreases from left to right. ASDS and USRnet always fall into first and second ranking groups.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig5.PNG" width="381" height="220"/><br/>

### Human Preference Analysis
This part analyzes the results collected in the additional questionnaire during the human subjective study. We show the vote percentages of all the reasons for LR2 in the following figure. The *i*-th element in each row represents the vote percentage of the Reason #*i* for corresponding SISR algorithm in this row. In general, Reason #2 gets the highest vote percentage and Reasons #3, #5, #7 get relatively higher vote percentage than the rest reasons. 

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig6.PNG" width="361" height="206"/><br/>

# KLTSRQA: An Objective NR Quality Metric for SISR
## Motivation
As shown above, the distortions on macro-structures (e.g., edges and contours) and micro-structures (e.g., texture and details) are the main factors affecting the visual quality of SISR results. The KLT coefficients in different spectral components actually account for different image components, i.e., the front part of spectral components in the KLT coefficient matrix accounts for macro-structures while the latter part accounts for micro-structures. We shown this characteristic in the following figure which demonstrates the image reconstruction process.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig7.PNG" width="914" height="457"/><br/>

In this work, we decompose the original image into 64 KLT spectral components. In the above figure, (a) is the original image, (b)-(h) are the reconstructed images by using the former *k* spectral components, and *k* = 1, 2, 4, 8, 16, 32, 64, respectively. As shown in (b), when only the 1-st spectral component is involved in the reconstruction process, almost all the macro-structures such as the basic contours and structures are recovered. However, many small textures and fine details are missing. As *k* increases, the small textures and fine details are becoming richer and clearer. As shown in (f), when we take the former 16 spectral components to perform reconstruction, the visual quality of the reconstructed image is comparable with that of the original image. These observations verify the characteristic of KLT spectral components. Therefore, in this work we are inspired to extract quality-aware features from different spectral components to more accurately evaluate SISR image quality in a NR manner.
## KLTSRQA
The flow chart of KLTSRQA is depicted in the following figure. The input of KLTSRQA is a to-be-evaluated SISR image and the output is an estimated quality score. For an input SISR image in the RGB format, we first convert it into the opponent color space and then perform a local mean subtraction and divisive normalization on each color channel to obtain three mean subtracted contrast normalized (MSCN) coefficient maps. The KLT is performed on the corresponding MSCN maps using the KLT kernels that we have constructed offline. Therefore, we can obtain three KLT coefficient matrices corresponding to the three opponent color channels. Based on the obtained KLT coefficient matrix for each channel, quality-aware feature extraction is performed from two aspects. On the first aspect, we use the asymmetric generalized Gaussian distribution (AGGD) model to fit the KLT coefficients in different spectral components and the estimated AGGD parameters are taken as the first part of features. On the second aspect, we compute the energy of the KLT coefficients in different spectral components as the second part of features. These two parts of features are combined together and aggregated over three channels to yield a final quality-aware feature vector for quality score prediction via the SVMrank model.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig8.PNG" width="618" height="288"/><br/>

## Experimental Results
### Algorithm Performance Test on *RealSRQ*
First, we test the performance of *KLTSRQA* on *RealSRQ*. To demonstrate the superiority of our method, 15 existing relevant NR-IQA metrics for comparison. The selected 15 NR-IQA metrics are GM-LOG, BLIINDS-II, CurveletQA, BRISQUE, OG-IQA, SSEQ, DIIVINE, RISE, BMPRI, FRIQUEE, NIQE, ILNIQE, HVS-MaxPol, PCRL, and SR-metric. Among these methods, NIQE, ILNIQE, and HVS-MaxPol are training-free while the rests are all training-based. For all the training-based methods, the regression functions are all implemented by SVMrank for fair comparison. The performance results of these algorithms are shown in the following table. As shown, *KLTSRQA* achieves the best performance in terms of all performance criteria, i.e., KROCC, SROCC, PLCC, and RMSE, at all three scaling factors. 

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Table3.PNG" width="739" height="287"/><br/>

The scatter plots of different metrics are shown in the following figure. We can observe that the proposed *KLTSRQA* metric is more in line with subjective B-T scores.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig9.PNG" width="756" height="576"/><br/>

To further demonstrate the superiority of *KLTSRQA*, we also conduct the statistical significance test by using the data of SROCC values. The following figure presents the t-test results, where the value 1/-1 indicates that row algorithms perform statistically better/worse than the column algorithms while the value 0 indicates that row algorithms perform statistically competitive with the column algorithms. As we can see, *KLTSRQA* performs statistically better than all the competing NR-IQA metrics on *RealSRQ*, which further prove the superiority of *KLTSRQA*.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig10.PNG" width="391" height="290"/><br/>

### Algorithm Performance Test on *QADS*
In addition to *RealSRQ*, we also conduct performance test on a recently published synthetic SISR dataset *QADS* to more comprehensively validate the performance of *KLTSRQA*. The numerical performance results are shown in the following table. *KLTSRQA* still achieves the best numerical performance results (i.e., the highest PLCC, KROCC, and SROCC values, while the lowest RMSE value) on *QADS*. 

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Table4.PNG" width="400" height="300"/><br/>

The scatter plots are shown in the following figure. The scatter plot of *KLTSRQA* is also highly in line with the subjective scores, which further demonstrates its superiority and good robustness on different datasets.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig11.PNG" width="756" height="576"/><br/>

The following figure presents the t-test results. It is seen that *KLTSRQA* performs statistically better than almost all the competing NR-IQA metrics.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig12.PNG" width="391" height="290"/><br/>

# Download
You can download our constructed dataset [*RealSRQ*](https://pan.baidu.com/s/14yuztHcMpej5OyNMBvK3BA) (key:1121) on BaiduYun disk. As long as our paper is published, we will upload our software *KLTSRQA*. To be continued.
