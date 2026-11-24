# Brazilian E-Commerce Data Preparation Using MYSQL

Project Overview
This project focuses on cleaning, standardising, transforming, and preparing the Brazilian E-Commerce Public Dataset by Olist for Exploratory Data Analysis (EDA).

Using MySQL, I performed data quality checks, handled inconsistent text values, removed duplicate records, transformed date columns, and created staging tables to ensure the dataset was structured and reliable for further analysis.

The project also explores SQL performance optimisation through indexing and automation using scheduled MySQL events to refresh the cleaned staging tables.

Project Objectives
Clean and standardise inconsistent data across the dataset.
Identify and handle missing, blank, and invalid records.
Detect and remove duplicate records using SQL window functions.
Create staging tables to preserve the original dataset.
Transform date columns into appropriate DATETIME formats.
Improve query performance through indexing.
Automate staging table refreshes using MySQL events.

1. Data Cleaning and Standardisation

The first stage of the project involved improving data quality and consistency across the eight tables in the Olist dataset.

The objective was to standardise inconsistent text values, remove unwanted spaces and characters, correct encoding issues, and prepare the data for subsequent transformation and analysis.

1.1 Customer Table

Table: olist_customers

Operations performed:

Used TRIM() to remove unwanted leading and trailing spaces from customer city and state values.
Used UPPER() and CONCAT() to standardise the first letter of customer cities.
Converted customer state abbreviations to uppercase for consistency.
1.2 Geolocation Table

Table: olist_geolocation

This table contained inconsistent city names, accented characters, encoding issues, and unwanted special characters.

Operations performed:

Used REGEXP_REPLACE() to standardise accented characters.
Used REPLACE() to remove or correct unwanted special characters.
Corrected specific city names affected by encoding inconsistencies.
Standardised city names by capitalising their first letters.
1.3 Order Items Table

Table: olist_order_items

Applied TRIM() to order_id, product_id, and seller_id to remove unwanted spaces.
1.4 Order Payments Table

Table: olist_order_payments

Applied TRIM() to order_id and payment_type to ensure consistent text values.
1.5 Orders Table

Table: olist_orders

Standardised order_status by capitalising its first letter.
Removed unwanted spaces from order_id and customer_id.
1.6 Products Table

Table: olist_products

Removed unwanted spaces from product_id.
Standardised product category names by capitalising their first letters.
1.7 Sellers Table

Table: olist_sellers

Standardised seller city names.
Removed unwanted spaces from seller_id.
1.8 Product Category Translation Table

Table: product_category_name_translation

Renamed the imported column ï»¿product_category_name to product_category_name to remove the unwanted BOM encoding characters.
Standardised both Portuguese and English product category names.
SQL Techniques Used
SQL Function	Purpose
TRIM()	Removes unwanted spaces
UPPER()	Converts text to uppercase
CONCAT()	Combines text values
LEFT()	Extracts the first character
SUBSTRING()	Extracts the remaining characters
REPLACE()	Replaces unwanted characters
REGEXP_REPLACE()	Replaces characters using regular expressions
ALTER TABLE	Renames an incorrectly imported column

Outcome: Improved consistency across the eight tables, corrected several text-quality issues, and prepared the dataset for duplicate removal and further cleaning.
