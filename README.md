The Vinho Verde dataset consists of physicochemical and sensory data for Portuguese "Vinho Verde" wines. It is used to train models to predict wine quality based on objective chemical tests. In this project, a binary classification method is used to get the quality of wine. 

1. Data Loading & Cleaning

Loaded data from a CSV
Dropped rows with null values and removed the Id column.

2. Exploratory Data Analysis

Plotted histograms of all features to see their distributions.
Built a correlation heatmap (via seaborn) to spot relationships between features like acidity, alcohol, sulphates, etc.
Plotted the distribution of the quality score specifically, which showed it's heavily imbalanced. Most wines cluster around quality 5–6, with very few rated 3, 4, 7, or 8.

3. Problem Reframing

Converted the multi-class quality score into a binary target: 1 if quality ≥ 7 ("good" wine), 0 otherwise. 

4. Handling Class Imbalance
The crux of this project is to understand how to handle class imbalance.   
The data was split 80/20 (stratified) into train/test sets.
Applied SMOTE (Synthetic Minority Oversampling) on the training set only, to balance the two classes before fitting the model. 

6. Model Training

Trained a RandomForestClassifier (100 trees) on the SMOTE-resampled data.
Evaluated with a classification report and ROC AUC (~0.89) and plotted an ROC curve.

6. Model Evaluation

Built a confusion matrix and accuracy score

7. Threshold Tuning

Computed precision-recall curves across thresholds, then found the threshold that maximizes F1-score for the minority class (good wine).
Best threshold is around 0.53, giving an F1 score of 0.63 for class 1. Plotted precision/recall/F1 vs. threshold.
