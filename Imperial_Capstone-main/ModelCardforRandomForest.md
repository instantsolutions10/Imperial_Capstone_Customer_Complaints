### **Model Card for Random Forest Classifier**

---

### **Model Description**
**Objective**: The Random Forest Classifier is designed to predict customer complaint categories based on textual and categorical input data. The model is used to automate the categorization process, helping businesses respond to customer concerns more efficiently.

- **Input**:
  - Textual data: `Consumer complaint narrative`, preprocessed and vectorized using `TfidfVectorizer`.
  - Categorical features: Features like `State` and `Submitted via`, label-encoded for numerical representation.
  
- **Output**:
  - A predicted category (`Product`) from 21 classes, including "Credit reporting," "Debt collection," and others.

- **Use Case**:
  - Automating customer complaint categorization to reduce manual effort and improve operational efficiency.

---

### **Model Architecture**
- **Algorithm**: Random Forest Classifier
- **Key Parameters**:
  - `n_estimators`: 50 (number of trees in the forest)
  - `max_depth`: 10 (maximum depth of each tree)
  - `max_features`: 'sqrt' (square root of total features considered for each split)
  - `class_weight`: Default (unbalanced)
- **Feature Engineering**:
  - Text features: Preprocessed and vectorized with a maximum of 1,000 features using TF-IDF.
  - Categorical features: Encoded using label encoding.

---

### **Performance**
**Evaluation Metrics**:
- **Accuracy**: 46% (overall correct predictions).
- **Precision, Recall, and F1-Score**:
  - **Macro average**: Precision = 30%, Recall = 10%, F1-score = 11%.
  - **Weighted average**: Precision = 50%, Recall = 46%, F1-score = 40%.

**Observations**:
- Class **6** (likely the dominant class) performed the best with an F1-score of 58%, while many other classes have poor performance (precision and recall near 0).
- Imbalanced data negatively impacted the model’s ability to predict minority classes.

**Visualization**:
- Confusion matrix analysis highlights poor predictions for minority classes and better performance for dominant classes.

---

### **Limitations**
1. **Imbalanced Data**:
   - The dataset contains a high degree of imbalance, with certain classes dominating. This leads to poor performance for underrepresented classes.
2. **Overfitting to Dominant Classes**:
   - The model heavily favors the majority class (class 6), reducing generalizability across all categories.
3. **Limited Depth**:
   - Restricting the depth of trees (to 10) limits the model's ability to capture complex relationships.

---

### **Trade-offs**
1. **Accuracy vs. Generalization**:
   - The model achieves moderate accuracy but fails to generalize to underrepresented classes.
2. **Scalability**:
   - Reducing tree depth and feature size helps scalability but limits performance.
3. **Interpretability**:
   - While Random Forests are more interpretable than neural networks, feature importance for imbalanced data may skew insights.

---

### **Recommendations for Improvement**
- Address class imbalance using oversampling (e.g., SMOTE) or undersampling.
- Experiment with hyperparameter tuning (e.g., `class_weight='balanced'`) to improve performance across all classes.
- Consider switching to gradient-boosting algorithms like XGBoost or LightGBM, which often handle imbalanced datasets better.

---

This Random Forest model provides a moderate baseline but requires further improvements to handle class imbalance and enhance predictions for underrepresented classes.
