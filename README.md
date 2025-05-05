# Stroke Prediction Analysis
## Project Overview
This project aims to develop a machine learning model to predict the likelihood of stroke in patients based on healthcare data. Early detection of stroke risk is crucial, since stroke is a major cause of death and long-term disability
cdc.gov
pmc.ncbi.nlm.nih.gov
. In fact, stroke risk increases with age and prompt action can greatly improve patient outcomes
cdc.gov
. By profiling patient attributes (age, gender, work type, health metrics, etc.), the model can flag high-risk individuals for preventive intervention.
## Methodology
Data Ingestion: The dataset of patient health records was loaded and validated. We confirmed that all expected fields (demographics, medical history, lab values, etc.) were present and correctly formatted, and performed basic checks for missing or anomalous entries.
Exploratory Data Analysis (EDA): We examined the data to uncover trends and relationships.
Univariate: Each feature was analyzed individually. For example, the age distribution showed that stroke patients tended to be older, and stroke patients had higher average glucose levels (a known metabolic risk factor)
cdc.gov
pmc.ncbi.nlm.nih.gov
. Distributions of gender, work type, and smoking status were also checked for imbalances.
Bivariate: We compared features in pairs against the stroke outcome. Patients with hypertension or heart disease had a significantly higher proportion of strokes, consistent with known clinical risk factors
pmc.ncbi.nlm.nih.gov
. Smoking status and marital status also showed notable associations with stroke occurrence
pmc.ncbi.nlm.nih.gov
.
Multivariate: Using 3D scatterplots and pairplots, we found that stroke cases tended to cluster where patients were both older and had higher glucose levels. This multivariate clustering aligns with established risk profiles—older age and elevated blood glucose are significant stroke risk indicators
cdc.gov
pmc.ncbi.nlm.nih.gov
.
Data Preparation: We cleaned and prepared the data for modeling. Missing BMI values were imputed (e.g. using the median). Categorical variables (such as work type and smoking status) were encoded into numerical form. Duplicate records were removed to ensure data integrity.
Model Training: We used an XGBoost classifier due to its strong performance on tabular data. The processed data was split into training and test sets, and basic hyperparameters (like tree depth and learning rate) were tuned using cross-validation. The final model was trained on the training set and then evaluated on the held-out test set.
## Results
Accuracy: 78%
Precision: 0.98 (No Stroke), 0.18 (Stroke)
Recall: 0.77 (No Stroke), 0.78 (Stroke)
F1 Score: 0.87 (No Stroke), 0.30 (Stroke)
Class Imbalance: The dataset is highly imbalanced (the vast majority of patients did not experience a stroke). As a result, the model achieved high overall accuracy largely by predicting the majority “No Stroke” class. It performs very well on the majority class (high precision and recall for “No Stroke”) but struggles to identify the minority class (“Stroke”), yielding very low precision for stroke predictions. The low F1 score (0.30) for the stroke class highlights this issue.
## Conclusion & Recommendations
In conclusion, the XGBoost model achieved moderate overall accuracy but its ability to predict actual stroke cases was limited by the imbalanced data. The model tended to over-predict the majority “No Stroke” class, resulting in high accuracy and precision for that class but poor precision for the “Stroke” class. To improve the model’s performance on stroke prediction, we recommend the following enhancements:
Resampling or Class Weights: Apply techniques like SMOTE (Synthetic Minority Oversampling) or adjust class weights during training to give the minority “Stroke” class more influence. This can help the model learn from the under-represented cases.
Alternative Models: Experiment with other algorithms such as Random Forest, Support Vector Machine, or neural networks. Different models may capture the data patterns in ways that improve minority-class detection.
Feature Engineering: Create new features or interactions that could help distinguish stroke risk. For example, combine or transform existing variables (like BMI categories, or an interaction term between age and glucose) to provide clearer signals.
Hyperparameter Tuning: Conduct a more extensive search (e.g. grid search or Bayesian optimization) to find optimal model parameters. Better-tuned hyperparameters can improve the balance between sensitivity and specificity.
These steps aim to address the class imbalance and enhance the model’s ability to identify true stroke cases, ultimately leading to better risk profiling and earlier interventions.
## Citations
Favicon
Stroke Facts | Stroke | CDC

https://www.cdc.gov/stroke/data-research/facts-stats/index.html
Global, regional, and national burden of stroke and its risk factors, 1990–2019: a systematic analysis for the Global Burden of Disease Study 2019 - PMC

https://pmc.ncbi.nlm.nih.gov/articles/PMC8443449/
Favicon
Stroke Facts | Stroke | CDC

https://www.cdc.gov/stroke/data-research/facts-stats/index.html
Global, regional, and national burden of stroke and its risk factors, 1990–2019: a systematic analysis for the Global Burden of Disease Study 2019 - PMC

https://pmc.ncbi.nlm.nih.gov/articles/PMC8443449/
Stroke Risk Factors, Genetics, and Prevention - PMC

https://pmc.ncbi.nlm.nih.gov/articles/PMC5321635/
Stroke Risk Factors, Genetics, and Prevention - PMC

https://pmc.ncbi.nlm.nih.gov/articles/PMC5321635/
All Sources
Faviconcdc
pmc.ncbi.nlm.nih
