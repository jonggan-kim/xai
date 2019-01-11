![GitHub](https://img.shields.io/badge/Version-0.1-lightgrey.svg)
![GitHub](https://img.shields.io/badge/Python-3.5_|_3.6-blue.svg)
![GitHub](https://img.shields.io/badge/License-MIT-lightgrey.svg)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)

# XAI - An explainability-first AI library

XAI is a Machine Learning library that is designed with AI explainability in its core. XAI contains various tools that enable for analysis and evaluation of data and models. The XAI library is maintained by [The Institute for Ethical AI & ML](http://ethical.institute/), and it was developed based on the [8 principles for Responsible Machine Learning](http://ethical.institute/principles.html).

## What do we mean by eXplainable AI?

The XAI library is designed to empower machine learning engineers and relevant domain experts to analyse the end-to-end solution and identify discrepancies that may result in sub-optimal performance relative to the objectives required. More concretely, the XAI library is designed using the 3-steps of explainable machine learning, which involve 1) data analysis, 2) model evaluation, and 3) production monitoring. 

The provide a visual overview of these three steps, we can have a look at this in the diagram below:

<img width="100%" src="images/bias.png">

# XAI Quickstart

## Installation

The XAI package is on PyPI. To install you can run:

```
pip install xai
```

Alternatively you can install from source by cloning the repo and running:

```
python setup.py install 
```

## Usage

You can find example usage in the examples folder.

### 1) Data Analysis

``` python
# Initialise XData object with dataframe and target col
xd = XData("loan", df)

# Set protected columns (default is all)
xd.set_protected(["gender", "ethnicity", "native-country", "age"])

# Access dataframe directly
xd.df.head()

# View class imbalances
xd.show_imbalances(cross=[])

# View imbalance for specific column
xd.show_imbalance("gender", cross=[])

# Adapt threshold for imbalance evaluation
xd.set_threshold(0.8)

# Balance class that is under threshold
xd.balance("gender")
xd.show_imbalance("gender", cross=[])

# Visualise cross-class imbalance
xd.show_imbalance("gender")

xd.reset()
xd.balance("gender", downsample=0.8, upsample=0.8)
xd.show_imbalance("gender")

# View correlations
xd.correlations()

xd.normalize_numeric()
xd.convert_categories()
xd.test_split()

model.fit(xd.df)
preds = model.predict(xd_test.df)

xd_test.roc_curve(preds, cross=["gender"])

```

### 2) Model Evaluation

``` python
# Normalize numerical columns
xd.normalize_numeric()
xd.convert_categories()

# You can access test and train datasets as well
xd.x_train.head()
# xd.x_valid.head()
# xd.x_test.head()
```


### 3) Production Monitoring





