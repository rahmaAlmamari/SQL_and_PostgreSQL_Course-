# Filtering Records

**THis section contain the following lessons:**

## 1. Filtering Rows with "Where"

![Table](./images/table.png)

```sql 

SELECT name, country
FROM cities
WHERE area > 4000;

```

![Where](./images/where.png)

**The order SQL run query**

![sql orde run](./images/sql_run_order.png)

![comparison operators](./images/comparison_operators.png)

```sql

SELECT name, area
FROM cities
WHERE area = 8223;

```

![equal](./images/equal.png)

```sql

SELECT name, area
FROM cities
WHERE area != 8223;

```

![not equal](./images/not_equal.png)

```sql

SELECT name, area
FROM cities
WHERE area BETWEEN 2000 AND 4000;

```

![bettwen](./images/bettwen.png)

```sql

SELECT name, area
FROM cities
WHERE name IN ('Delhi', 'Shanghai');

```

![in](./images/in.png)

```sql

SELECT name, area
FROM cities
WHERE name NOT IN ('Delhi', 'Shanghai');

```

![not in](./images/not_in.png)

```sql

SELECT name, area
FROM cities
WHERE area NOT IN (3043, 8223) AND name = 'Delhi';

```

![not in with and](./images/not_in_with_and.png)

```sql

SELECT name, population / area AS population_density
FROM cities
WHERE population / area > 6000;

```

![where with math operation](./images/where_with_math.png)


## 2. Updating Rows

![update](./images/update.png)

**Update Role:**

UPDATE tabble_name SET column_Name_to_update = new_value WHERE condation;

```sql

UPDATE cities 
SET population = 39505000
WHERE name = 'Tokyo';

```
![update example](./images/update_example.png)


## 3. Deleting Rows

![delete](./images/delete.png)

**Delete Role:**

DELETE FROM tabble_name WHERE condation;

```sql

DELETE FROM cities WHERE name = 'Tokyo';

```
![delete example](./images/delete_example.png)


[Back to read me](README.md)
