# MIS-311
# MIS 311 Project: An Exploratory Data Analysis of Global Cost of Living

This repository documents my project for **MIS 311: Introduction to Business Analytics**. The objective was to perform a comprehensive Exploratory Data Analysis (EDA) on a global "Cost of Living" dataset, transforming raw data into actionable business insights.

The analytical process was structured into three core phases:
1.  **Data Pre-processing and Cleaning:** Establishing a reliable foundation by ensuring data integrity.
2.  **Descriptive Statistics and Visualization:** Summarizing and visualizing data to uncover patterns and relationships.
3.  **Insight Generation:** Interpreting the visuals to derive meaningful business conclusions.

---

## 1. Data Pre-processing and Cleaning

This initial phase was critical for ensuring the accuracy and validity of all subsequent analyses.

### 1.1. Initial Inspection & Missing Value Strategy
The dataset contained 201 rows. An initial inspection revealed 4 cells with missing values across both categorical (`Region`) and numerical (`Average_Monthly_Income`) columns, which required a strategic approach to handle.

<img width="289" height="431" alt="image" src="https://github.com/user-attachments/assets/a28ef6ff-8ea2-469e-96a2-98c821d3defb" />
<img width="298" height="426" alt="image" src="https://github.com/user-attachments/assets/272e47b2-3233-4f96-ae44-4ed203f3a39c" />

### 1.2. Handling Categorical Missing Data (`Region`)
*   **Problem:** Two rows for the country "Mexico" were missing their `Region` designation.
*   **Solution (Logical Imputation):** Instead of deleting these valuable rows, I performed a **logical lookup**. By filtering for other "Mexico" entries, I confidently identified their region as **"North America"** and imputed the missing values, preserving data integrity.
<img width="282" height="482" alt="image" src="https://github.com/user-attachments/assets/19660ab5-937f-4f19-9216-c3952a289ea3" />
<img width="429" height="466" alt="image" src="https://github.com/user-attachments/assets/e44bf8ed-f6f7-43bf-bf6e-1347fce37dd0" />

### 1.3. Handling Numerical Missing Data (`Average_Monthly_Income`)
*   **Problem:** One row for "Australia" and one for "Mexico" were missing their `Average_Monthly_Income` values.
    <img width="428" height="50" alt="image" src="https://github.com/user-attachments/assets/e78d040c-5a1d-4b72-b53a-c835c2719710" />

*   **Solution (Grouped Median Imputation):** A simple global mean would be statistically inaccurate. I chose a more robust method: **Grouped Median Imputation**. The plan was to fill each missing value with the median income of its corresponding region ("Oceania" for Australia, "North America" for Mexico).
*   **Challenge:** Executing this plan revealed significant software limitations, which became a problem-solving exercise in itself (detailed in Section 3).

### 1.4. Handling Duplicate Rows
*   A final check for complete duplicate entries was performed using Excel's "Remove Duplicates" function.
    <img width="282" height="482" alt="image" src="https://github.com/user-attachments/assets/9aef7229-18de-4835-a6c9-a6a92b006dfd" />
    <img width="254" height="223" alt="image" src="https://github.com/user-attachments/assets/c00f3694-ec48-4317-a7b5-cd5ee62fb02c" />

---

## 2. Analysis, Visualization & Key Insights

After cleaning and preparing the data, I leveraged PivotTables and visualizations to uncover the core story hidden within.

### Insight 1: Europe Leads in Gross Income, But Global Disparity is Stark

A PivotTable was used to aggregate the average income and cost of living by geographical region, providing a high-level macroeconomic overview.

💡 **Critical Note on Methodology:** An initial analysis using `Sum` was identified as statistically flawed due to varying sample sizes across regions. The aggregation method was corrected to **`Average`** to ensure a fair, normalized comparison.

**Chart 1: Average Monthly Income vs. Average Cost of Living by Region**

<img width="279" height="141" alt="image" src="https://github.com/user-attachments/assets/e7ba60e1-878a-4da4-9026-b943b9701551" />

<img width="560" height="252" alt="image" src="https://github.com/user-attachments/assets/eb7af988-4dd3-4e82-803e-f0ae1a107791" />


**Analysis:**
A surprising finding is that **Africa** reports the highest average monthly income (approx. $4,695), slightly ahead of Oceania and Europe. 

However, the more critical story lies in the **"gap"** between income and cost.
*   **Europe** exhibits the **largest positive gap**, meaning its income significantly surpasses its living costs. This indicates strong real purchasing power.
*   In contrast, regions like **Africa and Oceania**, despite high incomes, also face high costs, resulting in a tighter financial margin.
*   The most striking case is **North America**, where income and cost are nearly identical, indicating almost zero financial leeway for the average person.

**Business Implication:**
This analysis proves that looking at gross income alone is insufficient.
*   **Opportunity:** Europe stands out as the most promising market for premium goods and services because its consumers have the highest potential disposable income.
*   **Challenge:** North America, while seemingly an affluent market, is extremely price-sensitive. Businesses should focus on value-driven strategies rather than luxury positioning. The tight financial situation of its consumers is a critical factor for market entry and product strategy.

---

### Insight 2: Disposable Income, Not Total Income, Reveals True Purchasing Power

High income is an incomplete metric; it is the **disposable income (Income - Cost)** that truly measures a population's financial well-being and purchasing power. A second analysis was performed to calculate and visualize this critical metric.
<img width="637" height="409" alt="image" src="https://github.com/user-attachments/assets/d9ae5022-44f4-4edc-b9f6-3aa2d38e9fc0" />
<img width="764" height="101" alt="image" src="https://github.com/user-attachments/assets/5fce5c78-c0ca-45db-9dda-49daf2fa16b6" />


**Chart 2: Average Disposable Income by Country (Income - Cost)**
<img width="303" height="672" alt="image" src="https://github.com/user-attachments/assets/7747d2ae-9e6a-4429-9ff9-a36b9a650bd6" />
<img width="230" height="325" alt="image" src="https://github.com/user-attachments/assets/c74f7be4-feb7-49d1-888a-1154cb7640bb" />

<img width="557" height="290" alt="image" src="https://github.com/user-attachments/assets/fe7e6ccd-2bc8-44c8-babb-41ebb73c7e32" />


**Analysis:**
This chart tells a surprising story that reframes the previous insight. While Europe has high gross incomes, it is **Germany and France** that truly excel, boasting the highest disposable incomes (over $1,000 left over monthly).

The most startling finding comes from **North America**. Despite its status as a high-income region, **Canada and the United States show a net financial deficit** in this dataset, with average living costs exceeding average income. This "financial squeeze" points to a challenging consumer environment.

**Business Implication:**
This is the most actionable insight of the analysis.
*   **Opportunity:** European nations like Germany and France represent prime markets for premium and luxury goods, as their consumers possess the highest real purchasing power.
*   **Risk:** North American markets, particularly Canada, appear to be extremely price-sensitive despite high top-line incomes. Businesses operating here should prioritize value-driven offerings, promotions, and flexible payment options, as consumers are financially constrained. This insight challenges the simplistic assumption that "high-income country = easy market."

---

## 3. Technical Challenges & Problem-Solving

A significant part of this project involved navigating and overcoming software limitations to implement the chosen "Grouped Median" imputation method.

### Barrier 1: No `Median` Function in PivotTables
My version of Excel for Mac does not include `Median` as a standard aggregation option in the "Value Field Settings".

**Proof: Missing 'Median' in PivotTable Menu**

<img width="339" height="364" alt="image" src="https://github.com/user-attachments/assets/e415a801-c98a-4f0c-851d-441ea5209257" />
<img width="332" height="357" alt="image" src="https://github.com/user-attachments/assets/283f3d85-f897-4e57-95d5-a96a85ce9bca" />



### Barrier 2: No "Add to Data Model" Feature
Plan B was to use the "Add to Data Model" feature, which often unlocks advanced DAX calculations like `MEDIANX`. This feature is completely absent from my Excel for Mac instance.

**Proof: Missing 'Add to Data Model' Checkbox**

<img width="485" height="361" alt="image" src="https://github.com/user-attachments/assets/37419bf4-bff9-48a9-aeb8-0cad310426cf" />


### Barrier 3: No `MEDIANIFS` Function
Plan C involved a direct formula, `=MEDIANIFS(...)`. However, my version of Excel does not support this function, returning a `#NAME?` error.

### 🏆 The Solution (Plan D - Manual but Accurate)
Forced to pivot, I reverted to a "classical" but 100% accurate manual method:
1.  **Filter:** Applied a filter to the `Region` column (e.g., "Oceania").
2.  **Highlight:** Selected all visible cells in the `Average_Monthly_Income` column.
3.  **Read Status Bar:** Read the auto-calculated `Median` value from Excel's Status Bar at the bottom of the window.
4.  **Impute & Repeat:** Manually entered this value and repeated the process for "North America".

This problem-solving journey, while time-consuming, demonstrates a commitment to analytical accuracy and adaptability when faced with technical barriers.

---

## 4. Conclusion

This Exploratory Data Analysis of the Cost of Living dataset yielded two pivotal findings:
1.  While Europe reports the highest gross income, significant economic disparities persist on a global scale.
2.  More importantly, **true purchasing power is dictated by disposable income, not total income.** This analysis uncovered the critical insight that some of the highest-earning nations in the dataset (Canada and the US) are financially squeezed, making them unexpectedly challenging consumer markets.

The project underscored the importance of methodological rigor (e.g., using Average over Sum) and the necessity of creative problem-solving. The insights derived from this analysis can directly inform strategic business decisions related to market prioritization, pricing, and product strategy.
