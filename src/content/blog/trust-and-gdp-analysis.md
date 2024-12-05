---
author: Daniel Cagney
pubDatetime: 2025-01-01
modDatetime: 2025-01-01
title: Trust and GDP Analysis
slug: trust-and-gdp-analysis
featured: false
draft: false
tags:
  - docs
description:
  Some rules & recommendations for creating or adding new posts using AstroPaper
  theme.
---

# Trust and GDP Analysis: Exploring the Relationship Using Machine Learning and Regression

This blog post delves into a detailed analysis of how **societal trust** influences **GDP per capita**, using both traditional econometric models and machine learning techniques. The methods, datasets, code snippets, and visualizations are provided to offer a complete reference for anyone looking to understand or replicate this analysis.

---

## Introduction

Societal trust is a key driver of economic success, shaping the way individuals interact, institutions function, and economies grow. In high-trust societies, the costs of doing business are reduced, cooperation is fostered, and governance is more effective, all of which contribute to greater economic prosperity. A striking example of this can be seen in the **Nordic countries**—Denmark, Norway, Sweden, and Finland—which consistently rank among the highest in global trust indices.

These nations are also known for their strong economies, high GDP per capita, and robust welfare systems. The high levels of societal trust in these countries allow for efficient transactions, lower corruption, and more inclusive social policies, which together fuel economic growth and stability.

In contrast, **Ireland** presents a different but evolving case. While Ireland has enjoyed significant economic growth in recent decades, transforming from one of the poorer nations in Europe to a prosperous economy, its levels of societal trust have historically been lower than those in the Nordic countries. Ireland’s economic boom—often referred to as the **Celtic Tiger**—was driven by factors like foreign direct investment and a young, educated workforce.

However, societal trust plays a growing role in Ireland’s continued development, particularly as the country seeks to maintain political stability, reduce inequality, and foster sustainable growth. By examining the relationship between trust and economic performance in Ireland, in the context of high-trust nations like the Nordics, we can better understand how improving societal trust may contribute to long-term prosperity.

---

## Analysis Overview

This analysis explores the relationship between **societal trust** and **economic performance** (GDP per capita), using both **linear regression** and **machine learning models** like **Random Forest** and **Gradient Boosting**. The goal is to assess the impact of trust on GDP and understand how other factors like education level, political stability, and institutional quality play a role.

---

## 1. Datasets Used

The following datasets were used in this analysis:

### a. **Trust Level Data**

- **Source:** European Social Survey (ESS), World Values Survey (WVS).

- **Variables:** Trust_Level (scaled 0-1, where 1 indicates high trust).

### b. **GDP Data**

- **Source:** Central Statistics Office (CSO), World Bank.
- **Variables:** GDP_per_Capita (in current USD).

### c. **Control Variables**

- **Education Level:** Percentage of the population with tertiary education (CSO).
- **Political Stability:** Political stability index from the World Bank (scaled 0-1).
- **Institutional Quality:** Corruption perception index from Transparency International.

---

## 2. Data Preparation

The following Python code demonstrates how the dataset is loaded, preprocessed, and scaled for use in regression and machine learning models.

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

# Load the dataset
data = pd.read_csv('trust_gdp_data.csv')

# Drop missing values
data = data.dropna()

# Define dependent and independent variables
X = data[['Trust_Level', 'Education_Level', 'Political_Stability', 'Institutional_Quality']]
y = data['GDP_per_Capita']

# Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Feature scaling
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```
