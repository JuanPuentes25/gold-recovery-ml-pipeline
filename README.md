# gold-recovery-ml-pipeline
End-to-end machine learning project to predict gold recovery from mining data. Includes data cleaning, validation of recovery calculations, exploratory analysis of metal concentrations, anomaly detection, and model evaluation using sMAPE with cross-validation.

🟡 Gold Recovery Prediction using Machine Learning
📌 Project Overview

This project focuses on predicting gold recovery at different stages of an industrial flotation and purification process using machine learning techniques.

The objective is to build a robust predictive model that estimates:

Rougher recovery (initial flotation stage)

Final recovery (after purification)

Accurate predictions can help optimize industrial operations, improve efficiency, and support data-driven decision-making in mineral processing.

🎯 General Objective

Develop a machine learning model capable of accurately predicting gold recovery in both the rougher and final stages of the extraction process using historical process data.

✅ Specific Objectives

Perform data cleaning and preprocessing on industrial time-series data

Prevent data leakage by aligning training features with test features

Handle missing values appropriately using time-aware techniques

Analyze metal concentration behavior across process stages

Train and evaluate a regression model using sMAPE as the main metric

Assess model performance and identify opportunities for improvement

📊 Dataset Description

The dataset contains operational parameters from a gold extraction process, including:

Flotation inputs (feed composition, reagents)

Process parameters (air flow, levels)

Intermediate and final outputs (metal concentrations and recovery rates)

Key Characteristics:

Time-series data (date column)

80+ numerical features

Separate datasets:

Training set

Test set

Full dataset (reference)

🔍 Data Exploration & Insights
1. Missing Values Handling

Missing values were present across multiple variables

Forward fill (ffill) was used due to the temporal nature of the data

This approach preserves process continuity better than median imputation

2. Data Leakage Prevention

The training dataset contained variables not available in the test set

These columns were removed to ensure realistic model training

✔ Result:

Final feature set: 53 variables

3. Recovery Formula Validation

The recovery formula was validated against the dataset:

𝑅
𝑒
𝑐
𝑜
𝑣
𝑒
𝑟
𝑦
=
𝐶
(
𝐹
−
𝑇
)
𝐹
(
𝐶
−
𝑇
)
×
100
Recovery=
F(C−T)
C(F−T)
	​

×100

Mean Absolute Error (MAE): ~ 9.3e-15

Confirms data consistency and correct implementation

4. Metal Concentration Analysis
🟡 Gold (Au)

Increases significantly through each stage

Confirms process effectiveness

⚪ Silver (Ag)

Slight increase after flotation

Decreases in final stage → likely removed during purification

⚫ Lead (Pb)

Gradual increase across stages

Indicates partial retention during processing

5. Distribution Analysis

Outliers (near-zero concentrations) were removed

Train and test distributions are consistent

Ensures good model generalization

⚙️ Data Preprocessing Steps

Sort datasets by time (date)

Apply forward fill for missing values

Remove leakage-prone features

Align training and test feature spaces

Drop rows with missing target values

🤖 Model Training
Model Used:

Random Forest Regressor

Validation Strategy:

Cross-validation (5-fold)

Evaluation Metric:

sMAPE (Symmetric Mean Absolute Percentage Error)

𝑠
𝑀
𝐴
𝑃
𝐸
=
∣
𝑦
𝑡
𝑟
𝑢
𝑒
−
𝑦
𝑝
𝑟
𝑒
𝑑
∣
∣
𝑦
𝑡
𝑟
𝑢
𝑒
∣
+
∣
𝑦
𝑝
𝑟
𝑒
𝑑
∣
sMAPE=
∣y
true
	​

∣+∣y
pred
	​

∣
∣y
true
	​

−y
pred
	​

∣
	​

📈 Results
Metric	Value
Rougher sMAPE	7.06%
Final sMAPE	5.62%
Combined sMAPE	5.98%
🧠 Model Performance Analysis
✔ Better Performance in Final Stage

The model predicts final recovery more accurately

Likely due to more stable process conditions

✔ Strong Overall Accuracy

Combined sMAPE below 6% indicates solid predictive performance

⚠️ Rougher Stage Complexity

Higher error suggests:

More variability

More complex relationships in early-stage processing
