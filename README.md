# Excel-dashboard
📊 A state-wise dataset of Indian engineering colleges categorized by quality ratings (Excellent, Good, Low, Worst), including data cleaning scripts, visual dashboards, and ready-to-use insights for education analysis.

# 📘 Documentation – Indian Engineering Colleges Dashboard

## 📁 Project Title:
**Indian Engineering Colleges Quality Analysis**

## 👨‍💻 Author:
**JAYAPRAKASH K**  
Artificial Intelligence & Data Science 
kangeyam instituions

---

## 📝 Project Overview

This project focuses on analyzing the state-wise quality distribution of engineering colleges in India. A tabular dataset extracted from an Excel workbook was cleaned and converted into a structured CSV format. Using Python-based tools, several interactive and visual dashboards were generated to aid stakeholders in understanding regional education quality trends.

The goal was to convert raw, inconsistent data into clear, usable insights that support decisions in education policy, college selection, or quality assessment.

---

## 📊 Dataset Summary

The dataset consists of an aggregated count of engineering colleges grouped by:

- **State / Union Territory**
- **Quality Rating**:
  - `Excellent`
  - `Good`
  - `Low`
  - `Worst`
  - `Invalid Data`

Each row corresponds to a specific Indian state and displays the number of colleges in each rating category.

---

## 🧹 Data Preparation & Cleaning Process

All cleaning was performed using **Python (Pandas)**.

### ✅ Key Data Cleaning Steps:

1. **Header Normalization**:
   - Removed the top metadata rows from the Excel pivot table.
   - Renamed `Excellant` column to `Excellent`.

2. **Data Type Conversion**:
   - Converted all rating columns to numeric (`int`), replacing NaNs with `0`.

3. **Row Filtering**:
   - Removed the aggregate row labeled `"Grand Total"` to focus only on state-wise values.

4. **Column Derivation**:
   - Calculated total colleges per state from row sums for dashboard purposes.
   - Exported the cleaned data to `Indian_Engineering_Colleges_Clean.csv`.

---

## 📐 Dashboard Design Overview

Three static visual dashboards were created using **Matplotlib**, suitable for embedding or publishing:

- ✅ **Top 10 States by College Count**
- ✅ **Stacked Rating Distribution by State**
- ✅ **Overall Rating Share (Pie Chart)**

> Additionally, a dynamic Streamlit dashboard was developed for real-time filtering and interaction.

### 🔑 Visual Elements Used:
- Bar Charts
- Stacked Column Charts
- Pie Charts
- Streamlit KPI Cards
- Dropdown Slicers (in app.py)

---

## 📌 Key Metrics Explained

| Metric                  | Description                                      |
|-------------------------|--------------------------------------------------|
| Total Colleges          | Total number of engineering colleges per state   |
| Excellent Institutions  | High-quality institutions rated “Excellent”      |
| Low/Worst Institutions  | Indicates potential regions needing attention    |
| Invalid Data Entries    | Flags issues in original dataset quality         |
| Quality Mix %           | Relative share of each rating per state          |

---

## 🧠 Key Insights Derived

1. **Kerala, Andhra Pradesh, and Maharashtra Lead**:  
   These states top the list in the number of engineering colleges.

2. **Strong Skew Toward “Good” Ratings**:  
   Across India, ~53% of institutions fall under “Good” — a likely signal of moderate standards or optimistic evaluations.

3. **Very Few Institutions Rated “Worst”**:  
   Less than 2% of colleges fall under this category, suggesting either genuinely high standards or a lack of stringent auditing.

4. **Some States Lack Quality Distribution**:  
   A few states report only one or two rating types — calling for more granular and standardized data.

5. **Potential Data Inconsistencies**:  
   “Invalid Data” entries hint at collection or classification issues in original data sources.

---

## 🧮 Python Code & Logic Used

Key analysis and plotting were done using:

```python
# Example: Clean & Convert Columns
df['Excellent'] = pd.to_numeric(df['Excellent'], errors='coerce').fillna(0).astype(int)

# Example: Total Colleges Per State
df['Total Colleges'] = df[['Excellent', 'Good', 'Low', 'Worst']].sum(axis=1)

# Example: Pie Chart for Overall Rating Distribution
df[['Excellent', 'Good', 'Low', 'Worst']].sum().plot.pie(autopct='%1.1f%%')
