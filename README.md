# Telco-Customer-Churn-Dataset-Focused-Customer-Retention-Program
USING MySQL FOR ALL DATA CLEANING AND ANALYSIS, WHILE MICROSOFT EXCEL WILL BE USED EXCLUSIVELY FOR VISUALIZATION AND DASHBOARD PRESENTATION 

<img width="800" height="400" alt="{D36CFD3F-E1FB-4FD9-923B-D54EA62C1C7C}" src="https://github.com/user-attachments/assets/ea55d924-76e2-4142-9568-7111a9904c47" />

## INTRODUCTION

The Telco Customer Churn dataset contains information on 7,043 customers of a telecommunications company, covering 21 attributes relating to customer demographics, account information, subscribed services and billing details. These attributes include CustomerID, Gender, SeniorCitizen, Partner, Dependents, Tenure, PhoneService, MultipleLines, InternetService, OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport, StreamingTV, StreamingMovies, Contract, PaperlessBilling, PaymentMethod, MonthlyCharges, TotalCharges and Churn.

The dataset provides information about customers who have either discontinued or continued using the company's services. It offers an opportunity to examine customer behaviour, identify patterns associated with customer attrition and understand the factors that may influence customers' decisions to leave or remain with the company.

This project uses MySQL for data cleaning, transformation and analysis, while Microsoft Excel is used for data visualization through PivotTables, PivotCharts and an interactive dashboard. The ultimate goal is to generate meaningful insights and provide data-driven recommendations to support effective customer retention strategies.

## PROJECT OBJECTIVE

To analyse the Telco Customer Churn dataset using MySQL to identify patterns and factors associated with customers who are retained or tend to leave across different customer segments, account characteristics and subscribed services, using Churn as the target variable. The analysis also aims to generate actionable insights and recommend effective strategies for improving customer retention.

## DATASET SOURCE
The dataset used for this project is a CSV (Comma-Separated Values) file containing 7,043 rows and 21 columns. It provides customer-related information covering demographics, account details, subscribed services, billing information and churn status.

The dataset was obtained from Kaggle and downloaded from the following source:
https://www.kaggle.com/datasets/blastchar/telco-customer-churn

## TOOLS AND TECHNOLOGIES

MySQL Workbench: Used for database creation, data importation, data cleaning, data transformation and customer churn analysis using SQL.

Microsoft Excel: Used for creating PivotTables, PivotCharts and a one-page dashboard to visualize the results obtained from the SQL analysis.

GitHub: Used for project documentation, version control and hosting the project files.

## DATA CLEANING (SQL)

Data cleaning was performed using MySQL Workbench to improve the quality, consistency and reliability of the Telco Customer Churn dataset before conducting further analysis. The process involved identifying missing values, checking duplicate customer records, removing unnecessary spaces, correcting data types and transforming selected columns to improve data consistency and support meaningful analysis.

# Checking and Handling NULL/Blank Values

To identify missing values in the dataset and handle the 11 blank entries found in the TotalCharges column.

1.  Identifying Missing Values

The following SQL query was used to identify NULL and blank values in the TotalCharges column.

<img width="511" height="141" alt="{B8722666-4746-425B-B462-37DCC7FF91EA}" src="https://github.com/user-attachments/assets/68d5d090-1fc9-4bfd-bee0-83bc27773710" />

2. Handling Missing Values

The 11 blank values were replaced with 0.

<img width="593" height="94" alt="{418A2465-A54F-4C24-BE7C-EE349E337EB8}" src="https://github.com/user-attachments/assets/28e21804-5c9b-4848-b6ee-518b0ab69ad0" />

3. Verification

The following query was executed to confirm that no blank or NULL values remained.

<img width="503" height="174" alt="{FBBB97DE-7179-4E96-A3CE-F4641A95F3FE}" src="https://github.com/user-attachments/assets/76cc7179-e37c-4642-bb53-40365de7bc34" />

# Reason for the decision

I replaced the 11 blank values with zero because the affected customers had a tenure of zero months. This indicates that they had not yet spent any time as active customers and therefore had not accumulated any total charges.

I considered deleting the records, but that would have resulted in losing useful customer information. Replacing the blanks with zero preserved the records while ensuring that TotalCharges contained valid numerical values for further analysis.


# CHECKING FOR DUPLICATES

To identify duplicate customer records using the customerID column and ensure that each customer has a unique identification number.

<img width="493" height="198" alt="{61AAB341-3020-43B5-BA05-CF9238520709}" src="https://github.com/user-attachments/assets/8bdcd7df-6cc7-4f2e-a507-6ee866c506fa" />

Observation:
The query returned no records, indicating that there are no duplicate values in the customerID column.

# TRIMMING EXTRA SPACES AND FIXING DATA TYPES

1. TRIM EXTRA SPACES: The TRIM() function was used to remove unnecessary leading and trailing spaces from the TotalCharges column.

<img width="288" height="56" alt="{D3AD7F06-11AA-434F-93DA-8BD00F362A1D}" src="https://github.com/user-attachments/assets/deaf9c5b-2d74-4309-86b2-a4887a9bf205" />

2. Handling Missing and Blank Values

The missing and blank values in TotalCharges were replaced with 0. This was done to ensure that the column could be converted into a numerical data type.

<img width="354" height="63" alt="{47AFC2B2-1137-4908-85F0-3CF11865418E}" src="https://github.com/user-attachments/assets/8ad9a75c-1988-40b6-b9d7-778ba2deb2ab" />

3. Converting the Data Type

The TotalCharges column was converted from TEXT to DECIMAL(10,2) to support numerical calculations and analysis.

<img width="360" height="62" alt="{6652C9E0-346B-4BF0-86DD-59F4A03BB7A2}" src="https://github.com/user-attachments/assets/b21aa505-ec73-4ad4-81aa-767996167a4a" />

4. Verification and confirmation of totalcharges if for sure it has converted to decimal

<img width="528" height="227" alt="{A194323F-BCFA-4439-9E8A-E284D98955A5}" src="https://github.com/user-attachments/assets/59736251-be27-4131-a29a-6379ea85640a" />


# Converting SeniorCitizen Values (0/1 to No/Yes)

To convert the SeniorCitizen column from numerical values (0 and 1) into more readable categorical values (No and Yes).

1. Checking Existing Values

The DISTINCT command was used to identify the unique values in the SeniorCitizen column.

<img width="448" height="185" alt="{D2FE60F7-F99B-4369-B950-E142B6B1A240}" src="https://github.com/user-attachments/assets/be967ed8-d10c-4115-b4fe-16fb4f8101f0" />

2. Changing the Column Data Type

The column data type was changed to VARCHAR(3) to accommodate the text values No and Yes.

<img width="321" height="61" alt="{18BE17C0-E638-423E-871D-515C497D5048}" src="https://github.com/user-attachments/assets/47ab1cfa-44ad-4709-bbcb-d14d904b6518" />

3. Converting the Values

The UPDATE statement and CASE expression were used to replace 0 with No and 1 with Yes.

<img width="601" height="80" alt="{54E98920-43F9-49C4-8E81-E6FA957CE057}" src="https://github.com/user-attachments/assets/fe3d000e-c594-44fe-a181-c29a8a91075d" />

4. Verification

The following query was used to confirm that the conversion was successful.

<img width="477" height="157" alt="{792036E4-D094-482E-BEFD-0D7101DE947B}" src="https://github.com/user-attachments/assets/2ec3b82a-c88a-4456-b20a-40c42891cfd0" />




