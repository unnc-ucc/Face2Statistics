# Face2Statistics
A comprehensive roadmap to deliver user-friendly, low-cost and effective alternatives for extracting drivers’  statistics. Full paper is accepted by HCII'22.

The WIP version is [here](https://github.com/unnc-ucc/Face2Multimodal).


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


