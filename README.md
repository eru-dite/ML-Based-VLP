# Machine Learning-Based Visible Light Positioning

[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python\&logoColor=white)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter\&logoColor=white)](https://jupyter.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas\&logoColor=white)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-013243?logo=numpy\&logoColor=white)](https://numpy.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557c)](https://matplotlib.org/)
[![Scikit--learn](https://img.shields.io/badge/Scikit--learn-Machine%20Learning-F7931E?logo=scikit-learn\&logoColor=white)](https://scikit-learn.org/)

A machine learning approach to indoor positioning using optical signal measurements from multiple visible light luminaires.

## Overview

Visible Light Positioning (VLP) uses light-emitting luminaires as reference sources to estimate the position of a receiver.

This project investigates whether machine learning models can learn the relationship between optical signal measurements received from multiple luminaires and the corresponding two-dimensional position of a receiver.

The system follows the relationship:

**Optical signal measurements → Machine learning model → Receiver position (x, y)**

Three regression models were evaluated:

* Random Forest
* K-Nearest Neighbours (KNN)
* Multi-Layer Perceptron (MLP)

## Dataset

The dataset contains:

* **7,344 samples**
* **11 optical signal features** (`L1`–`L11`)
* **2 target coordinates** (`x`, `y`)

The `L1`–`L11` features represent optical signal measurements associated with different luminaires, while `x` and `y` represent the actual receiver position.

The luminaire coordinates used in the project are provided in `luminaire_locations.csv`.

> **Note:** The original `Public_VLP_Dataset.csv` is not included in this repository. It is excluded through `.gitignore` because it is an external dataset.

## Methodology

### Data Preparation

The 11 optical signal measurements were used as input features:

```text
L1, L2, L3, ..., L11
```

The target variables were:

```text
x, y
```

The dataset was divided into:

* **80% training data**
* **20% testing data**

### Machine Learning Models

Three regression approaches were trained and evaluated:

**Random Forest Regressor**

An ensemble tree-based model used to learn nonlinear relationships between optical signal measurements and receiver position.

**K-Nearest Neighbours (KNN)**

A distance-based regression method that predicts position using neighbouring samples in the feature space.

**Multi-Layer Perceptron (MLP)**

A feedforward neural network used to model the nonlinear relationship between optical measurements and receiver coordinates.

## Results

The models were evaluated using the **mean Euclidean positioning error**, which represents the average physical distance between the predicted and actual receiver positions.

| Model             | Mean Positioning Error |
| ----------------- | ---------------------: |
| **Random Forest** |            **9.83 cm** |
| MLP               |               11.68 cm |
| KNN               |               11.69 cm |

The **Random Forest model achieved the best performance**, with a mean positioning error of approximately **9.83 cm** on the test set.

### Random Forest Error Analysis

| Metric          | Positioning Error |
| --------------- | ----------------: |
| Minimum         |           0.41 cm |
| Median          |           8.58 cm |
| Mean            |           9.83 cm |
| 95th percentile |          19.72 cm |
| Maximum         |            3.05 m |

The majority of predictions were relatively close to the actual receiver positions, although a small number of samples produced substantially larger errors.

## Visual Results

### Actual vs Predicted Positions

![Actual vs Predicted Positions](Figures/actual_vs_predicted.png)

The predicted positions generally follow the distribution of the actual receiver positions.

### Positioning Error Distribution

![Positioning Error Distribution](Figures/error_distribution.png)

The error distribution shows that most predictions have relatively small positioning errors, with a smaller number of larger errors.

### Model Comparison

![Model Comparison](Figures/model_comparison.png)

Random Forest produced the lowest mean positioning error among the three evaluated models.

### Feature Importance

![Feature Importance](Figures/feature_importance.png)

The Random Forest feature importance analysis identified **L4, L1, and L9** as the three most influential input features.

Together, these features accounted for approximately **66% of the total feature importance**.

## Limitations

The current evaluation uses a random train-test split.

Because measurements from spatially neighbouring positions can be similar, randomly distributing samples between the training and testing sets may produce an optimistic estimate of spatial generalization.

A more rigorous evaluation would use a **spatial holdout strategy**, where specific locations or regions are excluded from training and used exclusively for testing.

Therefore, the current results demonstrate the feasibility of machine learning-based VLP on the selected dataset but do not yet establish performance on completely unseen spatial regions.

## Future Work

Future development could investigate:

* Spatially separated training and testing regions
* Hyperparameter optimization
* Additional regression and deep learning models
* Feature selection and dimensionality reduction
* Robustness to measurement noise
* Real-time positioning
* Embedded deployment
* Edge AI implementation
* Integration with visible light communication systems

## Repository Structure

```text
ML-Based-VLP/
│
├── Figures/
│   ├── actual_vs_predicted.png
│   ├── error_distribution.png
│   ├── feature_importance.png
│   └── model_comparison.png
│
├── ML_Based_Visible_Light_Positioning.ipynb
├── README.md
├── Requirements.txt
├── luminaire_locations.csv
└── .gitignore
```

## Reproducibility

The analysis was implemented in Python using Jupyter Notebook.

Required Python packages are listed in `Requirements.txt`.

The notebook contains the complete workflow:

**Data loading → Data preparation → Model training → Prediction → Error analysis → Model comparison → Feature importance**

## Author

**Goodnews Osama Imakpokpomwan**

Electrical/Electronics Engineering
University of Benin

Research interests include intelligent sensing, embedded systems, optical wireless systems, machine learning, and AI-enabled sensing.


