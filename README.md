# Customer Churn Analysis Dashboard

## 📌 Project Goal & Overview

The primary objective of this project is to build a **comprehensive customer churn analysis dashboard**. The workflow includes:

* **SQL** for data extraction, transformation, and loading (ETL)
* **Power BI** for interactive dashboards and business insights
* **Python** (Jupyter Notebook) for predictive modeling using machine learning

The project covers both **historical churn analysis** and **future churn prediction**, enabling businesses to understand customer behavior and reduce churn rates.

---

## 🗄️ Part 1: Data Preparation and ETL in SQL

### Database Setup

* Created a new database: `db_churn`
* Loaded raw "Telecom customer churn" data into a **staging table** (`stg_churn`) using the flat file import wizard

### Data Cleaning

* Checked for nulls, missing values, and inconsistencies
* Cleaned and transferred data into a **production table** (`prod_churn`)

### Views Created

* **`vw_churn_data`** → historical customers (stayed or churned), used for **model training**
* **`vw_join_data`** → new joiners, used for **prediction**

---

## 📊 Part 2: Dashboard Creation in Power BI

### Data Modeling

* Imported `prod_churn` into Power BI
* Created new columns:

  * `Churn Status` → binary column (1 = churned, 0 = stayed)
  * `Monthly Churn Status`, `Tenure Group` → for analysis buckets

### DAX Measures

* **Total Customers** → count of all customers
* **New Joiners** → count of recent customers
* **Total Churn** → count of churned customers
* **Churn Rate** → percentage of churned customers

### Dashboard Visuals (Summary Page)

* **KPI Cards** → churn KPIs
* **Demographics** → churn by gender, age group
* **Account Analysis** → churn by contract type, payment method, tenure group
* **Geographic Analysis** → top churn states
* **Services Analysis** → impact of services (phone, internet, streaming, etc.)
* Applied formatting, color scheme, and tooltips for better UX

---

## 🤖 Part 3: Predictive Modeling in Python

### Algorithm

* **Random Forest Classifier** chosen for robustness and interpretability

### Data Preprocessing

* Loaded `vw_churn_data` (historical data)
* Dropped unnecessary columns (`customerID` etc.)
* Encoded categorical features with **Label Encoding**
* Train-test split: **80% training, 20% testing**

### Model Training & Evaluation

* Trained Random Forest on training set
* Evaluated with:

  * **Confusion Matrix**
  * **Classification Report** (accuracy, precision, recall, F1)
* Analyzed **Feature Importance** to identify key churn factors

### Prediction

* Used the trained model to predict churn on `vw_join_data` (new customers)
* Saved predictions to CSV for Power BI

---

## 📈 Final Dashboard: Churn Prediction Page

The second dashboard page focuses on **predicted churners**:

* **Customer List** → table of predicted churner IDs
* **KPIs** → number of predicted churners, breakdown by gender
* **Charts** → profile of at-risk customers (age, marital status, contract type, payment method)
* Added navigation buttons to switch between **Historical Summary** and **Prediction Page**

---

## 🚀 Business Value

This solution enables:

* Understanding historical churn drivers
* Identifying at-risk customers before they leave
* Designing **targeted retention campaigns** to reduce churn and increase customer lifetime value
