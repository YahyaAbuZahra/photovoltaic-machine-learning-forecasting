
# Predicting Photovoltaic Power Output: Ma'an Solar Plant Case Study

## Table of Contents

1. [Project Overview](https://www.google.com/search?q=%23project-overview)
2. [System Architecture](https://www.google.com/search?q=%23system-architecture)
3. [Data Acquisition](https://www.google.com/search?q=%23data-acquisition)
4. [Methodology](https://www.google.com/search?q=%23methodology)
5. [Performance Benchmarks](https://www.google.com/search?q=%23performance-benchmarks)
6. [Visualizations](https://www.google.com/search?q=%23visualizations)
7. [Installation and Usage](https://www.google.com/search?q=%23installation-and-usage)
8. [Author](https://www.google.com/search?q=%23author)

---

## Project Overview

This project focuses on the development and comparative analysis of machine learning models to forecast the total AC power output of the **Shams Ma'an Solar Power Plant** (52.5 MW capacity). By leveraging historical operational data and meteorological parameters, the system aims to provide accurate short-term power generation predictions to assist in grid stability and energy management.

The study evaluates the efficacy of various regression algorithms, ranging from classical methods (KNN, SVR) to advanced ensemble gradient boosting techniques (CatBoost, LightGBM, XGBoost), identifying the optimal architecture for deployment.

---

## System Architecture

The project follows a rigorous End-to-End Machine Learning pipeline:

```mermaid
graph LR
    A[Raw Data Ingestion] --> B[Preprocessing & Cleaning];
    B --> C[Feature Engineering];
    C --> D[Model Training];
    D --> E[Hyperparameter Tuning];
    E --> F[Evaluation & Selection];
    F --> G[Deployment Strategy];

```

---

## Data Acquisition

**Source:** Operational data from [Shams Ma'an Solar Power Plant](https://www.shamsmaan.com/), Jordan.

| Attribute | Details |
| --- | --- |
| **Time Period** | September 2025 – December 2025 |
| **Granularity** | 15-minute intervals |
| **Volume** | 5,860 clean records (post-processing) |
| **Target Variable** | Total AC Power Output (Sum of 9 Inverters) |

<details>
<summary><strong>Click to expand Feature Set Details</strong></summary>

The dataset comprises the following features utilized for training:

* **Meteorological Features:**
* Global Horizontal Irradiance (W/m²)
* Ambient Temperature (°C)
* PV Module Temperature (°C)
* Wind Speed (m/s) & Direction
* Relative Humidity (%)


* **Temporal Features:**
* Hour of Day
* Cyclical Time Encodings (Sine/Cosine transformations for Hour/Month)



</details>

---

## Methodology

The research methodology prioritizes a hierarchical evaluation of model complexity.

### 1. Preprocessing Pipeline

* **Imputation:** Handling missing values via interpolation.
* **Normalization:** Applied `StandardScaler` for distance-based algorithms (KNN, SVR).
* **Cyclical Encoding:** Mathematical transformation of time features to preserve temporal continuity.

### 2. Model Selection

We evaluated models across four distinct categories.

<details>
<summary><strong>Click to view Model Architectures</strong></summary>

* **Baseline:**
* *Persistence Model:* Assumes . Used to establish a performance floor.


* **Classical Machine Learning:**
* *K-Nearest Neighbors (KNN):* Distance-based regression.
* *Support Vector Regression (SVR):* Kernel-based regression (RBF kernel).


* **Bagging Ensembles:**
* *Random Forest:* Optimized utilizing RandomizedSearchCV.


* **Boosting Ensembles:**
* *Gradient Boosting Regressor (GBR)*
* *XGBoost:* Extreme Gradient Boosting.
* *LightGBM:* Light Gradient Boosting Machine.
* *CatBoost:* Categorical Boosting (Best Performer).



</details>

---

## Performance Benchmarks

Models were evaluated using **R-squared ()**, **Root Mean Squared Error (RMSE)**, and **Mean Absolute Error (MAE)**.

*Ordered by Accuracy ()*

| Model Architecture |  Score | RMSE | MAE | Operational Verdict |
| --- | --- | --- | --- | --- |
| **Persistence (Baseline)** | 0.9838 | 390,830 | 169,002 | Reference only; non-predictive. |
| **CatBoost** | **0.9620** | **599,102** | **269,402** | **Primary Choice for Deployment.** |
| **Random Forest** | 0.9595 | 618,519 | 297,636 | High stability, strong alternative. |
| **LightGBM** | 0.9566 | 639,967 | 292,204 | Fast inference, competitive accuracy. |
| **Gradient Boosting** | 0.9523 | 671,386 | 305,011 | Sensitive to hyperparameter tuning. |
| **KNN (Optimized)** | 0.9489 | 694,853 | 355,082 | Computational bottleneck in high dimensions. |
| **XGBoost** | 0.9383 | 763,551 | 314,495 | Underperformed relative to CatBoost. |
| **SVR** | -0.5101 | 3.77M | 2.42M | Failed to capture non-linear dynamics. |

---



</details>



## Installation and Usage

To replicate this analysis or deploy the model, follow the instructions below.

### Prerequisites

* Python 3.8+
* pip package manager

### Setup

1. **Clone the Repository**
```bash
git clone https://github.com/YahyaAbuZahra/Predicting-PV-Power-Maan.git
cd Predicting-PV-Power-Maan

```


2. **Install Dependencies**
```bash
pip install -r requirements.txt

```


3. **Run the Analysis**
```bash
python main.py

```



---

## Author

**Yahya Abu Zahra**

* Computer Engineering Undergraduate (AI Track)


*Disclaimer: The data utilized in this project is strictly for educational and research purposes.*
