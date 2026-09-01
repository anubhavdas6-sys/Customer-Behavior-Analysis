# Customer-Behavior-Analysis
Customer Behavior AnalysisThis project processes and analyzes a dataset of 3,900 customer purchases to evaluate shopping behavior, customer demographics, shipping preferences, subscription impact, and product ratings.  

Technical Stack & Architecture                     

[ Data Pipeline Architecture ]



 ┌─────────────────┐       ┌────────────────────┐       ┌──────────────────┐
 │ Raw Dataset     │ ────> │ Python / Notebook  │ ────> │ Relational DB    │
 │ (3,900 records) │       │ Cleaning & Engineering │       │ SQL Analysis     │
 └─────────────────┘       └────────────────────┘       └──────────────────┘
                                                                 │
                                                                 ▼
                                                        ┌──────────────────┐
                                                        │ Power BI         │
                                                        │ Visual Dashboard │
                                                        └──────────────────┘

                                                        

                                                        
Programming Language: Python (v3.9+)  Libraries: pandas, sqlalchemy, psycopg2-binary (PostgreSQL), pymysql (MySQL), pyodbc (MS SQL Server)  Databases Supported: PostgreSQL, MySQL, MS SQL Server 

Visualization/BI: Power BI Report Template (.pbix)  

Data Pipeline & PreprocessingThe Python notebook transforms raw customer transactions through a 5-step processing pipeline: 




┌──────────────────────┐
│  1. Ingest Data      │ ──> Load 'customer_shopping_behavior.csv'
└──────────┬───────────┘
           ▼

           
┌──────────────────────┐
│  2. Clean & Impute   │ ──> Impute 37 missing ratings with Category Medians
└──────────┬───────────┘
           ▼
           
           
┌──────────────────────┐
│  3. Standardize      │ ──> Convert headers to snake_case & rename spend metrics
└──────────┬───────────┘
           ▼

           
┌──────────────────────┐
│  4. Feature Engineering │ ─> Create 'age_group', 'purchase_frequency_days', drop redundant columns
└──────────┬───────────┘
           ▼

           
┌──────────────────────┐
│  5. DB Export        │ ──> Load cleaned data to SQL via SQLAlchemy
└──────────────────────┘



Data Insights & MetricsCustomer Lifecycle SegmentsCustomers are categorized based on purchase history to target marketing retention strategies:  Purchase Frequency

─────────────────────────────────────────────────────────────────────────────
[ New ]              ■■■ (1 Purchase)
[ Returning ]        ■■■■■■■■■■■■■■■ (2–10 Purchases)
[ Loyal ]            ■■■■■■■■■■■■■■■■■■■■■■■■ (>10 Purchases)
─────────────────────────────────────────────────────────────────────────────


Key Business Analytics (SQL Focus)Query / MetricAnalysis GoalPrimary Method
Q1. Gender RevenueEvaluate revenue share by gender  Grouped aggregation  
Q2. High-SpendersIdentify discount users spending above dataset average  Subquery filtering  
Q3. Top ProductsDiscover top 5 items by review rating  Ordered ranking  
Q4. Shipping ComparisonCompare Standard vs. Express spend patterns  Average comparison  
Q5. Subscription ImpactContrast spend/volume of subscribers vs. non-subscribers  Key segment aggregation  
Q6. Discount RatesMap percentage of discounted purchases by product type  Percentage calculation  
Q7. Lifecycle GroupsClassify into New, Returning, and Loyal tiers  Conditional logic (CASE)  
Q8. Category LeadersList top 3 items per category  ROW_NUMBER() OVER PARTITION  
Q9. Repeat ConversionMeasure subscription adoption among buyers with >5 purchases  Target cohort tracking
Q10. Age RevenueDistribution of overall spend across age groups 
Demographic aggregation 

Setup & Usage Instructions1. Execute Data PipelineRun the processing notebook to transform raw data and populate target database tables[cite:
:Bashjupyter notebook 

Customer_Behavior_Analysis.ipynb 
Execute Analytics QueriesConnect your SQL client (e.g., pgAdmin, MySQL Workbench) to the populated database to execute analytical queries.  
Open BI DashboardLaunch the included Power BI .pbix file to view interactive visuals, revenue distributions, and dynamic segment charts. 
