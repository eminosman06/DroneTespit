# Drone Detection 🚁

This project is a Pattern Recognition course project from January 2025. It aims to detect drones using image-based pattern recognition techniques. In this study, various image processing methods and machine learning algorithms are combined.

## Summary
In the project, Support Vector Machines (SVM) and Random Forest (RF) algorithms were specifically compared. For the given dataset and problem, SVM demonstrated higher accuracy and better generalization performance. Although RF is a strong ensemble method, it showed a risk of overfitting during training and achieved lower performance on the test data.

As a result, the winning algorithm in this project is SVM.

## Data Set
- **Number of positive images:** 4012  
- **Number of negative images:** 3010  
- **Total images:** 7022  
- Image size: (150, 150)  
- Class distribution: [3010, 4012]  
- The dataset is available in the Releases section. You can download the positive and negative data and place them in any directory to run the project.

## Preprocessing and Feature Extraction
- **Gaussian Blur:** Noise reduction and obtaining cleaner edge information.
- **HOG (Histogram of Oriented Gradients):** Extraction of edge and shape features.
  - Initial feature size: 1764  
  - After PCA: 500 (variance retained: 94.54%)
- **LBP (Local Binary Patterns):** Extraction of texture features.
  - Feature size: 18  
- **HOG + LBP birleştirme:** Total feature size: 518  
- **SMOTE:** Synthetic samples were added to the minority class to address class imbalance.

## Training / Validation / Test Results

|              Model              | Train Accuracy | Validation Accuracy | Test Accuracy |
|---------------------------------|----------------|---------------------|---------------|
| **SVM (rbf)**                   | 0.987          | 0.946               | **0.952**     |
| **RF (100 tree, max_depth=10)** | 0.991          | 0.918               | 0.909         |

## Result
- **SVM:** Better generalization, higher accuracy, 95.2% performance on the test set. 
- **RF:** Showed an overfitting tendency with 99.1% on training data. Overfitting likelihood increased on the test set.
- **Preprocessing steps (Gaussian Blur, HOG, LBP, PCA, SMOTE)** are critical components that improved model performance.

Therefore, for this project and dataset, **SVM was selected as the preferred algorithm**.
