\# Machine Learning-Based Visible Light Positioning



A machine learning approach for estimating receiver position from optical signal measurements in a Visible Light Positioning (VLP) environment.



\## Overview



Visible Light Positioning uses visible light signals from luminaires to estimate the position of a receiver.



This project investigates whether machine learning can learn the relationship between optical signal measurements and the two-dimensional position of a receiver.



The problem is formulated as:



\*\*Optical signal measurements (L1–L11) → Receiver position (x, y)\*\*



Three regression models were evaluated:



\* Random Forest

\* K-Nearest Neighbors (KNN)

\* Multi-Layer Perceptron (MLP) Neural Network



\## Dataset



The project uses the Public VLP Dataset, containing:



\* 7,344 samples

\* 11 optical signal features

\* 2 position coordinates



The input features are:



`L1, L2, ..., L11`



The target variables are:



`x, y`



The dataset identifiers were excluded from the machine learning features.



\## Methodology



The workflow consists of:



1\. Loading and inspecting the VLP dataset

2\. Selecting the optical signal measurements as input features

3\. Splitting the dataset into training and testing sets

4\. Training three regression models

5\. Predicting receiver positions

6\. Calculating Euclidean positioning error

7\. Comparing model performance

8\. Analysing prediction errors

9\. Examining Random Forest feature importance



\## Results



The models achieved the following mean Euclidean positioning errors on the test set:



| Model              | Mean Positioning Error |

| ------------------ | ---------------------: |

| \*\*Random Forest\*\*  |            \*\*9.83 cm\*\* |

| MLP Neural Network |               11.68 cm |

| KNN                |               11.69 cm |



Random Forest achieved the lowest mean positioning error among the three evaluated models.



\### Error Statistics



For the Random Forest model:



| Metric          |    Error |

| --------------- | -------: |

| Minimum         |  0.41 cm |

| Median          |  8.58 cm |

| Mean            |  9.83 cm |

| 95th percentile | 19.72 cm |

| Maximum         |   3.05 m |



\## Visual Results



\### Actual vs Predicted Positions



!\[Actual vs Predicted Positions](figures/actual\_vs\_predicted.png)



\### Positioning Error Distribution



!\[Positioning Error Distribution](figures/error\_distribution.png)



\### Feature Importance



!\[Random Forest Feature Importance](figures/feature\_importance.png)



\### Model Comparison



!\[Model Comparison](figures/model\_comparison.png)



\## Feature Importance



The Random Forest model identified the following features as the most influential:



| Feature | Importance |

| ------- | ---------: |

| L4      |     30.92% |

| L1      |     22.61% |

| L9      |     13.40% |

| L6      |      6.91% |

| L3      |      6.90% |



L4, L1 and L9 together accounted for approximately 66% of the model's total feature importance.



\## Limitations



The evaluation used a random train-test split. Because the dataset contains spatially clustered measurements, nearby positions may occur in both the training and testing sets. Consequently, the reported performance may be optimistic with respect to spatial generalization.



\## Future Work



Potential extensions include:



\* Spatially separated train-test evaluation

\* Robustness testing under measurement noise

\* Additional machine learning models

\* Hyperparameter optimization

\* Real-time VLP positioning

\* Deployment on embedded hardware

\* Integration with a physical VLC sensing system



\## Technologies



\* Python

\* Pandas

\* NumPy

\* Matplotlib

\* Scikit-learn

\* Google Colab



\## Repository Structure



```text

ML-Based-VLP/

│

├── figures/

│   ├── actual\_vs\_predicted.png

│   ├── error\_distribution.png

│   ├── feature\_importance.png

│   └── model\_comparison.png

│

├── ML\_Based\_VLP.ipynb

├── README.md

└── requirements.txt

```



\## Author



\*\*Goodnews Osama Imakpokpomwan\*\*



Electrical/Electronics Engineering | Intelligent Sensing | Embedded Systems | Photonics \& AI Hardware



