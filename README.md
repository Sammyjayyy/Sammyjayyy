# SQL Customer Analysis

This project uses PostgreSQL to analyze a customer dataset from Kaggle. The goal is to understand customer behavior based on income, age, spending habits, and demographic attributes.

## Dataset
- Source: [Kaggle - Customer Dataset](https://www.kaggle.com/datasets/datascientistanna/customers-dataset)
- Columns: CustomerID, Gender, Age, Annual Income, Spending Score, profession, work experience and family
- Objectives
	•	Find out which gender spends more on average
	•	Analyze spending patterns by age, income, and profession
	•	Understand the relationship between family size, work experience, and spending
	•	Identify customer segments for targeted marketing campaigns

## Example Queries
```sql
SELECT gender, AVG(spending_score) AS avg_spending
FROM customers
GROUP BY gender;
SELECT 
	CASE
		WHEN age BETWEEN 18 AND 25 THEN '18-25'
		WHEN age BETWEEN 26 AND 35 THEN '26-25'
		WHEN age BETWEEN 36 AND 45 THEN '36-45'
		ELSE '46+'
	END AS age_group,
	COUNT(*) AS total_customers,
	AVG(spending_score) AS avg_spending
FROM customers
GROUP BY age_group
ORDER BY age_group
