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
1. Average Spending Score By Gender
SELECT gender, AVG(spending_score) AS avg_spending
FROM customers
GROUP BY gender;
Explanation:
This query shows the average spending score for male and female customers.

Insight:
Female customers have a slightly higher average spending score than males. Marketing campaigns can be adjusted based on gender behavior.

2. Spending Score By Age Group
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
Explanation:
This query groups customers into age ranges and calculates the average spending score per group.

Insight:
The 18–25 age group has the highest average spending score, showing strong purchasing behavior. Adults (26–35) follow closely.

3. Spending Score By Age Group And Gender
 SELECT 
	CASE
		WHEN age BETWEEN 18 AND 25 THEN '18-25'
		WHEN age BETWEEN 26 AND 35 THEN '26-35'
		WHEN age BETWEEN 36 AND 45 THEN '36-45'
		ELSE '46+'
	END AS age_group,
	gender,
	COUNT(*) AS total_customers,
	AVG(spending_score) AS avg_spending
FROM customers
GROUP BY age_group, gender
ORDER BY age_group, gender
Explanation:
This query gives deeper insight by combining age group and gender to analyze how each subgroup behaves in terms of spending.

Insight:
Young adult males (18–25) and adult males (26–35) appear to have the highest spending scores. Female customers in general are more active spenders across all age ranges.
