# Selecting Distinct Records

**~~NOTE:~~** this section use the following DB:

[SQL_DB](./sql/001+-+sq+-+data.sql)

## 1. Selecting Distinct Values

![distinct](./images/distinct.png)

```sql 

SELECT DISTINCT department
FROM products;

```

![distinct](./images/distinct2.png)

```sql

SELECT COUNT(DISTINCT department)
FROM products;

```

![distinct](./images/distinct3.png)

```sql

SELECT DISTINCT department, name
FROM products;

```

![distinct](./images/distinct4.png)

