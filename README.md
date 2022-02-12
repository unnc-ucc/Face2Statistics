# Face2Statistics
A comprehensive roadmap to deliver user-friendly, low-cost and effective alternatives for extracting drivers’  statistics. Full paper is accepted by HCII'22.

The WIP version is [here](https://github.com/unnc-ucc/Face2Multimodal).


# Better Encoding Scheme
## Background
This paper has mentioned that using HSV color space instead of RGB to deal with the issue that illumination change influences three channels of RGB significantly. In this regard, for HSV color space only saturation and value changes, fluctuation on hue channel has been minimized.

## Similar approach: HSL
Like HSV color space, HSL (Hue, Saturation, Lightness) seems to provide an analogous method to solve this issue. The HSL representation models the way different paints mix to create color in the real world, with the lightness dimension resembling the varying amounts of black or white paint in the mixture. The difference between HSL and HSV is that a color with maximum lightness in HSL is pure white, but a color with maximum value/brightness in HSV is analogous to shining a white light on a colored object. 
Many researchers put forward improvement methods based on HSL. Su et al (2019) propose an improved method that adding flexible combinations of weight coefficient for HSL can achieve different results. In addition to the combination with Simple linear iterative clustering (SLIC) algorithm to improve accuracy and efficiency, Patrascu (2013) proposes a construction of a new distance in the HSL color space by a combination of the distances of HSL scalar components and by using the fuzzy c-means framework to derive a fuzzy color clustering method.

## Better technique: CIELAB
While HSL and HSV serve well enough to choose a single color, they ignore much of the complexity of color appearance. HSL and HSV are simple transformations of RGB which preserve symmetries in the RGB cube unrelated to human perception. As a more perceptually uniform space, CIELAB can show that different colors do not have the same lightness or chroma, or evenly spaced hues. It expresses color as three values: L* for perceptual lightness, and a* and b* for the four unique colors of human vision: red, green, blue, and yellow. Unlike the RGB color models, CIELAB is designed to approximate human vision. The L* component closely matches human perception of lightness. The most remarkable thing is that CIELAB is less uniform in the color axes but is useful for predicting small differences in color.
Using CIELAB with some technic has number of advantages in image process of different light intensities. For example, Tseng and Lee (2018) mention that the intensity component on CIELAB space is amplified by using the power law transform (PLT). Next, an image fusion method is used to combine several PLT-based enhanced images to obtain the final enhanced image. In addition to being used for enhancing image, the detection and removal of shadow is also a feasible application. According to Zhang, Zheng and Zheng (2014), a new scheme based on CIELAB color space is given and by this way, the limitation to the faint color is overcome by its inherent sensitive to the luminance. At the same time, the shadow removal can be optimized by using Susan operator, which based on the distinguished texture feature.


## References
C. -C. Tseng and S. -L. Lee, 2018. A Low-Light Color Image Enhancement Method on CIELAB Space. IEEE 7th Global Conference on Consumer Electronics (GCCE), 2018, pp. 141-142, doi: 10.1109/GCCE.2018.8574809. 
Haiying Zhang, Qirong Zheng, and Guiwen Zheng, 2014. A New Shadow Removal Algorithm Based on Susan and CIELAB Color Space. In Proceedings of International Conference on Internet Multimedia Computing and Service (ICIMCS '14). Association for Computing Machinery, New York, NY, USA, 222–225. DOI: https://doi.org/10.1145/2632856.2632878
Patrascu, V., 2013. New Framework of HSL System Based Color Clustering Algorithm. Proceedings of the 8th conference of the European Society for Fuzzy Logic and Technology, EUSFLAT-13. Available at: https://www.atlantis-press.com/proceedings/eusflat-13/8426.
Su F., Xu H., Chen G., Wang Z., Sun L., Wang Z., 2019. Improved Simple Linear Iterative Clustering Algorithm Using HSL Color Space. Robotics and Applications. ICIRA 2019. Lecture Notes in Computer Science, vol 11744. Springer, Cham. https://doi.org/10.1007/978-3-030-27541-9_34.




# INTRODUCTION TO F2S
## Introduction
Nowadays, as the development of extracting in-vehicle drivers’ statistics, there are some problems in practice. Uncomfortable driving experience with lots of sensors equipped and high costs make it necessary to find an effective alternative. Therefore, as a comprehensive roadmap to deliver user-friendly, low-cost, and effective alternatives, Face2Statistics is introduced for extracting drivers’ statistics. The key idea of Face2Statistics is leveraging each frame of facial expressions to predict instant statuses of in-vehicle drivers. 


## Designs and Implementations

### Component 1: Facial Expressions from Video Streams
OpenCV library, a state-of-the-art image processing library, is leveraged to implement this component.

### Component 2: Deep Neural Network-driven Predictors
The core component of Face2Statistics is the Deep Neural Network-driven predictors. There are three models which respectively are CNNs, LSTM-RNN, and BiLSTM-RNN.
* BiLSTM, LSTM and DenseNet achieves the best validation accuracy, in terms of Skin Conductivity, Heart Rate and Vehicle Speed respectively.
* BiLSTM has an advantage in terms of the structure of Skin Conductivity.
* The lowest precision of training accuracy occurs, when applying LSTM for Heart Rate prediction.

### Component 3: Visualization/Exportation of Predicted Results
Three parts of this component:
1. Basic data-processing component for reorganizing/streaming results into flat files, to serve as system logs/records.
2. High-level API. Other systems can directly deploy Face2Statistics via a simple function call.
3. Visualization example using the API, to justify the feasibility of visualizations.


## Experimental Methodology
* OpenCV library is used for data pre-processing.
* Tensorflow is used for all different Neural Network Models and the CRF model.
* BROOK dataset, an open-sourced and multi-modal dataset with facial videos for adaptive and personalized Human-Vehicle Interaction designs, is used to evaluate Face2Statistics.


## Model Limitations
* Currently only a general driving scenario in the dataset is considered. If more information needs to be considered, this requires a high degree of adaptation of the data set for re-collection.
* Different angle of facial expression video streams may also be a factor that affects the processing of facial expressions.