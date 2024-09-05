# Churn Analysis Project

## Summary
This project aims to apply the skills developed through the Power BI course offered by DataCamp, utilizing real-world client data. It marks the first project in which we have been provided with actual client data.

## The Problem
In this project, a client, Atlas Labs, has the primary goal of monitoring key HR metrics on employees and understanding the factors that impact attrition (Employee attrition is the naturally occurring, voluntary departure of employees from a company).

## Project Approach
As we build the report, it's essential to understand the process we will follow in our report development in Power BI. The process is summarized below:

### Step 1: Building the Data Model and Analyzing the Data
- Requirements gathering
- Data Connections
- Data Transformation
- Building the Data Model
- Writing DAX Measures

### Step 2: Report Design
- Branding
- Defining the Report Layout
- Building the Report with Chart Visualizations

## The Dataset: Requirements Gathering, Data Connections, and Data Transformation
For this project, we will use the Kimball modeling approach as we model our data. The fact table stores information about employee yearly reviews. We will also work with multiple dimension tables to provide more context to the data. The final data model will follow a snowflake schema.

The first step involves opening an empty Power BI file and loading and preparing the dataset. All CSV files will be imported and loaded into Power BI. Ensuring the data is clean is crucial. Each table name should begin with either `Fact` or `Dim`, depending on the table type.

## Building the Data Model: Date Dimension and Relating Tables
In any Power BI report, it is recommended to have a dedicated date table for accurate date and time reporting. At this stage, we will also model our data, enabling us to connect six different tables.

Steps include:

- Creating a dedicated date table using DAX code.
- Connecting the `DimDate` table to `FactPerformanceRating` and `DimEmployee` tables. (Note: The last relationship will be inactive due to Power BI's limitation on multiple active relationships between the same tables.)
- Connecting the `DimEducationLevel` table to the `DimEmployee` table.
- Connecting columns in `FactPerformanceRating` to `DimSatisfactionLevel` and `DimRatingLevel`, ensuring the correct active connections.

## Exploring the Data
We will explore the data and produce high-level metrics to understand attrition at the company. The overview page will be created, and a table called `_Measures` will store all the measures used.

### Measures include:
- Total count of all employees.
- Count of active and inactive employees.
- Attrition rate based on active and inactive employees.

### Visualizations:
- Employee hiring trends over time, using a stacked column chart.
- Departmental analysis using clustered bar charts and treemaps.

## Key Insights So Far
- Atlas Labs has employed over 1,470 people.
- Atlas Labs currently employs over 1,200 people.
- The largest department is Technology.
- The attrition rate is 16%.

## Demographics: Age and Gender
To understand diversity and inclusion, we focus on employee age and gender. This includes creating visualizations for age distribution and analyzing the distribution across age bins and gender.

Further analysis covers marital status and ethnicity, along with average salary by demographic groups.

## Performance Tracking
The HR team wants to track employee performance based on yearly reviews. The report includes pages to track performance, visualize satisfaction metrics, and display individual review ratings.

## More Insights Uncovered
- The majority of employees are between 20-29 years old.
- Atlas Labs employs 2.7% more women than men.
- Employees who identify as non-binary make up 8.5% of total employees.
- White employees have the highest average salary.
- Frequent travelers have the highest attrition rate.

## Creating a Cohesive Report
The final step is preparing to deliver the report to key stakeholders at Atlas Labs, focusing on insights into attrition and factors affecting employee retention.

The final report is available as a Power BI file in this repository.
