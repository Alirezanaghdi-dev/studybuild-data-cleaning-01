# E-commerce Customer Data Cleaning Project (project-01-data-cleaning-MoAminNKC)

## Project Overview
In this project, I explored and cleaned a dataset of e-commerce customers to identify issues and logically correct them. The goal was to transform raw, messy data into a reliable dataset ready for Exploratory Data Analysis (EDA) and further business insights.

## Tools & Technologies
- **Languages/Libraries:** Python, Pandas, NumPy, ydata-profiling [cite: 1, 2]
- **Environments:** Jupyter Notebook [cite: 1, 2]
- **Software:** Microsoft Excel [cite: 1]

## Data Cleaning Workflow

### 1. Handling Duplicates
- Identified and removed one completely duplicate row, reducing the dataset from 61 to 60 records. [cite: 1]

### 2. Missing Values & Outliers
- **Age:** Addressed missing values and illogical entries (e.g., an age of 145, or ages < 0 / > 120) by replacing them with the median age (45) to prevent outliers from skewing the data. [cite: 1]
- **Total Spending:** Resolved missing and incorrect values (e.g., a massive outlier of 25,000) by recalculating them using the established formula: `total_spending = purchase_count * avg_order_value`. [cite: 1]
- Statistical outliers in total spending were capped (Winsorized) using the Interquartile Range (IQR) method to preserve high-spending customer data without skewing averages. [cite: 1]

### 3. Structural Cleaning & Type Conversion
- Converted the `signup_date` column from string/object to proper datetime formats. [cite: 1]
- Adjusted the `age` column to integer after resolving missing values. [cite: 1]
- Stripped hidden leading/trailing spaces across all text columns. [cite: 1]
- Standardized text casing (e.g., Title Case for names, cities, and membership tiers, and Upper Case for genders). [cite: 1]

### 4. Logical Inconsistencies & Data Standardization
- **Purchase vs. Returns:** Discovered records where `returned_items` exceeded `purchase_count`. Rather than guessing, these impossible values were converted to NaN to maintain data integrity.
- **Gender Standardization:** Mapped and corrected gender values (`M` for Male, `F` for Female) based on the most frequent occurrence for each first name to resolve data entry inconsistencies. [cite: 1]

### 5. The Manual Review Process
- Advanced validation masks were created to flag categorical errors (invalid genders, tiers) and relational math mismatches. [cite: 1]
- Instead of applying a blanket automated script to fix complex discrepancies, these flagged rows were exported to a separate file (`requires_manual_fix.xlsx`). [cite: 1]
- I cleaned this subset by hand, as this deliberate, manual approach ensured higher accuracy for nuanced errors. 
- The manually corrected data was then re-integrated with the primary clean dataset to form the final `cleaned_dataset.xlsx`. [cite: 1]

### 6. Exploratory Data Analysis (EDA)
- With the dataset fully cleaned, column names were mapped to readable titles (e.g., `avg_order_value` to `Average Order Value`). [cite: 2]
- Utilized `ydata_profiling` to automatically generate a comprehensive HTML report for in-depth data profiling. 👉 **[Click here to view the Customer Analysis Report](https://MoAminNKC.github.io/studybuild-data-cleaning-01/submissions/Project01-MoAminNKC/report/customer_analysis_report.html)** [cite: 2]

## Final Result
The final output is a pristine dataset of 60 records, free of duplicates, illogical values, and formatting errors, alongside an automated profiling report for immediate business analysis. [cite: 1, 2]
