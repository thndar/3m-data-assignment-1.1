# Video Game Sales Analysis

## Dataset

You will be working with the following dataset: [Video Game Sales](https://www.kaggle.com/datasets/gregorut/videogamesales?resource=download)

📦 **Dataset Download Instructions**
1. Download the dataset ZIP file from the above link.
2. After downloading: Unzip the file to access vgsales.csv. Note the full file path to vgsales.csv — you'll need it in the next step.

🔍 **Challenge: Load the Data into DuckDB**
Using DBeaver and your DuckDB connection, how would you load the vgsales.csv file into a table so you can begin querying it?

## Business Question
How can game developers and publishers optimize their strategy to maximize global sales by understanding the performance of different game genres, platforms, and publishers?

*To answer the above question, use the following SQL queries to explore the dataset and address the following questions:*

Which genres contribute the most to global sales?

SQL:
```
SELECT vgs.Genre, SUM(vgs.Global_Sales) AS total_sales  
FROM main.vgsales vgs
GROUP BY vgs.Genre
ORDER BY total_sales DESC;

```
Findings:
```

```
Which platforms generate the highest global sales?

SQL:
```
select Platform, sum(global_sales) from vgsales group by platform order by sum(global_sales) desc;

```
Findings:
```

```
Which publishers are the most successful in terms of global sales?

SQL:
```
select Publisher, sum(global_sales) from vgsales group by Publisher order by sum(global_sales) desc;
```
Findings:
```findings

```
How does success vary across regions (North America, Europe, Japan, Others)?

SQL:
```
select  
Round(sum(NA_Sales),2) as NA_Sales_Sum, 
Round(sum(EU_Sales),2) as EU_Sales_Sum, 
Round(sum(JP_Sales),2) as JP_Sales_Sum, 
Round(sum(Other_Sales),2) as Other_Sales_Sum 
from vgsales;

```
Findings:
```findings

```
What are the trends over time in game sales by genre and platform?

SQL:
```
select genre, platform, year, 
sum(NA_Sales) as NA_Sales_Sum, sum(EU_Sales) as EU_Sales_Sum, sum(JP_Sales) as JP_Sales_Sum, sum(Other_Sales) as Other_Sales_Sum , sum(Global_Sales) as Global_Sales_Sum 
from vgsales 
group by genre, platform, year
order by   genre, platform, yea

```
Findings:
```findings

```
Which platforms are most successful for specific genres?

SQL:
```
SELECT genre, platform, total_sales
FROM (
  SELECT 
    genre,
    platform,
    SUM(global_sales) AS total_sales,
    RANK() OVER (PARTITION BY genre ORDER BY SUM(global_sales) DESC) AS rnk
  FROM vgsales
  GROUP BY genre, platform
) AS ranked
WHERE rnk = 1
ORDER BY genre;

```
Findings:
```findings

```
## Deliverables:
- SQL Queries: Provide all the SQL queries you used to answer the business questions.
- Summary of Findings: For each question, summarise your key findings and recommendations based on your analysis.

## Submission

- Submit the GitHub URL of your assignment to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
