### Cross Column Validation

During the cross-column validation process, the consistency between related columns was checked.

**Validation Rule**

Total Spending ~ Purchase Count * Average Order Value

**Result**

One inconsistent record was identified where the value of 'total_spending' did not match the calculated value 

**Action**

The record was flagged for review during the data cleaning process.

## Formatting Consistency Result: No formatting inconsistencies (such as mixed letter case, leading/ trailing spaces, or duplicate category labels) were detected in the categorical columns.




##Correlation Analysis
Correlation analysis showed a moderate positive relationship (r = 0.51) between purchase_count and total_spending, indicating that customers with more purchases generally spend more overall. Weak positive correlations were observed between age and total_spending (r = 0.34) and between avg_order_value and total_spending (r = 0.35). Weak negative correlations were found between satisfaction_score and both last_purchase_days (r = -0.29) and returned_items (r = -0.28). No strong correlations (|r| ≥ 0.8) were observed among the numerical features, suggesting a low risk of multicollinearity.