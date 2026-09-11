\# Deep Learning for Classification of Aerial Targets using Radar Micro-Doppler Signatures



\## Overview



This project focuses on classifying aerial targets using radar Micro-Doppler spectrograms and a Convolutional Neural Network (CNN).



The main objective is to investigate whether synthetic radar spectrograms generated using a Conditional Generative Adversarial Network (cGAN) can help train an aerial target classification model when only a very small amount of real training data is available.



The CNN is trained using a combination of:



\- GAN-generated synthetic spectrograms

\- A small subset of real radar spectrograms



The trained classifier is then tested on a separate real radar dataset to evaluate how well it generalizes to real-world data.



\---



\## Objective



The project aims to:



\- Classify different types of aerial targets from radar Micro-Doppler spectrograms.

\- Use synthetic spectrograms to supplement limited real training data.

\- Train a CNN using synthetic data combined with a small amount of real data.

\- Evaluate the trained model on real radar data.

\- Analyze classification performance using standard evaluation metrics.



\---



\## Target Classes



The dataset contains six aerial target classes:



1\. `3\_long\_blade\_rotor`

2\. `3\_short\_blade\_rotor`

3\. `Bird`

4\. `Bird+mini-helicopter`

5\. `RC\_plane`

6\. `drone`



\---



\## Dataset and Training Strategy



The project uses radar Micro-Doppler spectrogram images.



\### Training Data



The CNN training dataset consists of:



\- GAN-generated synthetic spectrograms

\- A very small amount of real spectrograms



This combined training approach is intended to improve the availability and diversity of training samples while reducing dependence on large amounts of real-world data.



\### Testing Data



The trained CNN is evaluated using real radar spectrogram data.



This provides a more realistic evaluation of the model's ability to classify actual radar observations.



\### Image Processing



Images are resized to:



`224 × 224`



The dataset is loaded using TensorFlow/Keras image dataset utilities with a batch size of:



`32`



\---



\## CNN Architecture



The classification model is a Convolutional Neural Network consisting of multiple convolutional blocks.



The architecture includes:



\- Convolutional layers

\- Batch Normalization

\- Max Pooling

\- Dropout

\- Flatten layer

\- Fully Connected (Dense) layer

\- L2 regularization

\- Softmax output layer



The convolutional layers progressively extract visual features from the radar spectrograms, while the final layers perform multi-class classification.



The network uses:



\- Adam optimizer

\- Sparse Categorical Crossentropy loss

\- Early Stopping

\- Model Checkpointing

\- Learning Rate Reduction



\---



\## Training Pipeline



The overall workflow is:



```text

Real Radar Dataset

&#x20;       │

&#x20;       ├───────────────┐

&#x20;       │               │

&#x20;       ▼               ▼

&#x20;Small Real Data    cGAN-generated Data

&#x20;       │               │

&#x20;       └───────┬───────┘

&#x20;               ▼

&#x20;      Combined Training Data

&#x20;               │

&#x20;               ▼

&#x20;         CNN Classifier

&#x20;               │

&#x20;               ▼

&#x20;       Trained Classification Model

&#x20;               │

&#x20;               ▼

&#x20;      Real Radar Test Dataset

&#x20;               │

&#x20;               ▼

&#x20;         Model Evaluation

