# BFSI-Classification

Supervised ML algorithms to perform a binary classification task. Here's a breakdown of the code:

The training dataset consists of two csv: X_train and y_train in the Training folder.<br />
X_train:<br />
o Unique_ID: Represent the Unique Identifier<br />
o	C1 to C8: Represents Categorical columns<br />
o	N1 to N35: Represent Numerical columns<br />
y_train:<br />
o	Unique_ID: Represent the Unique Identifier<br />
o	Dependent_Variable: Represent the outcome or dependent variable<br />

The testing dataset consist of two csv: X_test and final_predictions in the Testing folder.<br />
ROC_AUC uses probability estimates of the positive class for its calculation. Therefore, the final outcome is a probability estimate for the positive class (e.g. 0.82), not the class label (e.g. 0 or 1), which is stored in final_predictions.csv which is obtained on applying the trained model on X_test.csv.

Data Preprocessing:
1. Dropping Unique_ID Column: The Unique_ID column is dropped from X_df and X_test_df using the drop function.
One-Hot Encoding: Categorical columns in the datasets are one-hot encoded using pandas' get_dummies function, and the encoded data is stored back in X_df and X_test_df.
2. Imputation of Missing Values: The script imputes missing values in the concatenated dataset (concatenated_df = X_df + X_test_df) by filling them with the mean of their respective columns.
3. Scaling Numerical Columns: The numerical columns in the concatenated dataset are scaled using the StandardScaler from sklearn.preprocessing. The scaled columns are stored in df_scaled.
4. Splitting into X and X_test: The concatenated dataset (df_scaled) is split back into X_df and X_test_df based on the original shape.
5. Handling Class Imbalance: The script uses the Synthetic Minority Over-sampling Technique (SMOTE) from the imblearn library to handle class imbalance. It oversamples the minority class to balance the dataset.

Model Selection and Hyperparameter Tuning:
The scoring metrics used include precision, recall, F1-score, AUC-ROC, and accuracy.
The algorithms used are:
1. Logistic Regression
2. K-Nearest Neighbors (KNN)
3. Random Forest

Saving Predictions:<br />
o	ROC_AUC uses probability estimates of the positive class for its calculation. Therefore, the final outcome is a probability estimate for the positive class (e.g. 0.82), not the class label (e.g. 0 or 1). 
o	The probability estimates for the positive class are saved along with the corresponding Unique_ID in a DataFrame named y_test_df. The final results can be saved to a CSV file for further analysis or evaluation.

Current Best Model: Random Forest Classifier with One Hot Encoding, present in the DS_OneHotEncoder_MeanImputation.ipynb script.
