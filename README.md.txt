# Statistical Hypothesis Testing: Customer Sales Across Operating Regions
### Project Overview
This project investigates whether customer-level sales differ across the company's operating regions.
Rather than comparing independent groups of customers, the analysis focuses on customers who purchased from multiple regions. This allows regional sales to be compared within the same customers while accounting for the dependence between their observations.
The analysis consists of two main comparisons:
1.	**East vs West** - a paired comparison among customers who purchased from both regions.
2.	**Central, East, South and West** - a repeated-measures comparison among customers who purchased from all four regions.
A significance level of **Alpha = 0.05** was used throughout the hypothesis-testing procedures.

### Research Questions
**East vs West**
Do customers generate different levels of sales in the East and West regions?
**Four-Region Comparison**
Do customer sales differ across the Central, East, South and West regions?

### Dataset
The analysis uses the Superstore retail dataset.
The dataset contains transaction-level information including:
-	Customer ID
-	Customer Name
-	Order ID
-	Order Date
-	Ship Date
-	Region
-	Category
-	Sub-Category
-	Product
-	Sales
-	Quantity
-	Discount
-	Profit
For the hypothesis tests, sales were aggregated to the Customer ID × Region level.
This allowed the analysis to compare the same customers across the regions in which they made purchases.

### Data Preparation
The analysis included the following preparation steps:
-	Loaded the retail dataset using pandas.
-	Checked for missing values.
-	Checked for duplicate records.
-	Checked for negative sales values.
-	Aggregated sales by Customer ID and Region.
-	Identified customers who purchased across multiple regions.
-	Selected customers with the required regional coverage for each hypothesis test.
-	Reshaped the data where necessary to create within-customer comparisons.

### Statistical Methods
**1. Paired t-test**
A paired-samples t-test was used to compare East and West sales among customers who purchased in both regions.
The paired structure was used because the observations came from the same customers.
**2. Cohen's d**
Cohen's d was calculated to quantify the standardized magnitude of the East-West difference.
**3. Wilcoxon Signed-Rank Test**
The Wilcoxon signed-rank test was used as a non-parametric alternative to the paired t-test.
**4. Sign-Flip Permutation Test**
A sign-flip permutation test with 10,000 permutations was used as an additional robustness check for the East-West comparison.
**5. Repeated-Measures ANOVA**
A repeated-measures ANOVA was used to compare customer sales across Central, East, South and West among customers who purchased in all four regions.
**6. Log Transformation**
Because sales were strongly right-skewed, a log transformation was applied before the repeated-measures analysis to reduce skewness and the influence of extreme values.
**7. Mauchly's Test and Greenhouse-Geisser Correction**
Mauchly's test was used to assess the sphericity assumption.
Because sphericity was violated, the Greenhouse-Geisser correction was applied to the repeated-measures ANOVA.
**8. Holm-Adjusted Post-hoc Comparisons**
Pairwise comparisons were conducted following the repeated-measures ANOVA, with Holm adjustment applied to control for multiple comparisons.
**9. Four-Region Permutation Test**
A within-customer permutation test was also performed as a robustness check for the four-region analysis.

### Key Results
**East vs West**
The East-West analysis included 32 customers who purchased in both regions.
The paired t-test produced:
-	**t(31) = -0.111**
-	**p = 0.9122**
-	**95% CI = [-501.34, 449.49]**
-	**Cohen's d = -0.020**
The Wilcoxon signed-rank test produced:
-	**W = 252**
-	**p = 0.8320**
The sign-flip permutation test produced:
-	**p = 0.9123**
These results did not provide statistically significant evidence of a difference in customer-level sales between the East and West regions at α = 0.05.

**Four-Region Comparison**
The repeated-measures analysis included 301 customers who purchased in all four regions, producing 1,204 customer-region observations.
The analysis found:
-	**Mauchly's W = 0.95755**
-	**Mauchly's p = 0.02378**
Because the sphericity assumption was violated, the Greenhouse-Geisser correction was applied.
The corrected repeated-measures ANOVA produced:
-	**F = 7.615**
-	**p = Approximately 0.00006**
-	**Generalized eta^2 = 0.019**
The results provided statistically significant evidence that customer-level sales were not identical across all four regions.

### Holm-Adjusted Pairwise Comparisons
| Comparison | Adjusted p-value | Cohen's d | Result at Alpha = 0.05 |
|---|---|---|---|
| Central vs East | 0.049849 | -0.198 | Significant |
| Central vs South | 0.594885 | 0.085 | Not significant|
| Central vs West |	0.010482 | -0.252 |	Significant |
| East vs South | 0.004631 | 0.285 | Significant |
| East vs West | 0.594885 |	-0.047 | Not significant |
| South vs West | 0.000400 | -0.342 | Significant |

The four-region within-customer permutation test produced:
-	**p = 0.0451**

Overall Findings
The East-West comparison did not show statistically significant evidence of a difference in customer-level sales.
In contrast, the four-region repeated-measures analysis detected a statistically significant overall regional difference after applying the Greenhouse-Geisser correction.
The post-hoc analysis indicated that several regional pairs differed, while Central vs South and East vs West were not statistically significant after Holm adjustment.
The permutation analysis also produced a p-value below 0.05 for the four-region comparison, although the evidence was considerably weaker than the corrected parametric ANOVA result.
Tools and Technologies
-	Python
-	Jupyter Notebook
-	pandas
-	NumPy
-	SciPy
-	Matplotlib
-	Seaborn
-	Pingouin
-	Statistical hypothesis testing
-	Permutation testing
-	Repeated-measures analysis

### Project Structure
```text 
Statistical-Hypothesis-Testing/
|
|-- README.md
|-- hypothesis_testing.ipynb
|
|-- results/
|   |-- statistical_results.csv
|
|-- visualizations/
|   |-- east_west_difference.png
|   |-- qq_plot.png
|   |--regional_sales.png
|
|-- report/
    |--statistical_analysis_report.pdf
```

### Skills Demonstrated
This project demonstrates practical application of:
-	Data cleaning and validation
-	Data aggregation
-	Data reshaping
-	Exploratory data analysis
-	Within-subject statistical analysis
-	Paired hypothesis testing
-	Repeated-measures ANOVA
-	Assumption checking
-	Data transformation
-	Effect size interpretation
-	Non-parametric testing
-	Permutation testing
-	Multiple-comparison correction
-	Statistical result interpretation
-	Python-based data analysis

### Author
**Israel Adewale**
Aspiring Data Analyst | Aspiring Data Analyst | Python | SQL | Power BI | Excel
