# <div style="background-color: lightblue; padding: 8px;">Lending Club Case Study</div>

## Introduction

In this case study, we will dive into an extensive analysis of a dataset encompassing **loan details** issued from **2007 to 2011**. Our primary objective is to apply `Exploratory Data Analysis (EDA)` techniques to uncover key factors that contribute to **loan defaults**.

Loan default is a **critical issue** in the financial sector, **impacting** both lenders and borrowers. Understanding the underlying patterns and factors influencing defaults can help financial institutions better **manage risk**, **optimize** loan issuance strategies, and **improve** overall decision-making processes. 

By leveraging **historical loan data**, we aim to identify and analyze the variables that significantly correlate with **loan default**, providing actionable **insights** for stakeholders.



## Table of Contents
* [Business Understanding](#Business-Understanding)
* [Loan Decision Scenarios](#Loan-Decision-Scenarios)
* [Business Objective](#Business-Objective)
* [Dataset Overview](#Dataset-Overview)
* [Data Preparation](#Data-Preparation)
* [Exploratory Data Analysis (EDA)](#Exploratory-Data-Analysis-(EDA))
* [Results](#Results)
* [Conclusion and Recommendation](#Conclusion-and-Recommendation)
* [Technology used](#Technology-used)
* [References](#References)



## Business Understanding

You work for a consumer finance company that specializes in lending various types of loans to urban customers. When the company receives a loan application, it must make a critical decision regarding loan approval based on the applicant’s profile. This decision involves assessing two types of risks:

- **Opportunity Loss:** If the applicant is likely to repay the loan, then not approving the loan results in a loss of potential business for the company.
<br><br>
- **Financial Risk:** If the applicant is not likely to repay the loan, i.e., is likely to default, then approving the loan may lead to a financial loss for the company. <br><br>
- The dataset provided contains information about past loan applicants and whether they ‘defaulted’ or not. The aim is to identify patterns that indicate if a person is likely to default. This information can be used to make more informed decisions regarding loan approval, such as: <br>

> **Denying the Loan:** For applicants likely to default.<br>
> **Reducing the Loan Amount:** To minimize risk exposure.<br>
> **Adjusting Interest Rates:** Charging a higher rate for riskier applicants.
<!-- You don't have to answer all the questions - just the ones relevant to your project. -->

## Loan Decision Scenarios

When a person applies for a loan, the company can make one of the following decisions:

- **Loan Accepted:** If the company approves the loan, there are three possible scenarios:

> **Fully Paid:** The applicant has fully paid the loan, including both principal and interest.<br>
> **Current:** The applicant is in the process of paying the installments, i.e., the tenure of the loan is not yet <br> 
> **completed:** These candidates are not labeled as 'defaulted'.
- **Charged-Off:** The applicant has not paid the installments in due time for a prolonged period, indicating they have defaulted on the loan.
- **Loan Rejected:** The company rejected the loan (because the candidate did not meet the requirements, etc.). Since the loan was rejected, there is no transactional history of those applicants with the company and thus this data is not available in the dataset.

## Business Objective

This company is a leading online loan marketplace, facilitating personal loans, business loans, and financing for medical procedures. **Borrowers** can easily access lower interest rate loans through a streamlined online interface.

Like most lending companies, the primary **financial risk** is associated with lending to **‘risky’ applicants**, leading to what is known as **credit loss**. Credit loss refers to the amount of money lost by the lender when the borrower refuses to pay or defaults on the loan. In this case, customers labeled as **'charged-off'** are considered the 'defaulters'.

Identifying risky loan applicants is crucial for reducing credit loss. By leveraging `Exploratory Data Analysis (EDA)`, the company aims to uncover the driving factors behind loan defaults. Understanding these **driver variables**, i.e., the variables that are strong indicators of **default**, allows the company to improve its portfolio and risk assessment strategies.

## Dataset Overview 

The dataset under examination includes comprehensive records of loans issued over a five-year period, with features ranging from borrower demographics to loan characteristics and payment history. 
 Key attributes are:

- **loan_status:** The status of the loan (e.g., Fully Paid, Charged Off, Current). This is the `target` variable.
- **annual_inc:** Annual income of the applicant.
- **loan_amnt:** Amount of the loan.
- **int_rate:** Interest rate of the loan.
- **purpose:** Purpose of the loan (e.g., credit_card, debt_consolidation).
- **dti:** Debt to income ratio of applicant.
- **grade:** Cradit rating of the applicant (e.g., A,B..G).
- **term:** Duration for which loan has been taken (e.g., 36 Months, 60 Months)

This rich dataset provides a fertile ground for applying various `EDA techniques` to gain insights into the following aspects:

> 1. **Understanding the Distribution of Loan Characteristics:** Analyzing attributes such as loan amount, interest rate, and loan term to assess their impact on loan performance.
<br>
> 2. **Examining Borrower Profiles:** Investigating demographic factors, such as annual income, employment length, and credit history, to understand their influence on loan default rates.
<br>
> 3. **Exploring Loan Default Patterns:** Identifying patterns and trends in loan defaults over time, and uncovering any correlations with specific loan features or borrower characteristics.

## Data Preparation

Data preparation involves:

1. **Handling Missing Values:** Imputation or removal of missing values.
2. **Data Transformation:** Converting categorical variables to numerical values if needed.
3. **Outlier Detection:** Identifying and handling outliers to ensure the quality of analysis.
4. **Derived Metrices:** Creating new metric from the existing columns.

For instance, missing values in `revol_util` were imputed using the median value of the column. Similarly, categorical variables such as `loan_status` were encoded for analysis. Outliers were identified using bocplot in attributes like `funded_amnt`, `funded_amnt`.  New metrics were derived like `loan_amnt_categories` , `annual_inc_categories`, `Year`, `installment_category`

## Exploratory Data Analysis (EDA)

In this section, we perform EDA to uncover patterns and relationships in the data:

1. **Univariate Analysis:** Analyzing individual features (e.g., distribution of `loan amounts`).
2. **Bivariate Analysis:** Examining relationships between two variables (e.g., `loan_status` vs `purpose`).
3. **Segmented Analysis:** Examining relationships between two variables (e.g., `Default rate` vs `Grade` segmented by `purpose`).
4. **Multivariate Analysis:** Understanding interactions between multiple features (e.g., `annual_inc` vs `loan_amnt`).

Visualizations and statistical summaries are provided to support our findings.

## Results

Key findings from the analysis include:

1. **Income and Charged-Off Proportion:**
   - There is a clear inverse relationship between the annual income of borrowers and the proportion of charged-off loans. Lower annual incomes tend to correlate with higher charged-off proportions.

2. **Loan Purpose and Default Risk:**
   - Loans taken for small business purposes exhibit the highest charged-off proportion compared to other loan purposes. This suggests that small business loans carry a higher default risk.

3. **Loan Grade and Default Risk:**
   - As the LC assigned loan grade (`grade`) decreases from 'A' to 'G', the charged-off proportion increases. Grade 'A' represents the highest credit rating, while 'G' represents the lowest.

4. **Interest Rate and Default Risk:**
   - There is a positive correlation between the interest rate (`int_rate`) and charged-off proportion. Higher interest rates are associated with higher default risk.

5. **Public Bankruptcy Records:**
   - The charged-off proportion increases with an increase in the count of public bankruptcy record number for borrowers.

6. **Loan Term and Interest Rate:**
   - Longer loan terms are associated with higher interest rates. This indicates that borrowers opting for longer terms incur higher interest costs.

7. **Debt-to-Income Ratio and Interest Rate:**
   - There is a positive relationship between the debt-to-income ratio and interest rate. As the debt-to-income ratio increases, so does the interest rate.

8. **Loan Grade and Interest Rate:**
   - Similar to default risk, as the LC assigned loan grade (`grade`) decreases from 'A' to 'G', the interest rate increases. Lower-grade loans are associated with higher interest rates.

9. **Loan Amount and Interest Rate:**
   - Interest rates tend to increase with higher loan amounts. This suggests that larger loans are associated with higher interest costs.

10. **Interest Rate by Purpose:**
    - Loans for small business purposes have the highest interest rates compared to other loan purposes.

11. **Loan Amount and Annual Income:**
    - There is a positive correlation between the loan amount and annual income of borrowers. Higher annual incomes tend to correlate with higher loan amounts.

12. **Annual Income and Debt-to-Income Ratio:**
    - There is a negative correlation between annual income and debt-to-income ratio. Higher incomes tend to be associated with lower debt-to-income ratios.

13. **Small Business Loans and Default Rate Across Grades:**
    - Small business loans consistently exhibit the highest default rates across all loan grades ('A' to 'G'). Additionally, the default rate for small business loans increases as the credit rating of borrowers decreases.

14. **Default Rates Across Loan Terms:**
    - Small business loans have higher default rates compared to other loan purposes, across both 36-month and 60-month term loans.

15. **Small Business Loans Across Housing Types:**
    - Small business loans consistently exhibit the highest default rates across borrowers residing in rented houses, owning houses, or having mortgaged houses. <br>
16. **Interest Rate and Credit Utilization:**
    - There is a positive correlation between interest rate and credit utilization `revol_util`. Higher the credit utilization higher is the interest rate. <br>
    
** ChargedOff_Proportion and Default_rate refers to : The percentage of loans that have been defaulted


## Conclusion and Recommendation

Based on the findings from the analysis, the following recommendations are suggested for the loan provider/bank:

1. **Risk Assessment and Loan Approval:**
   - Implement a stricter assessment for borrowers with lower annual incomes, particularly for loans with small business purposes, given their higher default risk.

2. **Credit Rating and Interest Rates:**
   - Adjust interest rates based on the LC assigned loan grade ('A' to 'G') to better reflect the risk associated with different credit ratings. Lower-grade loans should incur higher interest rates.

3. **Debt Management and Loan Terms:**
   - Encourage borrowers to manage their debt-to-income ratios effectively, as higher ratios are linked to higher interest rates and potential default risks, especially for longer loan terms.

4. **Monitoring Small Business Loans:**
   - Enhance monitoring and risk management strategies specifically for small business loans, which consistently exhibit higher default rates across different metrics.

5. **Housing Status and Loan Performance:**
   - Consider the housing status of borrowers (rented, owned, mortgaged) when assessing default risks for small business loans, as default rates remain consistently high across different housing types.


## Technologies Used
- numpy -     version 1.23.0
- pandas -    version 1.5.3
- seaborn -   version 0.13.2
- matplotlib- version 3.5.1

## References

- Dataset Source: https://drive.google.com/file/d/1d5huiJYyUJia2LZp-4Cw_IxmMlfqLaFz/view?usp=drive_link

