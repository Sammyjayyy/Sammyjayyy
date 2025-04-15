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
