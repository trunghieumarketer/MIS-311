# MIS-311
# MIS 311 Project: Cost of Living Exploratory Data Analysis (EDA)

This repository documents my project for **MIS 311: Introduction to Business Analytics**. The objective was to perform a complete Exploratory Data Analysis (EDA) on a global "Cost of Living" dataset, moving from raw data to actionable insights.

The process involved three core phases:
1.  **Data Pre-processing and Cleaning:** Ensuring data integrity.
2.  **Descriptive Statistics and Visualization:** Summarizing and visualizing data to find patterns.
3.  **Insight Generation:** Interpreting the visuals to derive key business insights.

---

## 1. Data Pre-processing and Cleaning

This was the most critical phase to ensure the analysis was built on a reliable foundation.

### 1.1. Initial Inspection & Missing Value Strategy
The initial inspection of the 201-row dataset revealed critical missing values in 4 cells, impacting both categorical and numerical data.

### 1.2. Handling Categorical Missing Data (`Region`)
* **Problem:** Two rows for the country "Mexico" were missing their `Region`.
* **Solution (Logical Imputation):** Instead of deleting these valuable rows or guessing, I performed a **logical lookup**. By filtering for other "Mexico" entries in the dataset, I confidently identified their region as **"North America"** and imputed the missing values.

### 1.3. Handling Numerical Missing Data (`Average_Monthly_Income`)
* **Problem:** One row for "Australia" and one for "Mexico" were missing their `Average_Monthly_Income`.
* **Solution (Grouped Median Imputation):** A simple "global mean" would be inaccurate. I selected the most statistically robust method: **Grouped Median Imputation**.
    * The goal was to fill "Australia's" missing income with the **median income of its region ("Oceania")**.
    * And fill "Mexico's" missing income with the **median income of its region ("North America")**.
* **Challenge:** Executing this plan revealed significant technical limitations in my software stack, which became a problem-solving challenge in itself (detailed in Section 3).

### 1.4. Handling Duplicate Rows
* A final check for complete duplicate rows was performed using Excel's "Remove Duplicates" function.
* **Result:** `[Enter your result, e.g., "No duplicate values were found." or "Removed X duplicate rows."]`

---

## 2. Analysis, Visualization & Key Insights

After cleaning the dataset, I used PivotTables and charts to tell a story.

### Insight 1: Deep Economic Disparity Exists Between Regions

I used a PivotTable to aggregate the average income and cost of living by region.

💡 **Critical Note:** My initial analysis using `Sum` was **statistically flawed** because the regions had different sample sizes (e.g., 73 entries for Europe vs. 12 for South America). Comparing `Sum` is meaningless. I corrected this by changing the aggregation to **`Average`** to ensure a fair, apples-to-apples comparison.

**Chart 1: Average Monthly Income vs. Average Cost of Living by Region**
> `[!!! INSERT YOUR CLUSTERED COLUMN CHART IMAGE HERE !!!]`
> 
> *(Drag-and-drop your .png/.jpg file here to upload it)*

**Analysis:**
The chart clearly visualizes the deep economic disparity between regions. **[Your Highest Region, e.g., Europe]** demonstrates a significantly higher average income and cost of living compared to all other regions. In stark contrast, **[Your Lowest Region, e.g., Africa]** has the lowest averages for both metrics.

**Implication:** This confirms that a one-size-fits-all business strategy for pricing, marketing, or product development is not viable. Go-to-market strategies must be hyper-localized based on regional economic realities.

---

### Insight 2: High Income Strongly Correlates with High Cost of Living

To explore the *relationship* between income and cost, I generated a Scatter Plot.

**Chart 2: Relationship between Monthly Income and Cost of Living**
> `[!!! INSERT YOUR SCATTER PLOT IMAGE HERE !!!]`
>
> *(Drag-and-drop your .png/.jpg file here to upload it)*

**Analysis:**
The scatter plot reveals a strong **positive correlation** between average monthly income (X-axis) and cost of living (Y-axis). The data points form a clear upward-sloping trend from left to right.

**Implication:** This challenges the simple assumption that "high salary equals a better life." It suggests that in high-income countries, a significant portion of that income is consumed by a proportionally high cost of living. This directly impacts real purchasing power and savings potential.

---

## 3. ⚠️ Technical Challenge & Problem-Solving (Excel for Mac Limitations)

A significant part of this project was overcoming software limitations to implement the "Grouped Median" (Plan A).

### Barrier 1: No `Median` Function in PivotTables
My version of Excel for Mac does not include `Median` as a standard option in the "Value Field Settings...".

> **Proof: Missing 'Median' in PivotTable Menu**
> `[!!! INSERT IMAGE PROOF 1: Screenshot of your PivotTable settings menu showing NO 'Median' option !!!]`

### Barrier 2: No "Add to Data Model" Feature
Plan B was to use the "Add to Data Model" feature, which often unlocks advanced calculations like `Median`. This feature is completely absent from my Excel for Mac instance.

> **Proof: Missing 'Add to Data Model' Checkbox**
> `[!!! INSERT IMAGE PROOF 2: Screenshot of your "Create PivotTable" dialog box, proving the checkbox is not there !!!]`

### Barrier 3: No `MEDIANIFS` Function
Plan C was to use a direct formula, `=MEDIANIFS(...)`. My version of Excel does not support this function, returning a `#NAME?` error.

### 🏆 The Solution (Plan D - Manual but Accurate)
I reverted to a "classical" but 100% accurate manual method:
1.  **Filter:** Applied a filter to the `Region` column (e.g., "Oceania").
2.  **Highlight:** Selected all visible cells in the `Average_Monthly_Income` column.
3.  **Read Status Bar:** Read the auto-calculated `Median` value from Excel's Status Bar.
4.  **Repeat:** Repeated the process for "North America".

This problem-solving process, while time-consuming, demonstrates my commitment to finding the most accurate analytical method despite facing significant technical barriers.
