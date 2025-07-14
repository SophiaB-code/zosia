# 📊 IT Job Market Data Analysis (SQL Project)

## 📁 Introduction  
This project focuses on analyzing a database related to the IT job market - including salaries, required skills, and job types. 
The analysis was performed using SQL in PostgreSQL, with all code and queries organized in the [project_sql folder](/project_sql) folder.

## 🧠 Background  
This project is based on a [YouTube course by Luke Barousse](https://www.youtube.com/watch?v=7mz73uXD9DA&t=822s), which provided a great foundation for practicing real-world data analysis using SQL. My goal was to deepen my knowledge of SQL and gain hands-on experience by exploring a dataset related to tech job offers.  

It was a great opportunity to improve my skills in querying, data cleaning, and insight generation - all within the context of the IT job market.

### The questions answered through the SQL queries were:
1. What are the top-paying data analyst jobs?
2. What skills are required for these top-paying jobs?
3. What skills are most in demand for data anlysts?
4. What skills are associated with higher salaries?
5. Which are the most optimal skills to learn?

## 🛠️ Tools I Used  
- **SQL**: The core tool used for querying and analyzing the data.
I applied various techniques such as filtering, joining tables, using subqueries, creating CTEs and aggregations to extract meaningful insights from the dataset.
- **PostgreSQL**: I used it to import and store the dataset, write SQL queries, and perform all data operations.
  Its support for advanced SQL features like CTEs, window functions, and indexing made it ideal for this type of analysis.
- **Visual Studio Code**: Served as my main development environment. With the help of SQL extensions and PostgreSQL integration, it allowed me to write, run, and manage SQL scripts efficiently.
- **Git & GitHub**: Essential for version control to track changes, manage code versions, and maintain a clean development workflow.


## 📈 The Analysis  

### 1. Top Paying Data Analyst Jobs

This query filters job postings for **Data Analyst** positions based on **average yearly salary** and **location**, with a specific focus on **remote jobs**. The goal is to identify the highest-paying options available on the market.

By narrowing the results to remote jobs, this analysis highlights top-paying roles that offer flexibility and are accessible regardless of geographic location. It provides valuable insight for job seekers who are looking for well-compensated, remote-friendly data analyst positions.
```sql
SELECT 
    job_id,
    cd.name AS company_name,
    job_title,
    job_location,
    job_schedule_type,
    salary_year_avg,
    job_posted_date
  
FROM
  job_postings_fact jpf
LEFT JOIN company_dim cd ON jpf.company_id = cd.company_id
WHERE jpf.salary_year_avg IS NOT NULL 
  AND jpf.salary_year_avg > 0
  AND jpf.job_title IS NOT NULL
  AND jpf.job_location = 'Anywhere'
  AND jpf.job_title_short = 'Data Analyst'
ORDER BY jpf.salary_year_avg DESC 
LIMIT 10;
```


## 🎓 What I Learned  
Through this project, I improved my ability to:
- Write and optimize complex SQL queries (JOINs, CTEs, subqueries)  
- Analyze large datasets and extract key insights  
- Work efficiently in a PostgreSQL + VSCode setup  

## ✅ Conclusions  
The analysis revealed clear trends in IT job offers, such as:
- High demand for cloud and backend technologies  
- Significant salary differences by region and experience  
- The growing number of remote job opportunities  

This project showcases how SQL can be used to turn raw job market data into actionable insights.
