Customer Churn & Retention Analytics

An Analysis of Customer Churn Drivers, Revenue at Risk, and Retention Opportunities in a Telecom Customer Base
Overview
Customer Churn & Retention Analytics is an end-to-end data analytics project designed to transform a raw, messy customer dataset into actionable retention insights.
The project cleans and validates the data, identifies the customer groups most likely to leave, estimates the revenue lost to churn, and tests whether a retention offer would be financially worthwhile.
Business Objective
The objective is to build a repeatable analytics pipeline that can:
•	Measure the overall churn rate
•	Identify the customer characteristics linked to higher churn
•	Understand why customers leave
•	Quantify the revenue lost to churn
•	Define a high-risk customer segment for targeted action
•	Estimate the break-even point of a retention offer
•	Support retention decisions with data
Technology Stack
•	Python — Data cleaning, validation, and transformation
•	Pandas — Data manipulation, segmentation, and KPI calculations
•	Excel — Raw and cleaned data files
•	Power BI — Interactive dashboard and DAX measures
•	GitHub — Version control and portfolio management
Technology Flow
Excel (raw) → Python + Pandas → Excel (clean) → Power BI → Business Insights
Project Workflow
RAW DATA
Excel (1,225 rows, 18 columns)
     │
     ▼
PYTHON DATA CLEANING
Load → Detect → Standardize → Fix → Validate
     │
     ▼
CLEAN DATASET
Excel (1,200 rows, 20 columns)
     │
     ├──────────────────┐
     ▼                  ▼
PYTHON ANALYSIS     POWER BI
Churn drivers &     Interactive
retention scenario  Dashboard
     │                  │
     └────────┬─────────┘
              ▼
       BUSINESS INSIGHTS
              │
              ▼
     RETENTION ACTION PLAN
              │
              ▼
       DECISION SUPPORT
Python cleans and analyzes the data → Power BI communicates it → Business analysis drives retention decisions.
Dataset
The project uses a synthetic telecom customer dataset created for this project. It contains 1,225 raw records and 18 variables, deliberately built with real-world data-quality problems so that the cleaning work is part of the project.
The dataset covers dimensions such as:
•	Customer ID
•	Gender and Senior Citizen status
•	Partner and Dependents
•	City
•	Signup Date
•	Tenure (months)
•	Contract type
•	Internet Service
•	Online Security and Tech Support add-ons
•	Payment Method and Paperless Billing
•	Monthly Charges and Total Charges
•	Churn and Churn Reason
Note: Because the data is synthetic, the findings demonstrate the analytical method and are not claims about a real company.
Data Preparation & Cleaning
Python was used as the cleaning layer to prepare the raw customer dataset before analysis. The raw file was never edited, and all cleaning was done on a copy.
The cleaning process included:
•	Loading the raw dataset using Pandas
•	Verifying dataset dimensions, data types, and missing values
•	Removing duplicate customer records
•	Standardizing inconsistent text labels
•	Converting Total Charges to a numeric field
•	Parsing three different date formats into one
•	Flagging impossible values (negative tenure, unrealistic charges)
•	Recalculating missing values from related columns
•	Resolving logic conflicts between columns
•	Running automated validation checks and saving the clean dataset
Cleaning Flow
Raw Dataset → Pandas → Issue Detection → Standardization → Missing-Value Treatment → Logic Checks → Validation → Clean Dataset
Data Quality Issues Resolved

#	Issue	Fix
1	Duplicate customer records (25)	Trimmed IDs, removed duplicates
2	Inconsistent labels (for example M2M, bangalore, Y/1)	Mapped every variant to one standard label
3	Dollar signs and blank text in Total Charges	Stripped symbols, converted to numeric
4	Mixed date formats	Parsed each format explicitly
5	Negative tenure (8 rows)	Recalculated from Signup Date
6	Unrealistic monthly charges (6 rows)	Set to missing, recalculated
7	Missing tenure, monthly and total charges	Derived from related columns
8	Missing internet plan (41 rows)	14 inferred from add-ons, 26 labelled Unknown
9	Add-ons conflicting with "No internet"	Standardized to "No internet service"
10	Churn reason recorded for customers who stayed (14)	Cleared
11	Churned customers with no reason (21)	Labelled "Not recorded"
Assumption: The data extraction date was taken as 30 June 2026 to recalculate missing tenure from signup dates. Where tenure already existed, this method matched it over 99.9% of the time.
Business Analysis
The cleaned data was analyzed across multiple business dimensions:
•	Overall churn rate
•	Churn by contract type
•	Churn by customer tenure group
•	Churn by internet service
•	Churn by payment method
•	Churn by senior citizen status, paperless billing, and gender
•	Churn reasons
•	Revenue lost to churn
•	High-risk segment identification
•	Retention offer scenario and sensitivity analysis
Key KPIs
KPI	Result
Total Customers	1,200
Churned Customers	456
Churn Rate	38.0%
Monthly Revenue Lost	$29,610
Annual Revenue Lost	$355,314
High-Risk Segment Churn Rate	61.2%
High-Risk Segment Share of All Churn	29.4%
Power BI Dashboard
Power BI was used to transform the analyzed customer data into an interactive dashboard. All dashboard figures were cross-checked against the Python results.
 
Dashboard Page — Customer Churn & Retention
The dashboard provides visibility into:
•	Total Customers
•	Churned Customers
•	Churn Rate
•	Monthly Revenue Lost
•	Annual Revenue Lost
•	High-Risk Churn Rate
•	Churn Rate by Contract Type
•	Churn Rate by Customer Tenure
•	Churn Rate by Internet Service
•	Churn Rate by Payment Method
•	Churned Customers by Reason
•	Revenue Lost by Contract Type
•	City, Contract, Internet Service, and Payment Method filters
Key Business Insights
1. Churn Is a Significant Revenue Problem
The overall churn rate is 38.0%, with 456 of 1,200 customers lost. Churned customers were paying about $29,610 per month, an estimated annual revenue loss of approximately $355K.
Business implication: Churn is large enough to justify a dedicated retention program.
2. Month-to-Month Contracts Are the Strongest Churn Driver
Month-to-month customers churn at 52.3%, compared with 25.3% for one-year and 9.9% for two-year contracts.
Business implication: Moving customers onto longer contracts is the most direct lever for reducing churn.
3. Churn Is Concentrated in the First Year
Customers with 0-12 months of tenure churn at 58.2%, falling to 9.3% for customers with more than four years of tenure.
Business implication: Early-life onboarding and engagement deserve the most attention.
4. The High-Risk Segment Drives Nearly a Third of All Churn
Month-to-month customers in their first 12 months make up 18.2% of the customer base (219 customers) but account for 29.4% of all churn, with a 61.2% churn rate. Within this group, fiber optic customers churn at 80.0%.
Business implication: Retention effort should be targeted at this segment first, with fiber optic customers prioritized.
5. Price and Competitor Offers Drive About Half of Churn
Price too high (127) and better competitor offer (116) together explain 243 of the 456 churned customers.
Business implication: Pricing and competitive positioning are central to any retention strategy.
6. Fiber Optic and Electronic Check Customers Churn More
Fiber optic customers churn at 48.5% (versus 20.5% for customers with no internet service), and electronic check payers churn at 45.7% (versus 31.0% for bank transfer).
Business implication: Service quality and pricing for fiber customers, and autopay incentives for check payers, are worth investigating. These are associations, not proven causes.
7. Gender and Paperless Billing Are Not Churn Drivers
Churn is nearly identical across paperless billing (38.1% vs 37.8%) and shows only a small difference by gender (39.4% vs 36.7%).
Business implication: These factors should not be used to design retention actions.
8. A Retention Offer Breaks Even at About a 15% Save Rate
Assuming a 10% discount for all 219 high-risk customers, the offer breaks even if it keeps 14.8% of at-risk customers. At an assumed 25% save rate, the net benefit is about $9,980 per year.
Save Rate	Net Annual Benefit
10%	-$4,726
15%	$176
25%	$9,980
35%	$19,784
Business implication: The offer is worth testing, but the real save rate should be confirmed with an A/B test before a full rollout. The 25% save rate and 10% discount are assumptions, not facts from the data.
Management Recommendation Priorities
Priority	Area	Recommended Action
High	Month-to-month customers in their first year	Offer an incentive to move to an annual contract
High	Fiber optic customers in the high-risk segment	Investigate pricing and network quality for this group
Medium	Price and competitor offers	Review pricing and benchmark competitor offers
Medium	Electronic check payers	Encourage lower-risk payment methods such as autopay
Medium	Retention offer	Run an A/B test to measure the real save rate
Monitor	Gender and paperless billing	No action needed, continue monitoring
Business Value
The project helps management move from observing churn to understanding it, sizing it, and acting on it.
Key business benefits include:
•	Clear visibility of churn and revenue at risk
•	Identification of the customers most likely to leave
•	Understanding of why customers leave
•	A financial test of a retention offer before it is launched
•	Prioritized, data-backed decision-making
•	A repeatable Python → Power BI reporting workflow
Limitations
•	The dataset is synthetic, so findings demonstrate the method and do not describe a real business.
•	The save rate and discount in the retention scenario are assumptions.
•	The analysis shows association, not causation.
•	Derived and median values were used to fill gaps, which can slightly understate natural variation.
•	The "Unknown" internet-plan group contains only 26 customers and should not be read as a reliable segment.
Future Improvements
Potential enhancements include:
1.	Building a churn prediction model (for example, logistic regression) to score each customer's risk
2.	Running an A/B test to measure the real effect of the retention offer
3.	Loading the data into SQL Server and moving the KPI calculations into SQL
4.	Automating the Excel → Python → Power BI refresh process
5.	Adding customer lifetime value to prioritize high-value customers
6.	Automated alerts when churn rises in a segment
7.	Replacing synthetic data with real operational data
Project Structure
Customer-Churn-Analytics/
│
├── data/
│   ├── telco_churn_raw.xlsx
│   └── telco_churn_clean.xlsx
│
├── python/
│   └── churn_analysis.py
│
├── powerbi/
│   └── Customer_Churn_Dashboard.pbix
│
├── screenshots/
│   └── customer_churn_dashboard.png
│
├── README.md
└── requirements.txt
Conclusion
The Customer Churn & Retention Analytics project demonstrates an end-to-end approach to transforming messy customer data into actionable business insights.
The solution combines Python data cleaning and analysis with a Power BI dashboard to provide visibility into churn, its drivers, and the revenue it puts at risk.
The analysis identified month-to-month customers in their first year as the primary high-risk segment, with price and competitor offers as the main reasons for leaving. The retention offer scenario shows that a modest save rate of about 15% is enough to break even, making a controlled A/B test a sensible next step.
Overall, the project demonstrates how data analytics can support evidence-based retention decisions.
From raw customer data to actionable retention decisions.
Author
❤️ Pranav Krishna R V ❤️
MBA | Business Analytics / Business Analyst Portfolio
GitHub: pranav-rv

