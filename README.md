---
title: "Project: Austin House Price Prediction"
author: "Your Name"
date: "2024-10-27"
output: html_document
---

# Project Overview
This project involves predicting house prices in Austin, Texas, using machine learning algorithms. The dataset includes various housing characteristics, ranging from structural details to amenities.

## Key Steps

### 1. Feature Engineering
We created additional custom features to enhance the predictive power of the models:
- House Age: Calculated from the difference between the year built and the current year.
- Total Features: Combined important features such as square footage and number of rooms.
- Bedroom-Bathroom Count: Created a combined feature for bedrooms and bathrooms to capture the living space layout.

### 2. Data Splitting & Cross-Validation
We split the dataset into an 80/20 ratio for training and testing. To ensure robust model performance, we used 10-fold cross-validation (k = 10).

```{r}
# Example code for data splitting and cross-validation
set.seed(123)
trainIndex <- createDataPartition(dataset$Price, p = .8, 
                                  list = FALSE, 
                                  times = 1)
trainData <- dataset[trainIndex,]
testData  <- dataset[-trainIndex,]

# K-fold cross-validation
control <- trainControl(method = "cv", number = 10)
