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
We adopt the Bradley-Terry model to derive the global ranking of SISR algorithms from the corresponding pairwise comparison results. By applying the B-T model on each group, we can get a B-T score for each SISR result in this group. Then, we rank the evaluated SISR results/algorithms based on the average B-T scores, as shown in the following figure.

<img src="https://github.com/Zhentao-Liu/RealSRQ-KLTSRQA/blob/main/images/Fig2.PNG" width="863" height="227"/><br/>


# KLTSRQA
In our paper, we demonstrate that the existing objective metrics can not precisely evaluated the SISR results. To solve this problem, we propose a new objective metric, i.e., KLTSRQA, based on the Karhunen-Loeve Transform (KLT) to evaluate the quality of real-world SISR images accurately. The extensive experiments in our paper demonstrate that KLTSRQA is highly consistent with human perception.

# References

# Download
You can download our constructed dataset [*RealSRQ*](https://pan.baidu.com/s/14yuztHcMpej5OyNMBvK3BA) (key:1121) on BaiduYun disk. As long as our paper is published, we will upload our software *KLTSRQA*. To be continued.
