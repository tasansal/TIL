# Anomaly Detection 101

## Summary
* Isolation Forest:
  * unsupervised, random forest based, 
  ![](https://miro.medium.com/max/1308/1*8KO2Q04TdH-8tW8GI32ZIg.png)
* Local Outlier Factor
  * unsupervised, looks at density 
  ![](https://miro.medium.com/max/700/1*THoxY_4jKpnPXjlR_trxGA.jpeg)
* Robust Covariance
  * For gaussian independent features
  * Gaussian/normal variables, points lying away from 3rd deviation can be considered as anomalies.
  * If all the feature gaussian in nature, then the statistical approach can be generalized by defining an elliptical hypersphere that covers most of the regular data points.
* One-Class SVM
  *  SVM tries to find a hyperplane that best separates the two classes of data points. For one-class SVM where we have one class of data points, and the task is to predict a hypersphere that separates the cluster of data points from the anomalies.
* One-Class SVM (SGD)
  * Stochastic Gradient Descent version of the above

![](https://scikit-learn.org/stable/_images/sphx_glr_plot_anomaly_comparison_001.png)

### Useful Links:
#### 1. Comparing anomaly detection algorithms for outlier detection on toy datasets
[Source](https://scikit-learn.org/stable/auto_examples/miscellaneous/plot_anomaly_comparison.html)
#### 2. Five Anomaly Detection Algorithms every Data Scientist should know
[Source](https://towardsdatascience.com/5-anomaly-detection-algorithms-every-data-scientist-should-know-b36c3605ea16)