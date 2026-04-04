# Aggregation of Records

**THis section contain the following lessons:**

## 1. Aggregating and Grouping

![grouping and aggregation](./images/grouping_aggregation.png)

**Grouping**

![grouping](./images/grouping1.png)

![grouping](./images/grouping2.png)

**~~NOTE:~~** when we use grouping we will not be able to select any oraginal columns without aggregation the only column we can select without aggregation is the column we used for grouping.

**Aggregation**

![aggregation](./images/aggregation1.png)

![aggregation](./images/aggregation2.png)

**~~NOTE:~~** when we use aggregation we will not be able to select any oraginal columns without grouping the only column we can select without grouping is the column we used for aggregation.

**Grouping with Aggregation**

**Example Oen:**
![group with max](./images/group_max.png)

```sql

SELECT user_id, MAX(id)
FROM comments
GROUP BY user_id;

```

![group with max](./images/group_max2.png)


**Example Two:**

![group with count](./images/group_count.png)

```sql

SELECT user_id, COUNT(id) AS number_of_comment
FROM comments
GROUP BY user_id;

```

![group with count](./images/group_count2.png)

**~~NOTE:~~** `count()` do not count null values so if some row have null value in the column we aply `count()` on that row will not be included unless we do `count(*)` ... `count(*)` count all value of coulmn even the null.

**Example Three:**

![group with count](./images/group_count3.png)

```sql

SELECT photo_id, COUNT(*) AS number_of_comment
FROM comments
GROUP BY photo_id;

```

![group with count](./images/group_count4.png)


## 2. Filtering Groups with Having

![having](./images/having.png)

**~~NOTE:~~**
1. We use having to fillter the groups so if we do not use **GROUP BY** key word we can not use having and having alwasy come after group by.

2. if we do just filltering this mean we need to use **WHERE** but if we want to do filltering with aggreation function that mean we will use **HAVING**

**Example One:**

![having](./images/having2.png)

```sql

SELECT photo_id, COUNT(*) AS number_of_comments
FROM comments
WHERE photo_id < 3
GROUP BY photo_id 
HAVING COUNT(*) > 2;

```

![having](./images/having3.png)

**Example Two:**

![having](./images/having4.png)

```sql

SELECT user_id, COUNT(*) AS number_of_comments
FROM comments
WHERE photo_id BETWEEN 1 AND 50
GROUP BY user_id 
HAVING COUNT(*) > 20;

```

![having](./images/having5.png)


[Back to read me](README.md)