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

### 1.2. Handling Categorical Missing Data (`Region`)
*   **Problem:** Two rows for the country "Mexico" were missing their `Region` designation.
*   **Solution (Logical Imputation):** Instead of deleting these valuable rows, I performed a **logical lookup**. By filtering for other "Mexico" entries, I confidently identified their region as **"North America"** and imputed the missing values, preserving data integrity.

### 1.3. Handling Numerical Missing Data (`Average_Monthly_Income`)
*   **Problem:** One row for "Australia" and one for "Mexico" were missing their `Average_Monthly_Income` values.
*   **Solution (Grouped Median Imputation):** A simple global mean would be statistically inaccurate. I chose a more robust method: **Grouped Median Imputation**. The plan was to fill each missing value with the median income of its corresponding region ("Oceania" for Australia, "North America" for Mexico).
*   **Challenge:** Executing this plan revealed significant software limitations, which became a problem-solving exercise in itself (detailed in Section 3).

### 1.4. Handling Duplicate Rows
*   A final check for complete duplicate entries was performed using Excel's "Remove Duplicates" function.
*   **Result:** No complete duplicate rows were found in the dataset, confirming the uniqueness of each entry.

---

## 2. Analysis, Visualization & Key Insights

After cleaning and preparing the data, I leveraged PivotTables and visualizations to uncover the core story hidden within.

### Insight 1: Europe Leads in Gross Income, But Global Disparity is Stark

A PivotTable was used to aggregate the average income and cost of living by geographical region, providing a high-level macroeconomic overview.

💡 **Critical Note on Methodology:** An initial analysis using `Sum` was identified as statistically flawed due to varying sample sizes across regions. The aggregation method was corrected to **`Average`** to ensure a fair, normalized comparison.

**Chart 1: Average Monthly Income vs. Average Cost of Living by Region**

[!!! CHÈN ẢNH BIỂU ĐỒ CỘT NHÓM VÀO ĐÂY !!!]

**Analysis:**
The chart reveals a clear economic hierarchy among the continents. **Europe** emerges as the leader with the highest average monthly income (approx. $4,477), followed by Africa and Oceania. This visualization immediately highlights the significant economic disparities that exist on a global scale.

**Business Implication:**
This finding confirms that a one-size-fits-all business strategy is unviable. Pricing models, marketing campaigns, and product positioning must be hyper-localized. A premium product strategy that thrives in Europe might fail in regions with lower income thresholds. Market entry decisions must be heavily informed by these regional economic realities.

---

### Insight 2: Disposable Income, Not Total Income, Reveals True Purchasing Power

High income is an incomplete metric; it is the **disposable income (Income - Cost)** that truly measures a population's financial well-being and purchasing power. A second analysis was performed to calculate and visualize this critical metric.

**Chart 2: Average Disposable Income by Country (Income - Cost)**

[!!! CHÈN ẢNH BIỂU ĐỒ CỘT THU NHẬP KHẢ DỤNG VÀO ĐÂY !!!]

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

[!!! CHÈN ẢNH CHỤP MÀN HÌNH MENU PIVOTTABLE KHÔNG CÓ 'MEDIAN' !!!]

### Barrier 2: No "Add to Data Model" Feature
Plan B was to use the "Add to Data Model" feature, which often unlocks advanced DAX calculations like `MEDIANX`. This feature is completely absent from my Excel for Mac instance.

**Proof: Missing 'Add to Data Model' Checkbox**

[!!! CHÈN ẢNH CHỤP MÀN HÌNH HỘP THOẠI 'CREATE PIVOTTABLE' KHÔNG CÓ CHECKBOX !!!]

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
