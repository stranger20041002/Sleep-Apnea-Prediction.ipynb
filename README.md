# Sleep Apnea Detection Using CNN–Transformer

## Overview

This project explores ECG-based sleep apnea prediction using deep learning. It uses electrocardiogram (ECG) signals from the Apnea-ECG dataset to classify signal segments as either normal or preceding an apnea event.

The model combines Convolutional Neural Networks (CNNs) for extracting local signal features with a Transformer encoder for learning temporal relationships.

## Objectives

- Process ECG signals into fixed-length segments.
- Identify patterns associated with upcoming sleep apnea events.
- Build a CNN–Transformer binary classification model.
- Evaluate model performance using stratified 5-fold cross-validation.

## Technologies Used

- Python
- PyTorch
- NumPy
- Matplotlib
- WFDB
- Scikit-learn
- Google Colab

## Dataset

The project uses the Apnea-ECG dataset, containing ECG recordings and apnea annotations.

The notebook processes selected records from three groups:

- `a01`–`a20`: Apnea group
- `b01`–`b05`: Borderline group
- `c01`–`c10`: Control group

ECG signals are sampled at 100 Hz and segmented into 40-second windows with a 15-second sliding step.

The classification focuses on distinguishing normal segments from segments preceding apnea events. Actual apnea segments are excluded from this binary classification.

Dataset source: [PhysioNet Apnea-ECG Database](https://physionet.org/content/apnea-ecg/)

## Model Architecture

The CNN–Transformer model consists of:

1. **CNN feature extraction:** Three convolutional blocks using Conv1D, Batch Normalization, and ReLU activation.
2. **Transformer encoder:** Learns relationships between extracted temporal features using multi-head self-attention.
3. **Classification head:** Produces a prediction score for the target class.

## Training and Evaluation

The notebook uses:

- Stratified 5-fold cross-validation
- Adam optimizer
- Binary cross-entropy with logits and positive-class weighting
- Training, validation, and testing splits within each fold

Performance is evaluated using:

- Accuracy
- Sensitivity (Recall)
- F1-score
- Confusion matrix
- Training and validation loss curves

## How to Run

1. Open the notebook in Google Colab.
2. Mount Google Drive when prompted.
3. Download the Apnea-ECG dataset from PhysioNet and place the required records and annotations in the configured data directory.
4. Update `DATA_DIR` in the notebook to match your dataset location.
5. Install the required dependencies.
6. Run the notebook cells in order to preprocess the signals, train the model, and evaluate its performance.

## Outputs

The notebook is designed to generate:

- Sample ECG epoch visualizations
- Training and validation loss curves
- Confusion matrix
- Performance comparison across cross-validation folds
- A saved model checkpoint (`cnn_transformer_apnea.pt`)

## Limitations

This is an experimental machine learning project. Its results depend on the dataset, preprocessing, validation methodology, and model configuration. It has not been established as a clinically validated diagnostic system.

The model should not be used to diagnose sleep apnea or make medical decisions.

## Author

Add your name and GitHub profile here.
