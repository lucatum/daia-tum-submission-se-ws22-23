# daia-tum-submission-se-ws22-23
submission of the team Luca (03703106), Max (03700525)&amp; Mathias (03659540)

----

**We provide 4 Jupyter Notebook: One LSTM Discrete, one LSTM Continuous, one GRU Discrete and one GRU Continuous**

---
Addtionally we provided all the Notebooks as PDF Versions
You will also find code in the PDF folder that documents our verification process to ensure that the model can handle single output rpms and does not interfere with training.

#Overview 

We developed a Deep Learning model that is able to predict the future power consumption of a single carrier of a motion system. The carrier moves horizontally back and forth in two different motion patterns: discrete and continuous. It can run at 20 different velocities. Thus, the datasets (xlsx files) contain 20 different time series of power consumption corresponding to speeds ranging between 100 and 2000 rpm. The data points have been collected with a time interval of 10 ms.

#Model description 

The Deep Learning models used in this data challenge are variants of the classical Recurrent Neural Network (RNN), namely LSTM and GRU. Both are used for each motion pattern, resulting in 4 separate scripts within this folder. The architecture follows an encoder-decoder structure: it exploits two layers of LSTM (or GRU respectively), with a repeat vector in between, followed by a time-distributed dense layer and a dense layer (output).

The dataset contains no outliers and does not require any form of cleaning process. For preparatory purposes, the data is split into train, test and validation sets (split sizes: 80%, 10% and 10%). After that, normalization using MinMaxScaler has been conducted, so that the sets have a range of 0 to 1. The scaled datasets are then reshaped into a 3D tensor and split into input X and output Y. By making use of the sliding window approach, the input sets have a lookback window of 40 data points whereas the outputs have a window size of 20. The latter represents the length of the forecast. In summary, we follow a multiple input – multiple output (MIMO) strategy.

#Validity tests 

In order to test the models on their performance (independent of their prediction accuracy, which has been evaluated within the respective scripts), separate validation tests have been conducted:

Training and testing on 19 randomly generated and 1 real time series 

Test on 19 random generated and 1 real time series after Training with the original data.

Test with the time series with swapped positions within the initial data frame after Training with the original data.

#Final Remarks 

The sections in the scripts are documented in order to provide a sufficient guide through the individual steps from the file load to the final evaluation plots. 
