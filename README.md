# Machine Learning-Based Classification of Variable Stars

### Research Question
Can we construct machine learning models that can effectively and accurately classify variable star types?
- More specifically, we want to compare the classification results of a Random Forest and XGBoost model.

### Motivation
With the increasing pace and volume of astronomical data collection, it becomes important to address astronomical problems using technologies that can handle all this data with reasonably efficiency and accuracy.

While our research topic is not new, we intend to compare our methods and findings to prior relevant research, and to potentially address pitfalls that they may have encountered. 

### Variable Stars
Variable stars are stars whose brightness fluctuates over time. They can be split into several subtypes, and this investigation aims to classify sevem types of variable stars, namely: 
1. Eclipsing Binaries
2. RR Lyrae
3. Delta Scuti Variables
4. Classical Cepheids
5. Type II Cepheids
6. Heartbeat Stars
7. Anamolous Cepheids

### Data
All our data was collected from all target fields of the fourth phase of the Optical Gravitational Lensing Project (OGLE-IV). 

Our original data consisted of close to 736,000 variable stars.
- All features with 20% or more of its data missing were dropped from the dataset → 670,000 rows remaining
- 7 different types of variable stars are to be classified

### Addressing Class Imbalance
Our original data was extremely imbalanced, with eclipsing binaries representing a majority of the dataset, and with some of the other star types representing less than 1% of the dataset. 

![image](https://github.com/jasminex21/variable_star_classification/assets/109494334/31cdf741-abdc-45e5-8adc-242128cfdf43)

![image](https://github.com/jasminex21/variable_star_classification/assets/109494334/dcef5399-681e-423e-ba2e-dc57d778a029)

Class imbalance can impact model performance, because models will tend to be biased towards the majority class(es). 

We chose to address this using Synthetic Minority Oversampling Technique (SMOTE), which generates synthetic samples of minority classes such that all classes end up with the same number of data points. 

### Machine Learning Models
#### Random Forest
An ensemble learning technique based on bagging (bootstrap aggregating), where multiple decision trees are created independently, and their predictions are merged.
#### XGBoost 
An ensemble learning technique based on gradient boosting; decision trees are created sequentially, and the later trees correct errors made by previous trees. 
#### Methodology 
We first ran a Random Search for both models to determine optimal hyperparameters. 

The optimal value of n_estimators (the number of trees) was determined to be 400 for the random forest and 300 for the XGBoost model.

Variable star types (the target variable) were encoded using scikit-learn’s LabelEncoder, which assigns each star type a unique numerical value. However, a limitation of this method is that it assumes ordinality among the values in the target variable. The alternative method to LabelEncoder would be One-Hot Encoding, but I chose not to use this because it would vastly complicate the investigation by making the data high-dimensional, and it may also require a separate model to be build for each variable star type. 

### Results
The Random Forest model achieved an accuracy of 97.71%, and the XGBoost model achieved an accuracy of 93.65%. 

![image](https://github.com/jasminex21/variable_star_classification/assets/109494334/b5563186-e73d-4627-83e2-703f1282269b)

![image](https://github.com/jasminex21/variable_star_classification/assets/109494334/7db244db-7f13-4e95-8327-ffa23d460371)

### Future Directions
- Construction of a recurrent neural network that takes in photometric data
  - Compare this to current models
- Applying our current models to other labelled datasets of variable stars to confirm their applicability 
- Applying our current models to unlabelled datasets






