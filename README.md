# EEG-Emotion-Prediction
Brain-Computer Interface course project (Electroencephalography-Based Human Emotion Prediction Using Deep Learning).


<p align="center">
  <img width="600" height="179" src="https://user-images.githubusercontent.com/107177894/173532032-a972cb69-ed93-4452-bdf9-c37462af5fb7.png">
</p>



### Project Aims & Objectives:
The goal of this project is to provide electroencephalography (EEG) approaches for emotion recognition. EEG signals are collected from the brain’s scalp and analyzed in response to a variety of stimuli representing the three main emotions. Human emotions are varied and complex but can be generalized into positive, neutral, and negative categories.

<p align="center">
  <img width="500" height="292" src="https://user-images.githubusercontent.com/107177894/173532930-92e15549-2956-4b37-a463-20cf4a08fa0e.png">
</p>

### Dataset:
For this project, [EEG Brainwave Dataset: Feeling Emotions](https://www.kaggle.com/datasets/birdy654/eeg-brainwave-dataset-feeling-emotions) (which is publicly available) is used. Four dry extra-cranial electrodes via a commercially available MUSE EEG headband are employed to capture the EEG signal. Microvoltage measurements are recorded from the TP9, AF7, AF8, and TP10 electrodes which account for the Frontal and Temporal lobes of the brain. 60 seconds of data were recorded from two subjects (1 male, and 1 female, aged 20-22). For each of the 6 film clips producing 12 minutes (720 seconds) of brain activity data (6 minutes for each emotional state). 3 film clips produced negative emotions and 3 of them contained positive scenes. Among each state, subjects took a rest for one minute and their EEG signals are captured and labeled as neutral emotions. In addition, participants were forced to watch the emotional videos without making any conscious movements such as drinking coffee in order to prevent the influence of Electromyographic (EMG) signals on the data due to their prominence over brainwaves in terms of signal strength [1], [2].

<p align="center">
  <img width="350" height="337" src="https://user-images.githubusercontent.com/107177894/173533521-edb18a15-cde4-4e9d-844a-7a8cf27c2688.png">
</p>


### Preprocessing:
To sum up, This dataset contains 3 class labels for emotion (neutral, happy, and sad) and it is preprocessed some features were extracted as follows [3]:

### – Considering the full-time window:

• The sample mean and sample standard deviation of each signal (8 features).

• The sample skewness and sample kurtosis of each signal (8 features).

• The maximum and minimum value of each signal (8 features).

• The sample variances of each signal, plus the sample covariances of all
signal pairs (10 features).

• The eigenvalues of the covariance matrix (4 features).

• The upper triangular elements of the matrix logarithm of the covariance
matrix. (10 features)

• The magnitude of the frequency components of each signal, obtained
using a Fast Fourier Transform (FFT)  (300 features).

• The frequency values of the ten most energetic components of the FFT,
for each signal (40 features).

### – Considering the two half-windows:

• The change in the sample means and in the sample standard deviations
between the first and second half-windows, for all signals (8 features).

• The change in the maximum and minimum values between the first and
second half-windows, for all signals (8 features).

### – Considering the quarter windows:

• The sample mean of each quarter-window, plus all paired differences of sample means between the quarter windows, for all signals (56
features).

• The maximum (minimum) values of each quarter window, plus all paired
differences of maximum (minimum) values between the quarter windows, for all signals (112 features).



### Methods:
For doing this project, we implement 4 different networks (recurrent neural network (RNN), long short-term memory (LSTM), gated recurrent unit (GRU), and regular artificial neural network (ANN)) on TensorFlow 2.x in 4 different scenarios as follows:

***Case 1:*** All above features

***Case 2:*** Using just ***fast Fourier transform (FFT)*** features

***Case 3:*** All above features except FFT

***Case 4:*** Using Principal Component Analysis (PCA)


***Please note that for the first 3 cases, we didn't scale our data. However, for Case 4 since we used PCA as an extra preprocessing step, data needs to be rescaled***



### Getting Started:

First, you need to download [EEG Brainwave Dataset: Feeling Emotions](https://www.kaggle.com/datasets/birdy654/eeg-brainwave-dataset-feeling-emotions). Then, put it in the "BCI Final Project" folder. Finally, you can easily run each notebook.



### Results:

***In README***, we just show test accuracy for all methods in different cases. For other metrics such as ***confusion matrix, precision, recall, F1 score, etc***  of all proposed models, please open the notebook of each. ***Obviously in Case 4 which PCA is used as preprocessing step, training time is too much faster than in other Cases***. Moreover, we can definitely get better results with ANN by scaling in the first 3 Cases. 

![result_BCI](https://user-images.githubusercontent.com/107177894/172810498-0e0efdda-426c-4893-82a5-d8499b96399a.png)

Actually, in [3], some methods for EEG Emotion Prediction are used based on this dataset. You can see the result which is directly obtained from [3]. As you can see, using PCA + ANN can beat simple CNN for this task!

![result_BCI_2](https://user-images.githubusercontent.com/107177894/173227869-e12bb9cd-ba14-47fc-9b69-9b034423c77c.png)


### References:
[1] J. Bird, A. Ekart, C. Buckingham, and D. Faria. "Mental emotional sentiment classification with an EEG-based brain-machine interface." In Proceedings of theInternational Conference on Digital Image and Signal Processing (DISP’19). 2019.

[2] J. Bird, D. Faria, L. Manso, A. Ekárt, and C. Buckingham. "A deep evolutionary approach to bioinspired classifier optimisation for brain-machine interaction." Complexity 2019 (2019).

[3] J. Ashford, J. Bird, F. Campelo, and D. Faria. "Classification of EEG signals based on image representation of statistical features." In UK Workshop on Computational Intelligence, pp. 449-460. Springer, Cham, 2019.
