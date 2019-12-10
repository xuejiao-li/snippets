# MySQL Snippets

[Web Dev Simplified Youtube Tutorial Channel](https://www.youtube.com/watch?v=p3qvj9hO_Bo&t=2996s)

## Basic 

- Keywords are not case sensitive
- Put the semi colon to the end of your SQL comment
- Best practice to put all UPPER case for keywords
- `-- this ic single line comment in SQL`
- ``` /* This is used for multiline comments for sql */```

Basic common SQL commands
```SQL
CREATE DATABASE test;
DROP DATABASE test; -- Almost never use for existing databases. 



```


Example for a record company

**CREATE UPDATE DELETE**
```SQL 
CREATE DATABASE record_company;
USE record_company;

CREATE TABLE test (
    test_column INT 
);

ALTER TABLE test
ADD another_column VARCHAR(255); -- Add another column named "another_column" and the type is string, the max length is 255 character

DROP TABLE test;

CREATE TABLE bankds (
    id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL, -- MUST ALWAYS HAVE A VALUE
    PRIMARY KEY (id)

);

CREATE TABLE albums (
    id INT NOT NULL AUTO_INCREMENT, 
    name VARCHAR(255) NOT NULL,
    release_year INT, 
    band_id INT NOT NULL,
    PRIMARY KEY (id),
    FOREIGN KEY (band_id) REFERENCES bands(id) -- SQL doesn't allow us to create album if we give an band id that not existed, also if we try to delete a band that has albums linking to that band that it will throw an error saying you have albums that exist for this band, that you can not delete the band unless you also delete the albums that go with the band. 

INSERT INTO bands (name)
VALUES ('Iron Maiden');

INSERT INTO bands (name)
VALUES ('Deuce'), ('Avenged Sevenfold'), ('Ankor');


SELECT * FROM bands;

SELECT * FROM bands LIMIT 2;

SELECT name FROM bands;
SELECT id AS 'ID', name AS 'Band Name' 
FROM bands;

SELECT * FROM bands ORDER BY name DESC; -- Defaul ASC

INSERT INTO albums (name, release_year, band_id)
VALUES ('The Number of the Beasts', 1985, 1),
        ('Power Slave', 1984, 1),
        ('Nightmare', 2018, 2),
        ('Nightmare', 2010, 3),
        ('Test Album', NULL, 3);

SELECT DISTINCT name FROM albums;

UPDATE albums 
SET release_year = 1982
WHERE id = 1;

SELECT * FROM albums 
WHERE release_year < 2000;

SELECT * FROM albums
WHERE name LIKE '%er%' OR band_id =2; -- % wildcard % any amount of characters before and after 'er'

SELECT * FROM albums 
WHERE release_year = 1984 AND band_id = 1; 

SELECT * FROM albums 
WHERE release_year BETWEEN 2000 AND 2018;

SELECT * FROM albums 
WHERE release_year IS NULL;

DELETE FROM albums 
WHERE id = 5; 

```

**JOIN** 

1. INNER JOIN is the default JOIN: Combines data where both the values on the LEFT and RIGHT, Only returns values when there is a match. 
2. LEFT JOIN: Will allow us all of the bands don't have albums will also show up. List everything on the LEFT. 
3. RIGHT JOIN


```SQL

SELECT * FROM bands
JOIN albums ON bands.id = albums.band_id; -- All the columns in bands table and in albums table returned where bands.id equals albums.band_id

SELECT * FROM bands
INNER JOIN albums ON bands.id = albums.band_id;

SELECT * FROM bands
LEFT JOIN albums ON bands.id = albums.band_id;

SELECT * FROM bands
RIGHT JOIN albums ON bands.id = albums.band_id;

```

**Aggregate Functions and Group By**

```SQL 

SELECT AVG(release_year) FROM albums: -- SUM, COUNT

SELECT band_id, COUNT(Band_id) FROM albums 
GROUP BY band_id;


SELECT b.name AS band_name, COUNT(a.id) AS num_albums  -- select columns that we want
FROM bands AS b
LEFT JOIN albums AS a ON b.id = a.band_id 
GROUP BY b.id
HAVING num_albums = 1 ; -- HAVING IS THE SAME AS WHERE BUT HAPPENS AFTER GROUP BY

```

**Join Multiple Tables** 


```SQL
SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName
FROM ((Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID)
INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID);
```

**Other Functions in MySql**

- `SELECT CURRENT_TIMESTAMP;`


## This is some practice including for joining multiple tables and how to pull the most recent notes for the deal table 

```SQL

CREATE DATABASE deals;

USE deals;

CREATE TABLE users (
	id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
	PRIMARY KEY (id)

);

CREATE TABLE deals (
	id INT NOT NULL AUTO_INCREMENT,
    stock VARCHAR(255) NOT NULL,
    customer VARCHAR (255) NOT NULL,
    PRIMARY KEY (id)
);

CREATE TABLE comments (
	id INT NOT NULL AUTO_INCREMENT,
    date_posted DATETIME NOT NULL,
    user_id INT NOT NULL,
    deal_id INT NOT NULL,
    PRIMARY KEY (id),
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (deal_id) REFERENCES deals(id)

);

ALTER TABLE comments
ADD note TEXT;

INSERT INTO users (name)
VALUES ('Jade'), ('Colema');

SELECT * FROM users;

INSERT INTO deals (stock, customer)
VALUES ('20001', 'Xuejiao'), ('30001', 'Meng');

SELECT * FROM deals;

INSERT INTO comments (date_posted, user_id, deal_id, note)
VALUES (current_timestamp(), 2, 2, 'This is the SECOND note for second deal');


SELECT * FROM comments;

-- Join 3 tables together

SELECT d.stock as stock, d.customer AS customer, u.name AS finance, c.note as comment, c.date_posted as posted_on, c.id
FROM deals AS d
LEFT JOIN comments AS c ON d.id = c.deal_id
LEFT JOIN users as u ON u.id = c.user_id;

SELECT MAX(c.id)
FROM comments as c
GROUP BY deal_id;


SELECT * FROM
(SELECT MAX(id) AS id FROM  comments GROUP BY deal_id) t1
INNER JOIN 
(SELECT id, date_posted, user_id, deal_id, note from comments) t2;

-- How to join multiple tables and use the select statement as a table. How to show the most recent note for the deal table
SELECT d.stock, d.customer, u.name AS Finance, t2.note AS Comments
FROM deals as d
LEFT JOIN 
(SELECT id, date_posted, user_id, deal_id, note from comments) t2
ON d.id = t2.deal_id
INNER JOIN 
(SELECT MAX(id) AS comment_id FROM  comments GROUP BY deal_id) t1
ON t1.comment_id = t2.id
LEFT JOIN
users as u ON u.id = t2.user_id;


```

  



