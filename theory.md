### Theory 
##### **Overfitting and Underfitting**  
These are common issues in machine learning that affect a model's ability to generalize to new data.  

##### **Overfitting**  
- Overfitting happens when a model learns the training data too well, including noise and outliers, instead of capturing the general patterns.  
- This results in high accuracy on the training data but poor generalization to unseen data, leading to poor test performance.  
- Overfitting often occurs when the model is too complex (e.g., too many parameters, deep neural networks with excessive layers).  
- **Solutions to Overfitting:**
  - **Regularization (L1/L2 penalties)** – Reduces the model complexity by penalizing large coefficients.  
  - **Pruning (for Decision Trees)** – Reduces the depth of the tree to prevent it from memorizing noise.  
  - **Dropout (for Neural Networks)** – Randomly removes neurons during training to prevent reliance on specific features.  
  - **Early Stopping** – Stops training when validation loss stops improving.  
  - **More Training Data** – Helps the model generalize better.  

##### **Underfitting**  
- Underfitting occurs when a model is too simple to capture the underlying patterns in data.  
- It results in both high training error and test error.  
- Common causes include insufficient model complexity, too few training iterations, or inadequate feature representation.  
- **Solutions to Underfitting:**
  - **Increase Model Complexity** – Use a more sophisticated model (e.g., moving from linear regression to polynomial regression).  
  - **Feature Engineering** – Add relevant features or transformations to better represent the data.  
  - **Reduce Regularization** – Loosening L1/L2 penalties can help the model learn more complex patterns.  



##### **Train/Test Split**  
- The train/test split is a crucial technique to evaluate machine learning models.  
- **Training Set** – The dataset used to train the model. The model learns patterns and adjusts parameters based on this data.  
- **Testing Set** – The dataset used to evaluate the model's generalization to new, unseen data.  
- A common split ratio is **70% training / 30% testing**, but it can be adjusted (e.g., 80/20, 60/40) based on dataset size and use case.  
- In some cases, a **validation set** (another split of data) is used to fine-tune hyperparameters before testing.  



##### **Evaluation Metrics**  
Evaluation metrics measure how well a model performs on different tasks.  

##### **Classification Metrics:**  
1. **Accuracy** = (Correct Predictions) / (Total Predictions)  
   - Measures how often the model predicts correctly.  
   - Works well when classes are balanced but can be misleading for imbalanced datasets.  

2. **Precision (Positive Predictive Value)** = TP / (TP + FP)  
   - The proportion of correctly predicted positive instances among all predicted positives.  
   - High precision means fewer false positives.  

3. **Recall (Sensitivity / True Positive Rate)** = TP / (TP + FN)  
   - Measures how well the model identifies all actual positives.  
   - High recall means fewer false negatives.  

4. **F1-Score** = 2 × (Precision × Recall) / (Precision + Recall)  
   - The harmonic mean of precision and recall.  
   - Useful when we need a balance between precision and recall.  

5. **ROC-AUC (Receiver Operating Characteristic – Area Under Curve)**  
   - A graphical measure of classification performance at different thresholds.  
   - AUC close to 1 means good performance, while AUC near 0.5 indicates random guessing.  

##### **Regression Metrics:**  
1. **Mean Absolute Error (MAE)** = \( \frac{1}{n} \sum | y_{\text{true}} - y_{\text{pred}} | \)  
   - Measures the average absolute difference between actual and predicted values.  

2. **Mean Squared Error (MSE)** = \( \frac{1}{n} \sum (y_{\text{true}} - y_{\text{pred}})^2 \)  
   - Squares the errors, giving more weight to larger errors.  

