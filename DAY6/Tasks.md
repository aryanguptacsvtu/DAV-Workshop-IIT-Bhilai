### 📁 data_analysis.csv – Attendance Dataset (for Q1)
---
**LIVE UPDATES**: [LINK](https://forms.gle/ubejNZsUhT7AgQJZA)
---

This dataset captures the daily attendance records of students who participated in the Data Analytics & Machine Learning workshop. Each row represents one student, and each date column contains their attendance status for that session.

#### *📄 Column Descriptions:*

| Column Name | Description |
|-------------|-------------|
| Sno | Serial number of the student entry |
| ID | Unique student ID (enrollment/registration number) |
| Name | Full name of the student |
| 2025-02-03, 2025-02-03 Lab, ..., 2025-04-25 | Columns representing each workshop session. Attendance is marked as:<br> - P: Present<br> - A: Absent<br> - NA: Not applicable or class not held |
| Total | Total number of sessions the student attended (count of P values across date columns) |

#### *🧾 Dataset Summary:*
- Timeframe: February 3, 2025 to April 25, 2025
- Each student may have attended multiple theory and lab sessions.
- Data includes possible missing values and inconsistent entries which must be cleaned.

#### *📊 Objective:*
Perform detailed EDA:
- Clean and preprocess missing or malformed values
- Calculate attendance percentages
- Identify attendance trends and correlations
- Visualize patterns over time and across groups (gender, sessions, students)

---

### 📁 dataset_cars – Car Dataset (for Q2)

This dataset contains historical listings of used cars, with various attributes that affect pricing. The task is to build a regression model to predict car prices using these features.
This contains train.csv and test.csv
Follow the sample_submission.csv for submission of your predicted output

#### *📄 Column Descriptions:*

| Column Name | Description |
|-------------|-------------|
| Brand | Manufacturer of the car (e.g., BMW, Mercedes-Benz, etc.) |
| Model | Specific model of the car (e.g., 320, Sprinter 212) |
| Body | Type of the car body (e.g., sedan, van, SUV, etc.) |
| Mileage | Mileage driven by the car (in thousands of kilometers) |
| EngineV | Engine volume (in liters) – e.g., 2.0, 5.0 |
| Engine Type | Type of engine: Petrol, Diesel, or Gas |
| Registration | Whether the car is registered (yes or no) |
| Year | Year the car was manufactured |
| Price | *Target variable* – the price at which the car is/was listed for sale |

#### *🧾 Dataset Summary:*
- The dataset includes both categorical and numerical features.
- May contain missing values or outliers (e.g., very high EngineV or low Mileage).
- The target variable (Price) is continuous and suited for regression.

#### *📊 Objective:*
- Clean and preprocess the data
- Convert categorical data to numerical (encoding)
- Handle missing values and outliers
- Train regression models to predict Price
- Evaluate model performance using R² Score, MAE, and MSE


### ✅ *Q1 – Attendance Data Analysis (50 Marks)*

| No. | Task Description | Marks |
|-----|------------------|-------|
| 1 | Data Cleaning / Preprocessing | 5 |
| 2 | Identify top 5 most present and absent students | 5 |
| 3 | Plot histogram of attendance for all students individually - week-wise | 5 |
| 4 | Group students based on attendance percentage (Hint: using Inter Quartile Range) | 5 |
| 5 | Analyze correlation between different days of the week | 10 |
| 6 | Identify patterns/correlation of attendance among students | 5 |
| 7 | Check if events (exam/holiday) correlate with spikes in absenteeism | 5 |
| 8 | Save at least one visual as .jpg/.png & export the clean dataset as .csv | 5 |

> 💡 You may use libraries such as pandas, matplotlib, seaborn, or plotly for analysis and visualization.

---

### ✅ *Q2 – Car Price Prediction (30 Marks)*

| Component | Description | Marks |
|-----------|-------------|-------|
| Model Preprocessing | Handle missing values, encode categorical variables, scale/transform features | 5 |
| Model Training & Prediction | Use any regression model (e.g., Linear, Random Forest, XGBoost) | 5 |
| Evaluation Metrics | Provide R² Score, Mean Absolute Error (MAE), and Mean Squared Error (MSE) on test data | 20|

📤 *Submit:*
- test.csv – Your predicted prices
- car_price_prediction.ipynb – Your modeling notebook

---

### ✅ *Q3 – MCQ Quiz (20 Marks)*

- Conducted via Google Form
- Covers workshop topics (EDA, Visualization, Machine Learning, Preprocessing)
