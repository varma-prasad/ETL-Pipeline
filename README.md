# ETL-Pipeline
Build ETL Pipelines for Various Scenarios

## Table of Contents

* [Overview](#overview)
* [Incremental Load](#incremental-load)
* [SCD Implementation](#scd-implementation)
* [F2F Pipeline](#f2f-pipeline)
* [ETL Pipeline Project](#etl-pipeline-project)
* [About Author](#authors)

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

## ETL Pipeline Project

### Source to Target Mapping Sheet and Rules

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/1ba34c06-ccfe-4b70-8636-c3808a6b4ebf)

### Design and Development

•	Import source and target details to the Designer\
•	Design Mapping from source to target with necessary transformation \
•	Use Substr and instr functions to trim names to get first name and last name to load in the target table\
•	Use Joiner transformation to join to two tables with required join type to get the data\
•	Lookup transformation to get data from the lookup table\
•	Filter transformation to limit the entry of data into target table\
•	Router transformation to route the data according to city

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/cc18adbd-0ed1-4675-86a0-2f0d4052e1de)
![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/98bba9f3-93d3-4490-85fb-321385ae31ca)
![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/38650d67-8dd5-4ddb-b14b-7f01a654c226)

### Data Validation

•	Check Run properties and session logs for the detailed report\
•	Check Count in Source and Target tables\
•	Check all the transformation logic are fulfilled such as (First/Last name, Total Sales Field, Null Cities Replaced, Product Price < 2000 are not entered)\
•	Check the rules of Data Loading are adhered

![image](https://github.com/varma-prasad/ETL-Pipeline/assets/108605375/d1eaf98b-2bfc-4704-a5d3-4cc2505810c0)

----

## 🛠 Tools used
![](https://img.shields.io/badge/Informatica_Powercenter-v10.2.0-purple)
![](https://img.shields.io/badge/Oracle_Database_21c-v21.1.0-blue)
![](https://img.shields.io/badge/Linux-v21.3-green)

## Authors

- [Varma Prasad S](https://github.com/varma-prasad)

## 🛠 Skills
SQL, ETL, Python, Power BI...

## 🔗 Links

[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/varma-prasad-s/)


















