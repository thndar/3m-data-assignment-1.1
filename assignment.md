# Assignment

## Instructions

Paste the answer to each question in the answer code section below each question.

### Question 1

Construct an ERD in DBML for a social media company whose database includes information about users, their followers, and the posts that they make. Users can follow multiple users and create multiple posts.

Each entity has the following attributes:

- User: id, username, email, created_at
- Post: id, title, body, user_id, status, created_at
- Follows: following_user_id, followed_user_id, created_at

Answer:

```
Table User {
  id int [pk, increment]
  username varchar
  email varchar
  created_at datetime
}

Table Post {
  id int [pk, increment]
  title varchar
  body text
  user_id int [ref: > User.id]
  status varchar
  created_at datetime
}

Table Follows {
  following_user_id int [ref: > User.id]
  followed_user_id int [ref: > User.id]
  created_at datetime
}

Ref: User.id < Post.user_id        // A user can have many posts
Ref: User.id < Follows.following_user_id  // A user can follow others
Ref: User.id < Follows.followed_user_id   // A user can be followed by others


```
### Question 2

Using the data provided in lession 1.3 ( https://github.com/su-ntu-ctp/5m-data-1.3-sql-basic-ddl/tree/solutions/data ), write the SQL statement to alter the teachers table in the lesson schema to add a new column subject of type VARCHAR.

Answer:

```
ALTER TABLE lesson.teachers ADD COLUMN subject_of_type VARCHAR;

```

### Question 3

Using the data provided in lession 1.3 ( https://github.com/su-ntu-ctp/5m-data-1.3-sql-basic-ddl/tree/solutions/data ), write the SQL statement to update the `email` of the teacher with the name 'John Doe' to 'john.doe@school.com' in the teachers table of the `lesson` schema.

Answer:

```
UPDATE lesson1.teachers
SET email = 'john.doe@school.com'
WHERE id = 1;

```
### Question 4

Using the data provided in lesson 1.4 ( https://github.com/su-ntu-ctp/5m-data-1.4-sql-basic-dml/tree/main/db ), categorize flats into price ranges and count how many flats fall into each category:

- Under $400,000: 'Budget'
- $400,000 to $700,000: 'Mid-Range'
- Above $700,000: 'Premium'
  Show the counts in descending order.

```
SELECT rfp.resale_price,
CASE 
    WHEN rfp.resale_price < 400000 THEN 'Budget' 
    WHEN rfp.resale_price BETWEEN 400000 AND 700000 THEN 'Mid-Range' 
    WHEN rfp.resale_price > 700000 THEN 'Premium'
    ELSE 'Low' 
  END AS price_level,
  COUNT(rfp.flat_type) AS flat_type_count
FROM resale_flat_prices_2017 rfp
GROUP BY rfp.resale_price;

```

### Question 5

Using the data provided in lesson 1.4 ( https://github.com/su-ntu-ctp/5m-data-1.4-sql-basic-dml/tree/main/db ),select the minimum and maximum price of flats sold in each town during the first quarter of 2017 (January to March).

```
SELECT rfp.town, MIN(rfp.resale_price), MAX(rfp.resale_price)
FROM resale_flat_prices_2017 rfp
WHERE rfp.month BETWEEN '2017-01' AND '2017-03'
GROUP BY rfp.town;

```
SELECT 
  rfp.town, 
  rfp.month, 
  MIN(rfp.resale_price) AS min_price, 
  MAX(rfp.resale_price) AS max_price
FROM resale_flat_prices_2017 rfp
WHERE rfp.month BETWEEN '2017-01' AND '2017-03'
GROUP BY rfp.town, rfp.month
ORDER BY rfp.town, rfp.month;

```
### Question 6

Using the data provided in lesson 1.5 ( https://github.com/su-ntu-ctp/5m-data-1.5-sql-advanced/tree/main/db ), using the `claim` and `car` tables, write a SQL query to compute the running total of the `travel_time` column for each `car_id` in the `claim` table. The resulting table should contain `id, car_id, travel_time, running_total`.

Answer:

```sql

```

### Question 7

Using the data provided in lesson 1.5 ( https://github.com/su-ntu-ctp/5m-data-1.5-sql-advanced/tree/main/db ), using a Common Table Expression (CTE), write a SQL query to return a table containing `id, resale_value, car_use` from `car`, where the car resale value is less than the average resale value for the car use.

Answer:

```sql

```

## Submission

- Submit the GitHub URL of your assignment solution to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
