# Exoplanet Transit Detection from Kepler Light Curves

This project detects exoplanet transit signals from stellar light curves using supervised deep learning. The task is framed as a binary classification problem (transit vs non-transit) on time-series photometric data derived from the Kepler mission.

The goal is to build a robust, reproducible pipeline that can identify transit-like signatures while controlling false positives, suitable for large-scale survey data.

---

## Dataset

- **Source:** Kepler labeled light-curve dataset  
- **Data type:** Stellar flux time-series  
- **Labels:** Transit / Non-transit  
- **Characteristics:** Noisy, uneven astrophysical signals with instrumental trends and stellar variability

Only labeled Kepler data is used in this project; no simulated light curves are included.

---

## Methodology

### Preprocessing
- Median normalization of flux
- Detrending using Savitzky–Golay filtering
- Gaussian smoothing to suppress high-frequency noise
- Robust scaling using Median Absolute Deviation (MAD)
- Downsampling to fixed-length sequences for CNN compatibility

### Model
- 1D Convolutional Neural Network implemented in **PyTorch**
- Convolution + pooling blocks to capture local transit features
- Fully connected layers for final classification

### Training Strategy
- Stratified K-Fold cross-validation to handle class imbalance
- Class-weighted cross-entropy loss
- Adam optimizer with learning-rate scheduling

---

## Evaluation

Model performance is evaluated using:
- ROC-AUC
- Precision, Recall, and F1-score
- Confusion matrices on out-of-fold predictions

To assess model reliability, example true positives and false positives are visualized directly on light curves.

---

## Results

- The model successfully learns transit-like features from Kepler photometry
- Cross-validation demonstrates stable performance across folds
- Diagnostic plots highlight common false-positive patterns for follow-up vetting

---

