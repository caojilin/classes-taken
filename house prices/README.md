### [House Prices: Advanced Regression Techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)  
description: Predict sales prices and practice feature engineering, RFs, and gradient boosting  

1 data preprocessing:
 - imputation: substitue missing value by average. This is a reasonable strategy if features are missing at random.
 - log transform of highly skewed variables including features and label.
   - The reason for ‘normalizing’ the features is that it brings all features to the same order of magnitude. If you can take the log of the data and it becomes normalish, then you can take advantage of many features of a normal distribution, like well-defined mean, standard deviation (and hence z-scores), symmetry, etc.
   - The reason for ‘normalizing’ the label is that we assume the data is [lognormal distribution](https://en.wikipedia.org/wiki/Log-normal_distribution). This will tend to be things like salaries, housing prices, etc, where all values are positive and most are relatively modest, but some are very large.
   - Also OLS requires errors to have a normal distribution with 0 mean and constant variance. Log transform can make sure the variance become constant.

2 feature engineering. It's not easy to do feature engineering and you don't know how helpful your engineered features even are. Why not directly dive into modeling?

3 variable selection. Too many features, it's hard for human to select by instinct or hand. So why not leave it to LASSO or Ridge

3 I choose to use Elastic Net, LASSO, Ridge. The first one is a generalization of the latter two.

4 Furthermore, you can experiment other low variance models for the sake of prediction, such as Random forests, bagging, and boosting.
