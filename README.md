# ETL-Pipeline
Build ETL Pipelines for Various Scenarios

## Table of Contents

* [Overview](#overview)
* [Incremental Load](#incremental-load)
* [SCD Implementation](#scd-implementation)
* [F2F Pipeline](#f2f-pipeline)

## Overview

Design, Develop and Data validation of ETL pipeline with the help of Informatica Powercenter.\
Develop Pipeline for Complicated Scenarios such as Incremental Load, SCD and etc.

## Incremental Load

### Design and Development

•	Import source and target details to the Designer\
•	Design Mapping from source to target with necessary transformation \
•	For Incremental loading of Data, we need to use Mapping Variable\
•	The control variable can be timestamp or unique Id’s of a column\
•	With the help of setmaxvariable function, assign a value to the mapping variable\
•	In SQ, specify condition to load data if and only if load date is greater than the mapping variable (SQL overwrite)

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/6f4430a2-8640-4187-a3ce-08e878304b00)

### Data Validation

•	Check Run properties and session logs for the detailed report\
•	Validate source and target with Load date in the filter condition\
•	If source or target is Flat file, then validate the count or records with the help of grep command

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/5e4b7be7-dec7-4974-8ba8-7757a8ab668d)

## SCD Implementation

## SCD Type 1

### Design and Development

•	Import source and target details to the Designer\
•	Design Mapping from source to target with necessary transformation \
•	Creating SCD type 1 Implementation: Change of records history is not possible. Only Update and Insert can be performed\
•	Use Lookup Transformation to check record exist in the target. Then the source record can be Inserted/ Update. Surrogate key (Sequence generator) is not necessary, as only unique record of the employees is present.

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/81739896-49f0-42ac-b575-a236df3fa424)

### Data Validation

•	Check Run properties and session logs for the detailed report\
•	Validate source and target with necessary SQL Queries\
•	Use Update_date columns to filter records and validate data

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/8fe271d7-1bc3-4c24-937f-7e2ee6fae864)

## SCD Type 2

### Design and Development

•	Import source and target details to the Designer\
•	Design Mapping from source to target with necessary transformation \
•	Creating SCD type 2 Implementation: This preserves the changes made to the data. History maintenance is achieved with this type of Design.\
•	Use Lookup Transformation to check record exist in the target. Then the source record can be Inserted/ Update and Expire. Surrogate key (Sequence generator) is used to update records.

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/2e9bdeaf-92d4-4815-be39-5b9ade9f3cda)

### Data Validation

•	Check Run properties and session logs for the detailed report
•	Validate source and target with necessary SQL Queries
•	Use Active Flag to filter Active records and validate source and Target

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/a112f043-54f6-405f-ace9-d05cdbef7673)

## SCD Type 3

### Design and Development

•	Import source and target details to the Designer \
•	Design Mapping from source to target with necessary transformation \
•	Creating SCD type 3 Implementation: This provides partial history maintenance \
•	Use Lookup Transformation to check record exist in the target. Then the source record can be Inserted/ Update. Surrogate key (Sequence generator) is not necessary, as only unique record of the employees is present.

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/4939028c-5d1c-4f79-bde1-db5879fc4a1e)

### Data Validation

•	Check Run properties and session logs for the detailed report\
•	Validate source and target with necessary SQL Queries\
•	Use Previous / current columns and Update_date columns to filter records and validate data

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/a1d47e39-770a-48a4-bb3f-faca0209075b)

## F2F Pipeline

Flat file : Simple data sources, where data is stored in text format.
Types of Flat files: 
  1.	Delimited flat File: Data is separated with delimiter (ex: CSV)
  2.	Fixed width Flat File: Where fields are defined on fixed width

### Design and Development

•	Import source and target details to the Designer (Both are Flat files)\
•	Design Mapping from source to target with necessary transformation \
•	Joiner Transformation used to get data from Multiple sources \
•	Sorter transformation is used to sort the data and distinct properties defined to get unique records in the target.

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/f12b7ffc-9f29-4ccc-8f54-3705f6e2af85)

### Data Validation

Check Run properties and session logs for the detailed report\
Validate source and target with Unix Commands

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/db0ae5bb-8f11-4373-a650-86f08349a415)

Positive Scenarios: 
1.	Check Record counts in Source and Target
2.	Check for Duplicates in Target
3.	Check Transformation logic applied in Target
4.	Use Diff Command to check for truncation of Data

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/d95560fb-b02b-4ab5-a8e4-f7ae2de9e76f)

Negative Scenarios
1.	Check for Different Delimiter than specified in SQ
2.	Change Datatype in the column entries
3.	Error Handling Mechanism (Ex:  if the file is absent)

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/f6875222-d64d-4d62-944a-da0a9f759cd3)



















