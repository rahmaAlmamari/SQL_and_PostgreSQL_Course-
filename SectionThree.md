# Working with Tables

**THis section contain the following lessons:**

~~NOTE:~~ This section use the following DB 

![DB](./images/DB.png)

## 1. Design Some Schema

![ERD](./images/app1.png)

## 2. One-to-Many and Many-to-One Relationships

**One to Many Relationships**

![one to many](./images/one_many.png)

**Many to One Relationships**

![many to one](./images/many_one.png)

**Examples**

![examples](./images/onemany_example.png)


## 3. One-to-One and Many-to-Many Relationships

**One to One Relationships**

![one to one](./images/one_one.png)

**Many to Many Relationships**

![many to many](./images/many_many.png)


## 4.Primary Keys and Foreign Keys

![PK and FK](./images/pk_fk.png)

![PK and FK](./images/pk_fk2.png)


## 5. Understanding Foreign Keys

![FK](./images/fk2.png)

![FK](./images/fk.png)



## 6. Auto-Generated ID's

**User Table**

```sql

CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  username VARCHAR(50)
);

```
~~NOTE:~~ SERIAL it is a key word that tell the PostgreSQL to generate int number for each new user in an increasing way.

![user table](./images/user_table.png)

```sql

INSERT INTO users (username)
VALUES 
    ('rahma'),
    ('ali'),
    ('fatema'),
    ('fahad');

```

![user table](./images/user_table2.png)

```sql

SELECT * FROM users;

```

![user table](./images/user_table3.png)


## 7. Creating Foreign Key Columns

**Photo Table**

```sql

CREATE TABLE photo (
   id SERIAL PRIMARY KEY,
   url VARCHAR(200),
   user_id INTEGER REFERENCES users(id)
);

```

~~NOTE:~~ to create FK use this role -> FK_ColumnName DataType REFERENCES TableName(PK_Column_Name)

![photo table](./images/photo_table.png)


```sql

INSERT INTO photo (url, user_id)
VALUES 
   ('http://etyru.com', 1),
   ('http://yyyujbb.com', 1),
   ('http://wwssxx.com', 3),
   ('http://wefvbhyujm.com', 4);

```

![photo table](./images/photo_table2.png)

```sql

SELECT * FROM photo;

```

![photo table](./images/photo_table3.png)


## 8.Foreign Key Constraints Around Insertion

![FK insert](./images/fk_insert.png)


## 9. Constraints Around Deletion

![FK delete](./images/fk_delete.png)

**EXAMPLE ONE**

```sql

CREATE TABLE photos (
id SERIAL PRIMARY KEY,
url VARCHAR(200),
user_id INTEGER REFERENCES users(id) ON DELETE CASCADE
);
 
INSERT INTO photos (url, user_id)
VALUES
('http:/one.jpg', 4),
('http:/two.jpg', 1),
('http:/25.jpg', 1),
('http:/36.jpg', 1),
('http:/754.jpg', 2),
('http:/35.jpg', 3),
('http:/256.jpg', 4);

```

![new photo table](./images/fk_delete2.png)

```sql

DELETE FROM users WHERE id = 1;

```

![delete user](./images/delete_users.png)

![delete user](./images/delete_user2.png)


**EXAMPLE TWO:**

```sql 

CREATE TABLE photos (
id SERIAL PRIMARY KEY,
url VARCHAR(200),
user_id INTEGER REFERENCES users(id) ON DELETE SET NULL
);
 
INSERT INTO photos (url, user_id)
VALUES
('http:/one.jpg', 4),
('http:/754.jpg', 2),
('http:/35.jpg', 3),
('http:/256.jpg', 4);

```

![delete user](./images/delete_user3.png)

![delete user](./images/delete_user4.png)

![delete user](./images/delete_users5.png)


[Back to read me](README.md)