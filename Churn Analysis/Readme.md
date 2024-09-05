**Case Study: Analyzing Customer Churn in Power BI**
---


Summary of case study
---
This case study is for the purpose of applying skills developed through the Power Bi course offered by Data Camp using a real-world problem.

The Problem
---

The task is to solve customer churn for a Telecom provider called Databel where I will be using a fictitious churn dataset. I will be analyzing why customers are churning and the churn rate.

Defining churn
---

A good definition is the one from Investopedia: “The churn rate, also known as the rate of attrition or customer churn, is the rate at which customers stop doing business with an entity.”


Calculating churn
---

The simplified formula for churn is to divide customers lost by the total number of customers.

Churn rate = customers lost/total number of customers

Example:
Churn rate = 10/100 = 10%

There are multiple methods to calculate churn, and depending on the industry. A traditional e-commerce platform might consider a certain customer a churner if he or she hasn’t made a purchase in the last 12 months.

The data
---

Key Characteristics:

* One big table with 29 different columns with one row per customer.
* Snapshot of the database at a specific moment in time, meaning there is no time dimension.
* The dataset contains more than just dimensions. Here is a view of the [metadata](https://assets.datacamp.com/production/repositories/5993/datasets/c55ad82061b13bc07f6516e51cba9883a90bfa27/Metadata%20-%20Case%20Study_Analyzing%20Customer%20Churn%20in%20Power%20BI.pdf)

Data check
---

The first step in any analysis is doing a data check. I will create two measures to check if the count of customer ids is equal to the count of unique customer ids. This check is particularly important to prevent double-count costs later incase of duplicates.

 Number of Customers = COUNT('Databel - Data'[Customer ID])
 
 Number of unique customers = DISTINCTCOUNT('Databel - Data'[Customer ID])


![image](https://user-images.githubusercontent.com/121925698/217404152-1d7a887e-9ea4-4471-8c1d-509843cb50fe.png)

Both values are the same.

Calculating Churn
---

Before getting further into the analysis, there is a churn label column that indicates “Yes” (if customer has churned) or “No” (If customer has not churned.) Because working with this column is difficult, it is best to convert it to a binomial column (1/0) that indicates whether or not the client churned.

_Creating a measure for the churned customers using a conditional IF expression based on the Churn Label_

Churned = IF('Databel - Data'[Churn Label]="Yes", 1, 0)
 
_Creating a measure to calculate the churn rate_

Churn Rate = [Churned customers]/[Number of Customers]
 
The total churn rate for “Databel” is **26.86% **

Investigating Churn reasons
---

Next, I will investigate the different reasons why customers churned.

The top three reasons are:

* Competitors made better offers
* Competitors had better devices
* Attitude of support person

![image](https://user-images.githubusercontent.com/121925698/217405866-6990c601-dd15-4acd-a77e-15e09d6e1ec4.png)

Customer Churn Reasons

Digging deeper into churn categories
---

Churn Reasons are grouped together in the Churn Category column. The “Extra data charges”, “Price too high” and other price related reasons are grouped together in the “Price” category. I will be displaying all churn categories in one visualization.

![image](https://user-images.githubusercontent.com/121925698/217405953-65240c7b-20a0-43b1-b802-1deac4cd4176.png)

The largest proportion of churned customers churning is related to the competitor category.

Using Maps
---

Databel wants to know if the aggressive promotions launched by competitors in different states has had an impact on their customers. The task is to create a map that will allow me to look at the churn rate by state.

![image](https://user-images.githubusercontent.com/121925698/217406011-8a941386-acfc-49cb-be92-03fdaa446973.png)

Insights discovered so far
---

* The Churn rate is for Databel is on average 27%
* 45% of the reasons why customers churn is related to competitors
* The Churn rate in California is abnormally high

The next stage is to analyze more columns, starting with the demographics of Databel.

Analyzing Demographics
---

The IF() method will be used to create a column with three age demography categories:

* “Senior,”
* “Under 30,”
* and “Other.”

Demographics = IF('Databel - Data'[Under 30] = "Yes", "Under 30", IF('Databel - Data'[Senior] = "Yes", "Senior", "Other"))

![image](https://user-images.githubusercontent.com/121925698/217406133-3c0f2f5b-f194-4d22-93b3-c7c24fd6dd27.png)

The churn rate for senior citizens is higher than the average.

Analyzing Age groups
---

From the above visualization, the senior citizens churn more often. This suggests the need t have a more detailed look at the ages. Next, I will create combo chart visualizing the number of customers per bracket and their respective churn rates.

![image](https://user-images.githubusercontent.com/121925698/217406180-2072f87e-0c01-4433-9343-6dfc7d1fb628.png)

In general, the churn rate has an increasing trend through the age brackets. As the age increases the average churn rate for age brackets also increases.

Multiple field investigation
---

For this task, I will use the function SWITCH() which allows creation of a new column by assigning new results to the values in a column. We will group 3 different contract types into two for easy observation of yearly and monthly contracts. We will further analyze the churn rate based on gender.

Contract Category = SWITCH('Databel - Data'[Contract Type], "One Year", "Yearly", "Two Year", "Yearly", "Monthly")

![image](https://user-images.githubusercontent.com/121925698/217406233-cc9f9923-17ec-4dbc-abfc-21c4b514364e.png)

Monthly contract customers churn more than yearly contract customers and the larger churning gender is females.

Group Consumption and Unlimited Plan
---

Databel has a hypothesis that people who are not on an unlimited data plan are more likely to churn. The task is to investigate this theory and prove if its accurate or not. I will also create a new column Grouped Consumption that categorizes the average monthly GB download into the following groups to determine whether it’s related to the amount of mobile data (GB) used:

* Less than 5 GB.
* Between 5 and 10 GB.
* 10 or more GB.

![image](https://user-images.githubusercontent.com/121925698/217406281-463f1f89-3f5c-451b-b9e3-a82feacfaa33.png)

It appears that the hypothesis is incorrect and instead, customers who are on an unlimited plan are more likely to churn.

International Calls and Contract Types
---

Databel has a request to analyze the international activity of customers and its relationship to churn. They would like to know if paying for an international plan influences customer loyalty. This will also help us find out if customers without international plans are making international calls and vice versa.

The findings were that customers who pay for an international plan but do not make international calls had a very high churn rate. The recommendation to Databel would be to contact customers who have an international plan but have not made any international calls and suggest that they downgrade their plan.

*Contract Type*

![image](https://user-images.githubusercontent.com/121925698/217406398-05972970-8e30-4377-a8c9-b0a78143c30f.png)

It seems the churn rate decreases over time.

Summary Overview
---

![image](https://user-images.githubusercontent.com/121925698/217406456-02adb9b4-9fe4-4716-ad3e-3754ff2d4f03.png)

* The Churn rate is for Databel is on average 27%
* 45% of the reasons why customers churn is related to competitors
* The Churn rate in California is abnormally high and this is due to campaigns launched by competitors inthe region
* There is a higher churn rate from senior citizens
* There is a higher churn rate from individual who have an international plan but have not made any international calls
* Customers with a monthly contract type have a higher churn rate

The next phase would be to identify reasons for the churn rates in the different categories and recommend solutions for Databel.
