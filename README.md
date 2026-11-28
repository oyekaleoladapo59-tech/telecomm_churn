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

# Creating a Tenure Group column

To group customers according to the number of months they have stayed with the company using the SQL CASE statement.

1. Creating a New Column

An additional column named TenureGroup was added to the dataset to store the customer tenure categories.

<img width="436" height="75" alt="{2F1CCFFF-F1E8-4B80-98A6-C540D5332E7A}" src="https://github.com/user-attachments/assets/6a3da4b3-a8a1-42fa-b44e-34ef51b719b2" />

2. Categorising Customers Using CASE

The CASE statement was used to classify customers into three groups based on their tenure in months.

<img width="511" height="95" alt="{4C83EB31-5100-485C-9ABB-99900A049391}" src="https://github.com/user-attachments/assets/264b22d5-6df3-4b54-a96b-0ef77f566713" />

3. Verifying the Results

The following query was used to confirm that customers were correctly assigned to their respective tenure groups.

<img width="591" height="175" alt="{307A630F-F304-42E1-ADC0-1ECE27623BD8}" src="https://github.com/user-attachments/assets/e6960c95-6176-4d30-b647-ad1f6cf8182b" />

# Renaming Contract Values

To simplify and standardise the categories in the Contract column by replacing the existing contract values with shorter and more descriptive labels.

1. Checking Existing Contract Values

The DISTINCT command was used to identify the unique contract categories in the dataset.

<img width="511" height="177" alt="{B2DA005F-293B-4BF8-B158-01D65CB93AEA}" src="https://github.com/user-attachments/assets/68bfdd96-6a3f-447b-886d-f0039d584bae" />

2. Renaming Contract Values

The SQL CASE statement was used to replace the existing contract values with the new labels.

<img width="570" height="105" alt="{2B394ED9-7617-400E-B542-51BD043480DC}" src="https://github.com/user-attachments/assets/97451cd1-3749-4d82-b0d7-18245445f94b" />

3. Verifying the Changes

The following query was used to confirm that the contract values were successfully renamed.

<img width="525" height="145" alt="{F91B7114-3225-4AC0-8E62-40A0D0835955}" src="https://github.com/user-attachments/assets/fd1903d5-22c7-4a14-afa4-6a4a061d6863" />

## Exploratory and Descriptive Analysis

After completing the data cleaning process, Exploratory Data Analysis (EDA) was conducted using SQL to examine the cleaned Telco Customer Churn dataset. The purpose was to identify patterns, understand customer behaviour and determine factors associated with customer churn.

# Overall Customer Churn Analysis

The first stage of the exploratory data analysis focused on understanding the overall customer churn situation. The objective was to determine the total number of customers, identify how many customers discontinued the service, calculate the number of retained customers and determine the overall churn rate.

1. Total Number of Customers

The following SQL query was used to determine the total number of customers in the dataset.

<img width="413" height="137" alt="{35A0794E-878B-4C7A-80A2-5041917E86BB}" src="https://github.com/user-attachments/assets/b5e5cf39-d28f-40a2-9ded-a42bf693775c" />

2. Number of Customers Who Churned

This query was used to identify and count customers who discontinued the company's services.

<img width="463" height="153" alt="{9B4AFA96-0F23-46A5-BBF5-58E15E2A7A9B}" src="https://github.com/user-attachments/assets/73fc4540-d253-4429-a949-fa2685cdcc82" />

3. Number of Retained Customers

This query was used to determine the number of customers who remained with the company.

<img width="483" height="173" alt="{7754008D-CA99-4D74-9B94-07C9716B5C40}" src="https://github.com/user-attachments/assets/adf39e26-a867-4b33-9083-7eb4d5aff9e4" />

4. Overall Customer Churn Rate

The churn rate was calculated to determine the percentage of customers who discontinued the company's services.

<img width="629" height="164" alt="{AF841CBE-3B8A-4B0D-9F29-C7B4BC6121D6}" src="https://github.com/user-attachments/assets/51d9ae05-6e87-4d76-b24b-1ca1e165557f" />

# Demographic Analysis

The demographic analysis was conducted to examine customer churn across different demographic categories. The objective was to understand how gender, senior citizen status, partner status and dependent status relate to customer churn.

SQL queries were used to group customers according to their demographic characteristics and churn status, making it easier to compare the number of customers who discontinued the company's services with those who remained.

1. Customer Churn by Gender

To examine the distribution of customer churn between male and female customers.

<img width="489" height="189" alt="{C19DBB9D-6167-4ACF-AA27-CEF3EC3C38A1}" src="https://github.com/user-attachments/assets/7724ec12-8388-4829-81fd-1b160531a5a2" />

2. Customer Churn by Senior Citizen Status

To investigate the relationship between senior citizen status and customer churn.

<img width="499" height="198" alt="{993D364C-E09C-433C-B581-39590B2E2B0D}" src="https://github.com/user-attachments/assets/46b68103-d8ea-4919-a9a5-cad720053d6e" />

3. Customer Churn by Partner Status

To examine whether customer churn differs between customers who have partners and those who do not.

<img width="527" height="212" alt="{0360E3C6-77B4-4325-B1F5-84580CFE629C}" src="https://github.com/user-attachments/assets/af7df3cd-3b6d-4f4f-8f59-c609b4c6748e" />

4. Customer Churn by Dependents

 To investigate whether customer churn patterns differ between customers with dependents and those without dependents.

 <img width="504" height="199" alt="{AD083A27-6F9F-45F5-831B-F3387FA5F08D}" src="https://github.com/user-attachments/assets/baa5b1ef-aef5-43c9-a777-008cb5119dc3" />

# Customer Account Analysis

The customer account analysis was conducted to investigate the relationship between customer account characteristics and churn behaviour. The objective was to identify how tenure group, contract type, paperless billing and payment methods relate to customer retention.

SQL queries were used to group customers according to their account characteristics and churn status, allowing comparisons between customers who discontinued the company's services and those who remained.

1. Customer Churn by Tenure Group

To investigate whether the length of time customers have stayed with the company influences their likelihood of discontinuing the service.

 <img width="502" height="240" alt="{03D73C82-72EB-499B-9898-0E0E1E98ED76}" src="https://github.com/user-attachments/assets/1c1268f8-e7b5-4b47-92fe-ac280b2c604a" />

2. Customer Churn by Contract Type

To examine how different contract types relate to customer churn.

<img width="490" height="233" alt="{52230664-83AE-4D9B-B836-847EE5DEA9DA}" src="https://github.com/user-attachments/assets/fe4a753f-24b8-446d-89e3-c2d54ad2a4a4" />

3. Customer Churn by Paperless Billing

To investigate whether customers who use paperless billing demonstrate different churn patterns compared to those who do not.

<img width="463" height="200" alt="{97949BE7-DE9D-4971-9F56-A0EB788FF945}" src="https://github.com/user-attachments/assets/cca690d0-0e98-45c1-b9b1-be29f66891a0" />

4. Customer Churn by Payment Method

To examine the relationship between customers' payment methods and their likelihood of discontinuing the company's services.

<img width="441" height="273" alt="{69411750-A6ED-4CB6-A796-EBB7298C6469}" src="https://github.com/user-attachments/assets/9e32cc63-a10b-4d4d-92e2-514252fdae4c" />

# Services Analysis

The services analysis was conducted to examine how the different services subscribed to by customers relate to their churn behaviour. The objective was to identify whether the type of services customers use influences their likelihood of discontinuing the company's services.

SQL queries were used to group customers according to their service subscriptions and churn status, allowing comparisons between customers who discontinued the services and those who remained.

1. Customer Churn by Phone Service

To investigate whether subscribing to phone services relates to customer churn behaviour.

<img width="474" height="198" alt="{15ECBBEB-2267-4B8B-BEE7-8C5996D2BF2B}" src="https://github.com/user-attachments/assets/cf9ac475-e9a3-4ae7-b468-d00a6257278f" />

2. Customer Churn by Internet Service

To examine whether the type of internet service subscribed to by customers relates to customer churn.

<img width="514" height="227" alt="{34A44E83-53A7-4A81-987D-FF9FB12B3486}" src="https://github.com/user-attachments/assets/e8749bcf-d047-4d40-8cd3-75c128d363ce" />

3. Customer Churn by Online Security

To investigate whether subscribing to online security services relates to customer churn behaviour.

<img width="537" height="212" alt="{24C7C164-B5E8-4F51-8E19-C0EFCCDF7F68}" src="https://github.com/user-attachments/assets/ff8a68e4-eb07-4ece-a507-ee2ee5c41823" />

4. Customer Churn by Tech Support

To examine whether subscribing to technical support services relates to customer churn behaviour.

<img width="494" height="208" alt="{25A6340E-E072-4F1D-8FE1-8965D76B31E3}" src="https://github.com/user-attachments/assets/814ff1c8-1a37-4dc9-a781-41f4f4b462b1" />

5. Customer Churn by Streaming TV

To investigate whether subscribing to Streaming TV services relates to customer churn behaviour.

<img width="507" height="209" alt="{398603B2-3F7F-4DD1-8556-9136FF2B98B8}" src="https://github.com/user-attachments/assets/63b306c7-fc2c-4d45-ac0d-65856132f8a5" />

6. Customer Churn by Streaming Movies

To examine whether subscribing to Streaming Movies relates to customer churn behaviour.

<img width="501" height="209" alt="{E083E47C-0A79-4AA5-9E0E-58EF6E416F0D}" src="https://github.com/user-attachments/assets/15457162-c2cd-405b-afdd-bb857fe81979" />

# Average Monthly Charges Analysis

To compare the average monthly charges of customers who churned with those who remained with the telecommunications company.

<img width="541" height="211" alt="{398A203A-8A9C-4572-A00C-41950B40CE5E}" src="https://github.com/user-attachments/assets/a99eeed8-eeb1-468e-95c2-bcc05d5a2d10" />

