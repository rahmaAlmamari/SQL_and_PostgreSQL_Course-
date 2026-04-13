# Assembling Queries with SubQueries

**~~NOTE:~~** this section use the following DB:

[SQL_DB](./sql/001+-+sq+-+data.sql)

**THis section contain the following lessons:**

## 1. What's a Subquery?

**A subquery** in SQL is simply a query written inside another query or in anther words "A subquery = a query inside a query".

Q: List the name and price of all products that are more expensive then all products in the 'Toys' department?

```sql

SELECT
  name,
  price
FROM
  products
WHERE
  price > (
    SELECT
      MAX(price)
    FROM
      products
    WHERE
      department = 'Toys'
  );

```

![subquery](./images/subquery.png)

**~~NOTE:~~** we can put so many queries inside anther query as subquery.


![subquery](./images/subquery2.png)

![subquery](./images/subquery3.png)

![subquery](./images/subquery4.png)


## 2. Subqueries in a Select

![subquery in select](./images/subquery_select.png)

```sql 

SELECT name, price, (
   SELECT MAX(price) FROM products
)
FROM products
WHERE price > 867;

```

![subquery in select](./images/subquery_select2.png)

**~~NOTE:~~** we can rename the single value which came from the subquery in select.

```sql

SELECT name, price, (
   SELECT price FROM products WHERE id = 3
) AS id_3_products
FROM products
WHERE price > 867;

```

![subquery in select](./images/subquery_select3.png)


## 3. Subqueries in a From

**Example of Subqueries that Return a many rows and columns in From:**

![subquery in from](./images/subquery_from.png)

```sql

SELECT
  name,
  price / weight AS price_weight_ratio
FROM
  products;

```

![subquery in from](./images/subquery_from2.png)

```sql

SELECT name, price_weight_ratio
FROM (
SELECT
  name,
  price / weight AS price_weight_ratio
FROM
  products
) AS p
WHERE price_weight_ratio > 5;

```

![subquery in from](./images/subquery_from3.png)


**Example of Subqueries that Return a Value in From:**

![subquery in from](./images/subquery_from4.png)

```sql

SELECT *
FROM (
SELECT MAX(price) FROM products
) AS p;

```

![subquery in from](./images/subquery_from5.png)


## 4. Example of a Subquery in a From

**Example One:**

![subquery in from example](./images/subquery_from_example.png)

```sql 

SELECT AVG(o.order_count)
FROM (
 SELECT user_id, COUNT(*) AS order_count FROM orders GROUP BY user_id
) AS o;

```

![subquery in from example](./images/subquery_from_example2.png)


## 5. Subqueries in a Join Clause

![subquery in join](./images/subquery_join.png)

```sql

SELECT first_name 
FROM users
JOIN (
  SELECT user_id FROM orders WHERE product_id = 3
) AS o 
ON o.user_id = user_id;

```

![subquery in join](./images/subquery_join2.png)


## 6. Subqueries with Where

![subquery in where](./images/subquery_where_main.png)

**Subquery with where (IN)**

![subquery in where](./images/subquery_where.png)

![subquery in where](./images/subquery_where2.png)

```sql

SELECT
  id
FROM
  orders
WHERE
  product_id IN (
    SELECT
      id
    FROM
      products
    WHERE
      price / weight > 50
  );

```

![subquery in where](./images/subquery_where3.png)

**Subquery with where (>)**

![subquery in where](./images/subquery_where4.png)

```sql

SELECT
  name
FROM
  products
WHERE
  price > (
    SELECT
      AVG(price)
    FROM
      products
  );

```

![subquery in where](./images/subquery_where5.png)

**Subquery with where (NOT IN)**

![subquery in where](./images/subquery_where6.png)

```sql

SELECT
  name,
  department
FROM
  products
WHERE
  department NOT IN (
    SELECT
      department
    FROM
      products
    WHERE
      price < 100
  );

```

![subquery in where](./images/subquery_where7.png)

**Subquery with where (> ALL)**

![subquery in where](./images/subquery_where8.png)

```sql

SELECT
  name,
  department,
  price
FROM
  products
WHERE
  price > ALL (
    SELECT
      price
    FROM
      products
    WHERE
      department = 'Industrial'
  );

```

![subquery in where](./images/subquery_where9.png)

**Subquery with where (> SOME, > ANY)**

![subquery in where](./images/subquery_where10.png)

```sql

SELECT
  name,
  department,
  price
FROM
  products
WHERE
  price > SOME (
    SELECT
      price
    FROM
      products
    WHERE
      department = 'Industrial'
  );

```

![subquery in where](./images/subquery_where11.png)


104. Data Structure with Where Subqueries
105. Exercise Overview
Coding Exercise 21: Subquery Where's
106. Exercise Solution
107. The Not In Operator with a List
108. A New Where Operator
109. Finally Some!
Quiz 10: Is It A Valid Subquery?
110. Exercise Overview
Coding Exercise 22: Practice Your Subqueries!
111. A Quick Solution
112. Probably Too Much About Correlated Subqueries
113. More on Correlated Subqueries
114. A Select Without a From?
115. Exercise Overview
Coding Exercise 23: From-less Selects
116. Exercise Solution