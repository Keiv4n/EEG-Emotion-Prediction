# EEG-Emotion-Recognition
Brain-Computer Interface course project (Electroencephalography-Based Human Emotion Prediction Using Deep Learning).

### Project Aims & Objectives:
The goal of this project is to provide electroencephalography (EEG) approaches for emotion recognition. EEG signals are collected from the brain’s scalp and analyzed in response to a variety of stimuli representing the three main emotions. Human emotions are varied and complex but can be generalized into positive, neutral and negative categories.

### Dataset:
For this project, [EEG Brainwave Dataset: Feeling Emotions](https://www.kaggle.com/datasets/birdy654/eeg-brainwave-dataset-feeling-emotions) (which is publicly available) is used. Four dry extra-cranial electrodes via a commercially available MUSE EEG headband are employed to capture EEG signal. Microvoltage measurements are recorded from the TP9, AF7, AF8, and TP10 electrodes which account for Frontal and Temporal lobes of the brain. 60 seconds of data were recorded from two subjects (1 male, 1 female, aged 20-22). For each of the 6 film clips producing 12 minutes (720 seconds) of brain activity data (6 minutes for each emotional state). 3 film clips produced negative emotions and 3 of them contained positive scene. Among each states, subjects took a rest for one minutes and their EEG signals are captured and labeled as neutral emotion. In addition, participants were forced to watch the emotional videos without making any conscious movements such as drinking coffee in order to prevent the influence of Electromyographic (EMG) signals on the data due to their prominence over brainwaves in terms of signal strength.

To sum up, This dataset contains 3 class label for emotion (neutral, happy, and sad) and it is preprocessed and some featues were extracted as follows:


### Methods:
For doing this project, we implement 4 different networks (recurrent neural network (RNN), long short-term memory (LSTM), gated recurrent unit (GRU), and regular artificial neural network (ANN)) in 4 different scenarios as follows:

***Case 1:*** All above features

***Case 2:*** Using just ***fast Fourier transform (FFT)*** features

***Case 3:*** All above featues except FFT

***Case 4:*** Using Principal Component Analysis (PCA)


***Please note that for first 3 cases, we didn't scale our data. However, for Case 4 since we used PCA as an extra preprocessing step, data needs to be rescaled***


### Getting Started:


### Results:

***In README***, we just show test accuracy for all methods in different cases. For other metrics such as ***confusion matrix, precision, recall, F1 score, etc***  of all proposed models, please open the notebook of each. ***Obviously in for Case 4 which PCA is used as preprocessing step, training-time is too much faster than other Cases***. Moreover, we can definitely get better results with ANN by scaling in first 3 Cases. 

![result_BCI](https://user-images.githubusercontent.com/107177894/172810498-0e0efdda-426c-4893-82a5-d8499b96399a.png)
