# Loan Data from Prosper
## by Abiola Ogunbajo


## Dataset

The Loan Data from Prosper dataset is a financial dataset which is related to the loan, borrowers, interest rates, etc. Prosper or Prosper Marketplace Inc. is a San Francisco, California based company specializing in loans at low interest rates to the borrowers. We are using the dataset from Prosper for exploratory data analysis.The dataset from prosper is comprised of 81 variables and contains 113937 entries.

I selected 15 variables out of the initial 81 variables for visualization. They are: 
- LoanKey - Unique key for each loan. This is the same key that is used in the API.  
- Term - The length of the loan expressed in months.
- LoanStatus - The current status of the loan: Cancelled,  Chargedoff, Completed, Current, Defaulted, FinalPaymentInProgress, PastDue. The PastDue status will be accompanied by a delinquency bucket.
- BorrowerAPR - The Borrower's Annual Percentage Rate (APR) for the loan.
- BorrowerRate - The Borrower's interest rate for this loan. 
- ListingCategory (numeric) - The category of the listing that the borrower selected when posting their listing: 0 - Not Available, 1 - Debt Consolidation, 2 - Home Improvement, 3 - Business, 4 - Personal Loan, 5 - Student Use, 6 - Auto, 7- Other, 8 - Baby&Adoption, 9 - Boat, 10 - Cosmetic Procedure, 11 - Engagement Ring, 12 - Green Loans, 13 - Household Expenses, 14 - Large Purchases, 15 - Medical/Dental, 16 - Motorcycle, 17 - RV, 18 - Taxes, 19 - Vacation, 20 - Wedding Loans
- EmploymentStatus - The employment status of the borrower at the time they posted the listing.
- IsBorrowerHomeowner - A Borrower will be classified as a homowner if they have a mortgage on their credit profile or provide documentation confirming they are a homeowner. 
- DebtToIncomeRatio, The debt to income ratio of the borrower at the time the credit profile was pulled. This value is Null if the debt to income ratio is not available. This value is capped at 10.01 (any debt to income ratio larger than 1000% will be returned as 1001%).
- IncomeRange - The income range of the borrower at the time the listing was created.
- IncomeVerifiable - The borrower indicated they have the required documentation to support their income.
- StatedMonthlyIncome - The monthly income the borrower stated at the time the listing was created.
- LoanOriginalAmount - The origination amount of the loan.
- MonthlyLoanPayment - The scheduled monthly loan payment.
- Investors - The number of investors that funded the loan.

#### Assessing Data
After assesing the dataset for visualization, there were duplicate rows, complex column names and non-descriptive listing categories.

#### Cleaning Data
The duplicate rows were dropped using pandas' drop_duplicates method, the column names were renamed with more suitable names using pandas' rename function and the non-descriptive listing categories were replaced with a descriptive listing categories using .replace() method.

The main features of interest in this dataset are Borrower APR, Borrower Rate, Term, Loan Status, Loan Original Amount, Stated Monthly Income and Monthly Loan Payment.
The features in the dataset that will support an investigation into the features of interest are Listing Category, Employment Status, Is Borrower A Home Owner?, Debt to Income Ratio, Income Verifiable and Investors.

## Summary of Findings


Many borrowers select 'debt consolidation' as the listing category, take loans for 36 months and are also employed.  The loan status with the maximum frequency is current followed by completed. Loans that are past due have the minimum frequency.This implies that most borrowers pay their loans in time.
Whether the borrower is a home owner or not does not affect the loan status.The distributions of the variables of interest are mostly unimodal and right skewed. There were unusual points in the histogram plot of the Stated Monthly Income. I performed log transformation on the Stated Monthly Income to focus on the most relevant parts.There was an unusual distribution in the histogram of the debt to income ratio. There were values greater than 1 which is unlikely because the debt to income ratio is not greater than 1.These points were considered as outliers and were removed from the data and assigned to a new dataframe. The outliers were removed because they represent errors in the data.
There was an interesting interaction among the monthly loan payment, loan original amount and term of loans. There is a higher positive correlation between monthly loan payment and loan original amount in borrowers with 12 months as the term of loans compared to borrowers with 36 and 60 months as the term of loans.
I plan on bringing some visualizations into the explanatory presentation. The visualizations are: 
1. The count of the length of loans
2. The most selected listing category
3. The effect of the borrower's verifiable income on the loan status
4. The interaction between the monthly loan payment, loan original amount by term of loans


## Key Insights for Presentation

The relationship between the monthly loan payment, loan original amount by term of loans and the effect of the borrower's verifiable income on the loan status will be selected to polish up for presentation.
The figsize of all the visualization will be increased to make them wider than normal. The currency for the monthly loan payment and loan original amount will be added together with the axis label for better understanding.

