# kaggle-challenge-machine-failure
Binary classification project based on the challenge posted on Kaggle website: https://www.kaggle.com/competitions/playground-series-s3e17/data

## Project description

### 1 Data exploration
Data exploration is a crucial step of every data analysis pipeline. Distribution of features and outcome variables is crucial to determine the best pre-processing techniques to be applied and classification models to be tested to ensure satisfying results.

#### 1.1 Unbalanced data
A key finding of data exploration of the Machine Failure dataset is that both features and outcome are unbalanced. This is issue is quite frequent in real world classification tasks. Some of the workarounds to solve the unbalanced problem are the following:
- **Collect more data:** being this a simple solution that may nevertheless be overlooked in real world classification problems, it is always worth asking the question: is it possible to collect more data? Unfortunately, in this context the answer is no as we are dealing with a toy dataset from Kaggle's website.
- **Change the performance metric:** accuracy is not a good metric in this case. As only 1.575% of observations result in a machine failure, a classifier predicting all machines to be correctly functioning would achieve around 98.425% accuracy. Some alternatives to accuracy such as Precision, Recall, Confusion Matrix, F-1 Score, and ROC Curve are valuable options. Cohen's Kappa is also an interesting metric consisting of a version of accuracy normalized for the imbalance of the classes in the dataset.
- **Resample:** this can be done in two ways:
    - Over-sampling: add copies of instances from the under-represented class (also refered to as sampling with replacement);
    - Under-sampling: delete instances from the over-represented class.
- **Generate Synthetic Samples**: randomly sample features from the minority class. There are various statistical methods to do so, such as using Naive Bayes, or the Synthetic Minority Over-sampling Technique (SMOTE).
- **Try Different Algorithms**: this is in general good advice with all classification tasks irrespective of unbalancedness. 
- **Introduce a Penalization Term**: another option is to tweak the loss function of the model to overweight prediction errors on the under-represented class. All classification methods that have a specification in terms of Empirical Risk Minimization allow for such option.
- **Change Perspective**: the core principle behind this method is that there may be a reason for the unbalanced class. In fact, in the specific case of Machine Failures we can consider a malfunctioning as being caused by some unexpected condition in the environment the machine is operating in. Switching from a classification to an anomaly detection problem may be the key to better predictions. 
