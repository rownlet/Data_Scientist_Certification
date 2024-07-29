# Predicting Recipe Site Traffic

## Overview

This project aims to predict popular recipes to increase site traffic and subscriptions for a recipe website. The business goal is to achieve an 80% prediction accuracy for high traffic recipes.

## Table of Contents

1. [Project Description](#project-description)
2. [Data](#data)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Model Development](#model-development)
6. [Model Evaluation](#model-evaluation)
7. [Business Metrics](#business-metrics)
8. [Conclusions](#conclusions)
9. [Recommendations](#recommendations)

## Project Description

The project involves the following steps:

1. **Data Validation and Cleaning**
2. **Exploratory Data Analysis (EDA)**
3. **Model Development and Evaluation**
4. **Business Metric Definition**
5. **Recommendations**

## Data

The dataset used for this project includes the following columns:

- `recipe`: Recipe identifier (int)
- `calories`: Caloric content (float)
- `carbohydrate`: Carbohydrate content (float)
- `sugar`: Sugar content (float)
- `protein`: Protein content (float)
- `category`: Recipe category (object, later converted to category)
- `servings`: Number of servings (object, later converted to int)
- `high_traffic`: High traffic indicator (object, later converted to bool)

## Installation

To run this project, you need to install the following dependencies:

```bash
pip install pandas scikit-learn matplotlib seaborn
```

## Usage

1. **Data Preparation**: Validate and clean the data, addressing missing values, duplicates, and data types.
2. **Exploratory Data Analysis (EDA)**: Perform EDA to uncover insights and patterns in the data.
3. **Model Development**: Develop and train predictive models using logistic regression, decision trees, random forest, and support vector machine (SVM).
4. **Model Evaluation**: Evaluate the models using accuracy, precision, recall, F1-score, and confusion matrix.
5. **Business Metric Definition**: Define and calculate the high traffic conversion rate as the key performance indicator (KPI).

## Model Development

### Data Pretreatment

- **Outliers Management**: Use Interquartile Range (IQR) to determine boundaries.
- **Transformations**: Apply Yeo-Johnson transformation for normalization.
- **Encoding**: Perform one-hot encoding on the `category` column.
- **Data Split**: Split data into features (X) and target variable (y).

### Models Used

- **Logistic Regression**: Baseline model
- **Decision Tree**: Comparison model
- **Random Forest**: Comparison model
- **Support Vector Machine (SVM)**: Comparison model

## Model Evaluation

| Model               | Data Set | Accuracy | Precision | Recall | F1-Score | Confusion Matrix       |
|---------------------|----------|----------|-----------|--------|----------|------------------------|
| Logistic Regression | Train    | 0.765    | 0.801     | 0.801  | 0.801    | [[210, 84], [84, 338]] |
|                     | Test     | 0.765    | 0.809     | 0.823  | 0.816    | [[44, 22], [20, 93]]   |
| Decision Tree       | Train    | 1.000    | 1.000     | 1.000  | 1.000    | [[294, 0], [0, 422]]   |
|                     | Test     | 0.670    | 0.750     | 0.717  | 0.733    | [[39, 27], [32, 81]]   |
| Random Forest       | Train    | 1.000    | 1.000     | 1.000  | 1.000    | [[294, 0], [0, 422]]   |
|                     | Test     | 0.765    | 0.803     | 0.832  | 0.817    | [[43, 23], [19, 94]]   |
| SVM                 | Train    | 0.589    | 0.589     | 1.000  | 0.742    | [[0, 294], [0, 422]]   |
|                     | Test     | 0.631    | 0.631     | 1.000  | 0.774    | [[0, 66], [0, 113]]    |

## Business Metrics

- **High Traffic Conversion Rate**: Defined as True Positives / False Positives, with an initial target value based on logistic regression train results KPI = 4.

## Conclusions

- Recipes with 4 servings are the most popular.
- Categories such as Potato, Vegetable, and Chicken generate high traffic.
- Logistic Regression is the best model, with no overfitting and a good balance of precision and recall.

## Recommendations

1. **Implement Logistic Regression**: Due to its balanced performance and lack of overfitting.
2. **Refine Random Forest**: Perform hyperparameters tuning for better results.
3. **Incorporate Additional Features**: Enhance model accuracy by adding more features.
4. **Monitor Model Performance**: Regularly evaluate the model using the defined business metric.

