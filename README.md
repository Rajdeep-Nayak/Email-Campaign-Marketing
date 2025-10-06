Email Marketing Campaign Optimization
Project Goal
The main goal of this project is to analyze the performance of an e-commerce company's email marketing campaign. We will determine how many users opened the email and clicked the link inside. Additionally, we will build a Machine Learning model to optimize future campaigns, aiming to maximize the number of users who click on the email link.

Key Questions Answered
Campaign Performance: What percentage of users opened the email, and what percentage clicked on the link within the email?

Predictive Model: Can we build a model based on user data to predict which users are likely to click the link?

Model Impact: By how much can our model improve the Click-Through Rate (CTR)? How would we test this?

User Insights: Did the campaign perform differently for various user segments (e.g., based on country, past purchases)?

Dataset
The project uses 3 data tables:

email_table: Information about each email sent.

email_id: Unique ID.

email_text: The version of the email ("long text" or "short text").

email_version: Whether the email was "personalized" or "generic".

hour: The local time the email was sent.

weekday: The day the email was sent.

user_country: The user's country.

user_past_purchases: How many items the user has purchased in the past.

email_opened_table: IDs of emails that were opened.

link_clicked_table: IDs of emails where the link was clicked.

Project Workflow
Data Preparation:

Merged the three tables (email_table, email_opened_table, link_clicked_table) on email_id to create a master DataFrame.

Created two new columns, opened and clicked, with binary values (1 or 0).

Exploratory Data Analysis (EDA):

Analyzed the data and discovered that the number of users who 'clicked' is very low, indicating an imbalanced dataset.

Created graphs (density plots, box plots) to understand the impact of features like hour and user_past_purchases on the 'clicked' outcome.

Found that emails sent in the morning and evening had a higher click rate.

Users with more past purchases also had a better click rate.

Data Preprocessing:

Encoding: Converted categorical features like email_text, email_version, weekday, and user_country into numerical format using One-Hot Encoding.

Feature Scaling: Scaled numerical features (hour, user_past_purchases) using StandardScaler to help the model train effectively.

Handling Imbalanced Data:

The click-through rate was very low, resulting in a small number of samples in the 'clicked' class.

To fix this, SMOTE (Synthetic Minority Over-sampling Technique) was used to generate more data points for the minority class (clicked=1).

Model Building and Training:

Split the data into 75% for training and 25% for testing.

Trained several classification models:

Logistic Regression

Decision Tree

Random Forest

XGBoost

K-Nearest Neighbors (KNN)

Used RandomizedSearchCV to find the best hyperparameters for each model.

Model Evaluation:

Due to the imbalanced nature of the data, the F1-Score was chosen as the primary metric for evaluating model performance.

All models were compared based on their Test F1-Score.

Results and Conclusion
Campaign Performance:

Email Open Rate: 10.35%

Click-Through Rate (CTR): 2.12%

Model Performance:

Among all the models, the XGBoost Classifier (trained on SMOTE data) performed the best. Its Test F1-Score was the highest, indicating that it can effectively predict 'clicks'.

How the Model Helps:

This model can inform the marketing team which users are most likely to click on an email link before the campaign is even sent.

This allows the team to target only those users with a high probability of clicking, which will increase the campaign's ROI (Return on Investment) and improve the overall click-through rate.

How to Run This Project
Clone the repository:

git clone [https://your-repository-link.git](https://your-repository-link.git)

Install dependencies:

pip install pandas numpy matplotlib seaborn scikit-learn imblearn xgboost

Run the Python script:

Run the Jupyter Notebook (Email_Campaign.ipynb) or the Python script (email_campaign.py).

Ensure the data files (email_table.csv, email_opened_table.csv, link_clicked_table.csv) are in the same folder as the script.
