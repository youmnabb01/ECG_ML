# ECG Classification Project

This project focuses on classifying electrocardiogram (ECG) signals into three categories: Normal Sinus Rhythm (NSR), Arrhythmia (ARR), and Congestive Heart Failure (CHF). The goal is to develop a machine learning model using feature engineering to distinguish between these categories based on ECG data. The steps involve preprocessing, R-peak detection, feature extraction, feature selection, and classification. 

## Contributors
Youmna Abboud, Diana Al Bazze

This project was completed at **TU Delft** as part of the **Introduction to Machine Learning** course.


## Project Structure

- **Introduction**: Overview of the problem, dataset, and methodology.
- **Methods**: Description of data preprocessing, feature extraction, dimensionality reduction, and classification techniques.
- **Results**: Performance evaluation of the models used.
- **Discussion and Conclusion**: Summary and insights from the results.

## Dataset

The dataset used in this study is sourced from the [PhysioNet](https://physionet.org/) repositories and consists of 162 ECG recordings. These recordings are divided into three categories:
- 96 recordings from patients with arrhythmia (ARR).
- 30 recordings from patients with congestive heart failure (CHF).
- 36 recordings from patients with normal sinus rhythm (NSR).

The data has been preprocessed as follows:
- Scaling defined in the PhysioNet `.info` files has been applied.
- The recordings have been resampled to a common rate of 128 Hz.
- Each data file consisting of two ECG recordings has been separated into two separate records.
- The data length was truncated to 65536 samples.

## Methods

### Data Preprocessing

The ECG data is bandpass filtered using a Butterworth filter to remove noise from both high and low-frequency components. A frequency range of 0.5 Hz to 40 Hz is chosen, as this is the typical range for ECG signals.

### R-Peak Detection

R-peaks are detected using the Pan-Tompkins algorithm. These peaks are crucial for understanding the rhythm of the heart and are used in subsequent feature extraction.

### Feature Extraction

The following features are extracted from the R-peaks for each ECG recording:
- **Heart rate (HR)**: Maximum, minimum, mean, and standard deviation.
- **Root mean square of successive differences (RMSSD)**.
- **Number of pairs of successive normal heartbeats differing by more than 20 ms (NN20)**.
- **Standard deviation of successive RR intervals (SDSD)**.
- **Successive differences of R-peaks**: Maximum, minimum, mean, and standard deviation.

These features provide valuable information about the heart's rhythm and variability, which is important for classifying ECG signals.

### Dimensionality Reduction

Principal Component Analysis (PCA) is applied to reduce the dimensionality of the feature space. This helps in retaining the most important features while discarding less informative ones.

### Classification

Multiple classification models are trained on the extracted features:
1. **Support Vector Machine (SVM)**: A linear classifier for binary classification tasks.
2. **Perceptron**: A simple neural network model used for classification.
3. **Softmax Regression**: A multinomial logistic regression model.
4. **Logistic Regression**: A regularized linear model used for classification.

The models are trained on 70% of the data and evaluated on the remaining 30%.

### Performance Evaluation

The models are evaluated based on their accuracy, and the confusion matrix is used to further analyze the performance. A heatmap of the confusion matrix is generated to visualize the misclassifications.

## Results

In this study, we trained and evaluated four different machine learning classifiers: Support Vector Machine (SVM), Perceptron, Softmax Regression, and Logistic Regression, on the extracted ECG features to classify the recordings into three categories: Normal Sinus Rhythm (NSR), Arrhythmia (ARR), and Congestive Heart Failure (CHF).

### Performance Evaluation

The models were trained on 70% of the dataset and tested on 30%. Accuracy was used as the primary evaluation metric, and a confusion matrix was generated to assess the performance of each model.

The following are the accuracy scores for each classifier:

- **SVM Accuracy**: 0.85
- **Perceptron Accuracy**: 0.82
- **Softmax Accuracy**: 0.87
- **Logistic Regression Accuracy**: 0.88

### Confusion Matrix

A confusion matrix was computed for the best-performing classifier, Logistic Regression, to evaluate how well the model predicted each class. The matrix visualizes the number of true positive, false positive, true negative, and false negative predictions for each class.


