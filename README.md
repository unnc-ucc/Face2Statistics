# Face2Statistics
A comprehensive roadmap to deliver user-friendly, low-cost and effective alternatives for extracting drivers’  statistics. Full paper is accepted by HCII'22.

The WIP version is [here](https://github.com/unnc-ucc/Face2Multimodal).

**Procedure**

![pipeline-optimize](./fig/pipeline-optimize.png)

Input

Raw video streams (facial expressions contains many noisy pixels)

Step1

Pre-processing input images to retrieve only the facial expressions and enhance the performance of Face2Statistics

Step2

Exploring different deep neural network-driven predictors

  First Attempt: Convolution Neural Networks (CNNs) 

  Second Attempt: Long Short-Term Memory (LSTM) Recurrent Neural Network (RNN) 

  Third Attempt: Bidirectional Long-Short-Term Memory (BiLSTM) Recurrent Neural Network (RNN)

Step3

Visualizing predicted result

Output

Two optimization

a) We utilize HSV color space instead of RGB color space to reduce the variance of illumination among different pixels.

b) We apply personalized parameters via pearson correlation coefficients to conditional random field to realize customizing.



**Experiment Results**

a) Comparisons among Different Neural Network Models

 The results of training and validation accuracy, in terms of DenseNet, LSTM and BiLSTM are displayed as follows.

![rgb(train)](./fig/rgb(train).png)

![rgb](./fig/rgb.png)

b) Comparisons between Different Color Models

The results of training and validation accuracy, in terms of RGB and HSV are displayed as follows.

![rgb2hsv(train)](./fig/rgb2hsv(train).png)

![rgb2hsv](./fig/rgb2hsv.png)

c) Comparisons between Models w/ or w/out CRF

The results of s the comparative validation accuracy of BiLSTM w/ and w/out CRF support for four different drivers are displayed as follows.

![crf-result](./fig/crf-result.png)



**Contributor**

Zeyu Xiong, Jiahao Wang, Wangkai Jin, Junyu Liu, Yicun Duan, Zilin Song, Xiangjun Peng
