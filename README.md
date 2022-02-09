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


NEW IDEAS BY Xiaotian ZHANG:
My ideas are about the problems about the privacy and ethics in the process of realizing Face2Statistics. 
1. 
In the training powerpoint, there are two solutions mentioned as example. One is to do the prediction in a local way, and in this method the availability of a powerful enough computational hardware is under consideration. For it takes so much time to run the previous densenet+LSTM program in my own desktop, I realized the computation it needs to take when doing the prediction. My reading online for related paper also contributes to the conclusion that to add a portable enough local machine on vehicle be able to do such calculation is very hard in the present stage, and it may cause as much trouble to the driver as directly fixing those monitoring machines. 

2. 
So I change my view to data encryption. This way is much easier to realize compared to the previous one, as there have been so many different kinds of highly developed ways of encryption. But as so much work have been done in this field, I didn't come up with so much ideas realistic and worth saying.

3. 
So at last I change back to the local part. Adding additional machines to existing vehicle is not a easy work, but what if the cars were produced with a strong enough built-in computer. In the inner part of traditional cars fueling gas, so much space is utilized by the engine and its complex components. However, in the future, eletric vehicles will become the mainstream, and this makes it possible to popularize the built-in computer for every car. In addition, there are so much space left unlike the traditional, so the realization of local computation may be possible at that time. 
For my own point of view, the safest way of protecting privacy is to do it offline.