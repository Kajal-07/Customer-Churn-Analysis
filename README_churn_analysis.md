# Customer Churn Analysis

## Project Overview

This project explores customer churn in a telecommunications dataset using Python. The goal is to understand how churn is distributed across customer groups and subscription characteristics, and to identify areas that a business could investigate to improve customer retention.

The notebook performs data inspection and preparation, followed by exploratory data analysis (EDA) using visualizations of churn status, demographics, tenure, contract type, payment method, and subscribed services.

> **Scope note:** This is an exploratory analysis. The charts show associations and distributions; they do not, by themselves, prove why customers churn or establish that a particular retention action will work.

## Business Objective

Customer churn can reduce recurring revenue and increase the cost of acquiring replacement customers. This analysis aims to:

- Measure the overall split between churned and retained customers.
- Explore churn patterns across demographic groups.
- Compare churn with contract type, tenure, payment method, and subscribed services.
- Identify segments that may merit deeper investigation by a customer-retention team.

## Dataset

The notebook loads a CSV file named `Customer_churn.csv`. The dataset contains customer-level information, including:

- Customer identifier and demographic attributes
- Tenure and contract type
- Phone and internet services and optional add-ons
- Payment method and billing information
- Churn status

The notebook uses 7,043 customer records and 21 columns. The target field is `Churn`.

## Tools and Libraries

- **Python** — analysis workflow
- **Pandas** — data loading, cleaning, grouping, and cross-tabulation
- **NumPy** — numerical operations
- **Matplotlib** — chart creation and formatting
- **Seaborn** — statistical visualizations
- **Jupyter Notebook** — interactive analysis environment

## Workflow

1. Load the customer dataset with Pandas.
2. Inspect column types and dataset structure using `df.info()`.
3. Convert `TotalCharges` to a numeric type. In the notebook, blank values are replaced with `0` based on the assumption that these records have zero tenure and no total charges recorded.
4. Check for missing values and duplicate customer IDs.
5. Convert the `SeniorCitizen` indicator from `1`/`0` to `yes`/`no` labels.
6. Explore churn distributions and relationships using count plots, a pie chart, a histogram, stacked percentage bars, and a 3×3 grid of service-related count plots.

### Visualizations included

- Overall customer churn count and proportion
- Churn by gender
- Customer distribution by senior-citizen status and churn percentage by senior-citizen status
- Customer tenure distribution split by churn
- Churn by contract type
- Churn by payment method
- Churn across phone service, multiple lines, internet service, online security, online backup, device protection, technical support, streaming TV, and streaming movies

## Executive Summary

The notebook analyzes 7,043 customers. Of these, 1,869 are marked as churned, giving an overall churn rate of approximately **26.54%**. The remaining 5,174 customers (approximately **73.46%**) are marked as retained.

The visualizations compare churn across customer demographics, tenure, contract types, payment methods, and service subscriptions. Contract type and optional services are useful dimensions for further investigation. However, count plots alone can be influenced by the size of each category, so category-level churn rates should be calculated before making firm comparisons.

The analysis provides a starting point for customer-retention work: identify higher-churn segments, examine whether churn is concentrated among newer customers, and assess how billing and service choices relate to churn.

## Key Business Questions to Explore Further

- Which contract types have the highest **within-category churn rate**?
- Is churn concentrated among customers with shorter tenure?
- How does churn vary by payment method and monthly-charge range?
- Are customers without online security or technical support more likely to churn after accounting for differences in customer mix?
- Which customer segments represent the greatest potential revenue impact?

## Recommendations

1. **Use rates as well as counts.** Calculate churn percentages within each contract, payment, demographic, and service category so that segments of different sizes can be compared fairly.
2. **Investigate early-tenure churn.** Group customers into tenure bands and calculate the churn rate for each band.
3. **Review contract and payment patterns.** Identify categories with elevated churn rates and explore customer experience or billing factors that may be relevant.
4. **Evaluate service add-ons carefully.** Compare churn rates for customers with and without each add-on; do not assume that an association means the service itself causes retention.
5. **Measure retention interventions.** If the business tests onboarding, support, or renewal initiatives, track churn and retention outcomes to assess whether the intervention makes a difference.

## Data Quality Notes and Limitations

- The notebook replaces blank `TotalCharges` entries with `0` based on zero tenure. This assumption should be verified against the source records before final reporting.
- The notebook checks missing values and duplicate customer IDs; retain the printed results in the notebook or report so that the data-quality outcome is explicit.
- The tenure histogram cell ends with `plt.show` rather than `plt.show()`. Add the parentheses if you want Matplotlib to explicitly display the figure in that cell.
- The current work is descriptive EDA. It does not include statistical significance testing, causal analysis, a churn prediction model, or quantified revenue-at-risk calculations.
- Monetary values should be reported with the appropriate currency only after confirming the dataset's currency convention.

## How to Run

1. Clone or download this repository.
2. Ensure Python and Jupyter Notebook are installed.
3. Place `Customer_churn.csv` in the same directory as the notebook, or update the CSV path in the first notebook cell.
4. Install the required libraries:

   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```

5. Open `churn_analysis.ipynb` in Jupyter Notebook or VS Code and run the cells in order.

## Repository Structure

```text
customer-churn-analysis/
├── churn_analysis.ipynb
├── Customer_churn.csv       # Add locally if permitted by the dataset license
├── customer_services_churn.png  # Optional exported visualization
└── README.md
```

## Conclusion

This project demonstrates an end-to-end exploratory workflow for investigating customer churn with Python. It establishes a baseline churn rate and explores how churn is distributed across customer and service categories. The next analytical step is to calculate segment-level churn rates and connect those patterns to tenure, billing, and potential business impact before recommending targeted retention actions.

---

**Project type:** Exploratory Data Analysis (EDA)  
**Primary topic:** Customer churn and retention  
**Status:** EDA notebook completed; deeper segment-rate analysis and business-impact evaluation are recommended next steps.
