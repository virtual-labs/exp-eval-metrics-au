#### 1. Overfitting and Underfitting

##### 1.1 Overfitting

**Definition**  
Overfitting occurs when a machine learning model learns both the underlying patterns and the random fluctuations (noise) present in the training data. As a result, the model performs extremely well on the training set but exhibits poor generalization performance on unseen data.

**Key Characteristics**
- Very low training error
- Significantly higher validation/test error (large generalization gap)
- High variance and low bias

**Common Causes**
- Model complexity excessively high relative to the amount of training data (e.g., very deep neural networks, high-degree polynomials)
- Limited or non-representative training data
- Lack of regularization
- Training has continued far beyond the point of optimal validation performance

**Prevention and Mitigation Techniques**
- L1 (Lasso), L2 (Ridge), or Elastic Net regularization
- Dropout, DropConnect, and stochastic depth (in neural networks)
- Early stopping using a validation set
- Data augmentation and acquiring additional training examples
- Cross-validation for more reliable performance estimation
- Model pruning, architecture simplification, or reducing capacity
- Ensemble methods (bagging, random forests) to reduce variance



##### 1.2 Underfitting

**Definition**  
Underfitting occurs when a model is too simple (has insufficient capacity) to capture the true underlying structure or relationships in the data.

**Key Characteristics**
- High error on both training and validation/test sets
- High bias and low variance

**Common Causes**
- Model capacity too low for the complexity of the problem (e.g., fitting a linear model to nonlinear data)
- Overly strong regularization
- Insufficient training duration (especially for iterative algorithms)
- Inadequate or poorly engineered features

**Remediation Techniques**
- Increase model capacity (add layers, neurons, higher-degree terms, etc.)
- Perform feature engineering or use more expressive feature representations
- Decrease regularization strength
- Allow the model to train for more epochs or use better optimization algorithms



##### 1.3 Bias–Variance Trade-off

The generalization error of a model can be decomposed as:  
**Generalization Error = Bias² + Variance + Irreducible Error**

- **Bias**: Error arising from overly simplistic assumptions in the learning algorithm (dominant in underfitting)
- **Variance**: Error arising from sensitivity to small fluctuations in the training set (dominant in overfitting)
- **Irreducible Error**: Inherent noise in the data that cannot be eliminated

The goal is to find the optimal model complexity that minimizes the sum of bias² and variance.

#### 2. Dataset Splitting Strategies

| Split          | Purpose                                                  | Typical Proportion                  | Notes                                           |
|----------------|----------------------------------------------------------|-------------------------------------|-------------------------------------------------|
| Training set   | Parameter learning (weights, coefficients)               | 60–98%                              | Primary data used for gradient-based optimization |
| Validation set | Hyperparameter tuning and early stopping decisions       | 10–20% (or 1–2% on very large datasets) | Never used for gradient updates                 |
| Test set       | Final unbiased evaluation of model performance           | 10–20%                              | Seen only once, after all tuning is complete    |

**Best Practices**
- Keep test set completely isolated until final evaluation
- Use stratified splitting for classification to preserve class distribution
- For small datasets: k-fold cross-validation (commonly k=5 or 10)
- For very large datasets: single train/validation split is often sufficient

#### 3. Evaluation Metrics

##### 3.1 Classification Metrics

| Metric          | Formula                                              | Interpretation                                      | Best Used When                              |
|-----------------|------------------------------------------------------|-----------------------------------------------------|---------------------------------------------|
| Accuracy        | (TP + TN) / (TP + TN + FP + FN)                      | Overall correctness                                 | Classes are balanced                        |
| Precision       | TP / (TP + FP)                                       | Proportion of positive predictions that are correct | Minimizing false positives is critical      |
| Recall (Sensitivity) | TP / (TP + FN)                                  | Proportion of actual positives correctly identified | Minimizing false negatives is critical      |
| F1-Score        | 2 × (Precision × Recall) / (Precision + Recall)      | Harmonic mean of precision and recall               | Imbalanced classes, need single metric      |
| ROC-AUC         | Area under the ROC curve                             | Ability to discriminate classes across thresholds   | Threshold-independent model comparison      |
| PR-AUC          | Area under Precision-Recall curve                    | Performance on highly imbalanced datasets           | Highly skewed positive/negative ratio       |

##### 3.2 Regression Metrics

| Metric                  | Formula                                                               | Properties                                      | Typical Use Case                              |
|-------------------------|-----------------------------------------------------------------------|-------------------------------------------------|-----------------------------------------------|
| Mean Absolute Error (MAE) | (1/n) Σ |yᵢ − ŷᵢ|                                      | Robust to outliers, interpretable in original units | Errors are equally costly                     |
| Mean Squared Error (MSE) | (1/n) Σ (yᵢ − ŷᵢ)²                                                   | Differentiable, penalizes large errors heavily  | Most optimization algorithms minimize MSE     |


#### 4. Summary of Key Relationships

| Situation                     | Training Error | Validation/Test Error | Diagnosis       | Action                              |
|-------------------------------|----------------|-----------------------|-----------------|-------------------------------------|
| Overfitting                   | Very low       | High                  | High variance   | Regularize, simplify, more data     |
| Underfitting                  | High           | High                  | High bias       | Increase capacity, better features  |
| Good generalization          | Low            | Low (close to training) | Balanced bias-variance | Monitor and deploy                |

