# MySQL Cheat Sheet

> Help with SQL commands to interact with a MySQL database

## MySQL Locations
* Mac             */usr/local/mysql/bin*
* Windows         */Program Files/MySQL/MySQL _version_/bin*
* Xampp           */xampp/mysql/bin*

## Add mysql to your PATH

```bash
# Current Session
export PATH=${PATH}:/usr/local/mysql/bin
# Permanantly
echo 'export PATH="/usr/local/mysql/bin:$PATH"' >> ~/.bash_profile
```

On Windows - https://www.qualitestgroup.com/resources/knowledge-center/how-to-guide/add-mysql-path-windows/

## Login

```bash
mysql -u root -p
```

## Show Users

```sql
SELECT User, Host FROM mysql.user;
```

## Create User

```sql
CREATE USER 'user_name'@'localhost' IDENTIFIED BY 'password_name';
```

## Grant All Priveleges On All Databases

```sql
GRANT ALL PRIVILEGES ON * . * TO 'user_name'@'localhost';
FLUSH PRIVILEGES;
```

## Show Grants

```sql
SHOW GRANTS FOR 'user_name'@'localhost';
```

## Remove Grants

```sql
REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'user_name'@'localhost';
```

## Delete User

```sql
DROP USER 'user_name'@'localhost';
```

## Exit

```sql
exit;
```

## Show Databases

```sql
SHOW DATABASES
```

## Create Database

```sql
CREATE DATABASE acme;
```

## Delete Database

```sql
DROP DATABASE acme;
```

## Select Database

```sql
USE acme;
```

## Create Table

```sql
CREATE TABLE users(
id INT AUTO_INCREMENT,
   first_name VARCHAR(100),
   last_name VARCHAR(100),
   email VARCHAR(50),
   password VARCHAR(20),
   location VARCHAR(100),
   dept VARCHAR(100),
   is_admin TINYINT(1),
   register_date DATETIME,
   PRIMARY KEY(id)
);
```

## Delete / Drop Table

```sql
DROP TABLE tablename;
```

## Show Tables

```sql
SHOW TABLES;
```

## Insert Row / Record

```sql
INSERT INTO users (first_name, last_name, email, password, location, dept, is_admin, register_date) values ('Brad', 'Traversy', 'brad@gmail.com', '123456','Massachusetts', 'development', 1, now());
```

## Insert Multiple Rows

```sql
INSERT INTO users (first_name, last_name, email, password, location, dept,  is_admin, register_date) values ('Fred', 'Smith', 'fred@gmail.com', '123456', 'New York', 'design', 0, now()), ('Sara', 'Watson', 'sara@gmail.com', '123456', 'New York', 'design', 0, now()),('Will', 'Jackson', 'will@yahoo.com', '123456', 'Rhode Island', 'development', 1, now()),('Paula', 'Johnson', 'paula@yahoo.com', '123456', 'Massachusetts', 'sales', 0, now()),('Tom', 'Spears', 'tom@yahoo.com', '123456', 'Massachusetts', 'sales', 0, now());
```

## Select

```sql
SELECT * FROM users;
SELECT first_name, last_name FROM users;
```

## Where Clause

```sql
SELECT * FROM users WHERE location='Massachusetts';
SELECT * FROM users WHERE location='Massachusetts' AND dept='sales';
SELECT * FROM users WHERE is_admin = 1;
SELECT * FROM users WHERE is_admin > 0;
```

## Delete Row

```sql
DELETE FROM users WHERE id = 6;
```

## Update Row

```sql
UPDATE users SET email = 'freddy@gmail.com' WHERE id = 2;

```

## Add New Column

```sql
ALTER TABLE users ADD age VARCHAR(3);
```

## Modify Column

```sql
ALTER TABLE users MODIFY COLUMN age INT(3);
```

## Order By (Sort)

```sql
SELECT * FROM users ORDER BY last_name ASC;
SELECT * FROM users ORDER BY last_name DESC;
```

## Concatenate Columns

```sql
SELECT CONCAT(first_name, ' ', last_name) AS 'Name', dept FROM users;

```

## Select Distinct Rows

```sql
SELECT DISTINCT location FROM users;

```

## Between (Select Range)

```sql
SELECT * FROM users WHERE age BETWEEN 20 AND 25;
```

## Like (Searching)

```sql
SELECT * FROM users WHERE dept LIKE 'd%';
SELECT * FROM users WHERE dept LIKE 'dev%';
SELECT * FROM users WHERE dept LIKE '%t';
SELECT * FROM users WHERE dept LIKE '%e%';
```

## Not Like

```sql
SELECT * FROM users WHERE dept NOT LIKE 'd%';
```

## IN

```sql
SELECT * FROM users WHERE dept IN ('design', 'sales');
```

## Create & Remove Index

```sql
CREATE INDEX LIndex On users(location);
DROP INDEX LIndex ON users;
```

## New Table With Foreign Key (Posts)

```sql
CREATE TABLE posts(
id INT AUTO_INCREMENT,
   user_id INT,
   title VARCHAR(100),
   body TEXT,
   publish_date DATETIME DEFAULT CURRENT_TIMESTAMP,
   PRIMARY KEY(id),
   FOREIGN KEY (user_id) REFERENCES users(id)
);
```

## Add Data to Posts Table

```sql
INSERT INTO posts(user_id, title, body) VALUES (1, 'Post One', 'This is post one'),(3, 'Post Two', 'This is post two'),(1, 'Post Three', 'This is post three'),(2, 'Post Four', 'This is post four'),(5, 'Post Five', 'This is post five'),(4, 'Post Six', 'This is post six'),(2, 'Post Seven', 'This is post seven'),(1, 'Post Eight', 'This is post eight'),(3, 'Post Nine', 'This is post none'),(4, 'Post Ten', 'This is post ten');
```

## INNER JOIN

```sql
SELECT
  users.first_name,
  users.last_name,
  posts.title,
  posts.publish_date
FROM users
INNER JOIN posts
ON users.id = posts.user_id
ORDER BY posts.title;
```

## New Table With 2 Foriegn Keys

```sql
CREATE TABLE comments(
	id INT AUTO_INCREMENT,
    post_id INT,
    user_id INT,
    body TEXT,
    publish_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY(id),
    FOREIGN KEY(user_id) references users(id),
    FOREIGN KEY(post_id) references posts(id)
);
```

## Add Data to Comments Table

```sql
INSERT INTO comments(post_id, user_id, body) VALUES (1, 3, 'This is comment one'),(2, 1, 'This is comment two'),(5, 3, 'This is comment three'),(2, 4, 'This is comment four'),(1, 2, 'This is comment five'),(3, 1, 'This is comment six'),(3, 2, 'This is comment six'),(5, 4, 'This is comment seven'),(2, 3, 'This is comment seven');
```

## Left Join

```sql
SELECT
comments.body,
posts.title
FROM comments
LEFT JOIN posts ON posts.id = comments.post_id
ORDER BY posts.title;

```

## Join Multiple Tables

```sql
SELECT
comments.body,
posts.title,
users.first_name,
users.last_name
FROM comments
INNER JOIN posts on posts.id = comments.post_id
INNER JOIN users on users.id = comments.user_id
ORDER BY posts.title;

```

## Aggregate Functions

```sql
SELECT COUNT(id) FROM users;
SELECT MAX(age) FROM users;
SELECT MIN(age) FROM users;
SELECT SUM(age) FROM users;
SELECT UCASE(first_name), LCASE(last_name) FROM users;

```

## Group By

```sql
SELECT age, COUNT(age) FROM users GROUP BY age;
SELECT age, COUNT(age) FROM users WHERE age > 20 GROUP BY age;
SELECT age, COUNT(age) FROM users GROUP BY age HAVING count(age) >=2;

```



## WARNING MESSAGE SHOW

```sql
SHOW WARNINGS;
SHOW COUNT(*) WARNINGS;
SHOW ERROR;
SHOW COUNT(*) ERRORS;

```


## INSERT DATE

```sql

CREATE TABLE correct_date (
kolom_date DATE
);

INSERT INTO customer
values
('Andre','Rizaldi','1996@1@15');

INSERT INTO customer
values
('Andre','Rizaldi','1996-1-15');

INSERT INTO customer
values
('Andre','Rizaldi','19960115');

```


## INSERT TIME

```sql

CREATE TABLE correct_time (
kolom_time TIME
);

INSERT INTO order
values
(1, 'Andre','21:00:00');

INSERT INTO order
values
(2, 'Andre','210000');


```



## INSERT DATETIME / TIMESTAMP

```sql

CREATE TABLE correct_timestamp (
kolom_timestamp timestamp
);

INSERT INTO order
values
(1,'Andre','1996-01-15 20:30:30.59');


```


## CASE DI DALAM CASE

``` sql

select first_name, birth_date,
case city
	when 'Waltham' then
		case birth_date
			when '1986-03-28' then 'Older Waltham'
            else 'Young Waltham' end 
	when 'Hampton' then
		case birth_date
			when '1986-04-13' then 'Older Hampton'
            else 'Young Hampton' end
	when 'Orlando' then
		case birth_date
			when '1974-04-14' then 'Older Orlando'
            else 'Young Orlando' end
else city
end as new_colomn
from customers;

```


## CONCAT

```sql


```




## ALIAS
```sql
NOT ALLOWED

SELECT CUSTOMER AS C, C * 10;


```


## CONCAT
```sql

SELECT PLAYERNO, CONCAT(LEFT(INITIAL,1), '. ', NAME) AS FULL_NAME
FROM PLAYERS
WHERE LEFT(NAME,1) = 'B';

```



## COALESCE
```sql

SELECT INITIAL, NAME, COALESCE(LEAGUENO, '1')
FROM PLAYERS
WHERE Town = 'Straford';

```


## CASTING

```sql

SELECT	CONCAT(NAMA, CAST(tgl_lahir as char(10)))
FROM	data_pribadi;

```


## INTERVAL DATE

```sql

SELECT	first_name, last_name, birth_date
FROM	customers
WHERE	birth_date >= '1985-02-01'
AND	birth_date <= '1985-02-01' + INTERVAL 4 DAY + INTERVAL 6 DAY;

RESULT :
+------------+-----------+------------+
| first_name | last_name | birth_date |
+------------+-----------+------------+
| Freddi     | Boagey    | 1985-02-07 |
+------------+-----------+------------+

```


## ADD TIME

```sql

SELECT	MATCHNO,
	START_TIME,
	ADDTIME(START_TIME, '01:00:00')
FROM	MATCHES_SPECIAL;

The result is:
MATCHNO START_TIME ADDTIME(START_TIME, '01:00:00')
------- ---------- -------------------------------
1 14:10:12 15:10:12
2 17:00:00 18:00:00


```


```sql

SELECT	MATCHNO,
	END_TIME
FROM 	MATCHES_SPECIAL
WHERE	ADDTIME(END_TIME, '01:00:00') = '17:50:09';

+---------+----------+
| matchNO | end_time |
+---------+----------+
|       1 | 16:50:09 |
+---------+----------+
1 row in set (0.00 sec)

```


































## CORETAN
```sql

SELECT	PLAYERNO,
	DAYNAME(BIRTH_DAT),
	MONTHNAME(BIRTH_DATE),
	DAYOFYEAR(BIRTH_DATE)
FROM	PLAYERS
WHERE	PLAYERNO < 10;

```


```sql

SELECT	PLAYERNO,
	BIRTH_DATE,
	ADDDATE(BIRTH_DATE, INTERVAL 7 DAYS)
FROM 	PLAYERS
WHERE	DAYNAME(BIRTH_DATE) = 'Saturday';

```


```sql

SELECT	PLAYERNO,
	BEGIN_DATE,
	END_DATE,
	DATEDIFF(END_DATE, BEGIN_DATE)
FROM	COMMITTEE_MEMBERS
WHERE	DATEDIFF(END_DATE, BEGIN_DATE) > 500
OR	(END_DATE IS NULL AND DATEDIFF(CURRENT_DATE, BEGIN_DATE) > 500)
ORDER BY  PLAYERNO;

Explanation: The DATEDIFF function calculates the difference in days between
two dates or timestamps. The second condition has been added to find those committee members who still hold the position (the ones that have a null value as
END_DATE). Every day, this statement can have another result, of course

```


```sql

SELECT	Id_bin,
	nama,
	DAYNAME(tgl_lahir) as hari,
	MONTHNAME(tgl_lahir) as bulan,
	DAYOFYEAR(tgl_lahir) as tahun
FROM 	data_pribadi
ORDER BY nama;

```


```sql

INI BUAT APA ?

SET @@SQL_MODE= 'PIPES_AS_CONCAT'

```


```sql

SELECT	id_payment,
	payment_Date
FROM 	penalties
WHERE	payment_date >= '1982-12-25'
AND	payment_date <= '1982-12-25' + INTERVAL 6 DAY


The result is:
PAYMENTNO PAYMENT_DATE
--------- ------------
7 1982-12-30


Interval literals can be
added to dates only
For example, MySQL rejects the expression DATE + (INTERVAL
1 YEAR + INTERVAL 20 DAY).


```


```sql

MENYIMPAN DATA KEDALAM VARIABLE @

// MEMBUAT TABLE
CREATE TABLE	dataTimeStamp ( colomn1 TIMESTAMP );

// SET NILAI, KEDALAM @TIMEX_SAVE VARIABLE
SET @TIMEX_SAVE = TIMESTAMP('1996-01-15 18:00:00');

// MEMASUKKAN DATA KE DALAM TABLE dataTimeStamp
INSERT INTO dataTimeStamp
values (@TIME);

// MENAMPILKAN TABLE dataTimeStamp
SELECT * FROM dataTimeStamp;

```


```sql

SELECT 	CUSTOMER_ID
CASE	CUSTOMER_ID > 5
WHEN	0
THEN	'Less than 6'
ELSE	'Greater than 5'
END AS value,
customer_id > 5
FROM customers;

```

```sql

Example 5.55: Get the numbers of the players who live on Haseltine Lane in Stratford.

SELECT 	PLAYERNO
FROM 	PLAYERS
WHERE (TOWN, STREET) = ('Stratford', 'Haseltine Lane')


The result is:
PLAYERNO
--------
6
100

```



```sql

Example 5.55: Get the numbers of the players who live on Haseltine Lane in Stratford.

SELECT 	PLAYERNO
FROM 	PLAYERS
WHERE 	(TOWN, STREET) = (SELECT 'Stratford', 'Haseltine Lane')


The result is:
PLAYERNO
--------
6
100

```

```sql

Explanation: You can specify this statement without brackets; the result is the
same. However, you also can formulate the statement as follows:

(((((SELECT *
FROM TEAMS)))))

```


## ORDER BY HARUS DIBELAKANG
```sql

// INI SALAH KARENA ORDER BY TIDAK DIBELAKANG

SELECT 	PLAYERNO
FROM 	TEAMS
ORDER	BY PLAYERNO
UNION ALL
SELECT 	PLAYERNO
FROM 	PENALTIES


// SEHARUSNYA

SELECT 	PLAYERNO
FROM 	TEAMS
UNION
SELECT 	PLAYERNO
FROM 	PENALTIES 
ORDER 	BY PLAYERNO


If you want to sort the intermediate result of a select block before it is linked
with a UNION operator, you must use brackets. Therefore, the following statement is
allowed:

((SELECT PLAYERNO
FROM 	TEAMS
ORDER 	BY PLAYERNO))
UNION
((SELECT PLAYERNO
FROM 	PENALTIES))
ORDER 	BY PLAYERNO



```





