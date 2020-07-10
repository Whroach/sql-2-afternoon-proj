# sql-2-afternoon-proj

1. PRACTICE JOINS

-- SELECT * FROM invoice_line
-- WHERE unit_price > 0.99

-- SELECT c.first_name, c.last_name, i.invoice_date, i.total FROM customer c 
-- JOIN invoice i ON i.invoice_id = c.customer_id 

-- SELECT c.first_name AS cFirstName, c.last_name AS cLastName, e.first_name AS eFirstName, e.last_name AS eLastName FROM customer c 
-- JOIN employee e ON e.employee_id = c.customer_id

-- SELECT alb.title, art.name FROM album AS alb
-- JOIN artist AS art ON art.artist_id = alb.artist_id


SELECT track_id FROM playlist_track AS pt
-- JOIN playlist AS p ON p.playlist_id = pt.playlist_id
-- WHERE p.name = 'Music'

SELECT name FROM track t
-- JOIN playlist_track p ON p.track_id = t.track_id
-- WHERE playlist_id = 5

-- SELECT t.name, p.name FROM track t
-- JOIN playlist_track pt ON t.track_id = pt.track_id
-- JOIN playlist p ON pt.playlist_id =  p.playlist_id

SELECT t.name, a.title FROM track t 
-- JOIN album a ON a.album_id = t.album_id
-- JOIN genre g ON g.genre_id = t.genre_id
-- where g.name = 'Alternative & Punk'


2. PRACTICE NESTED QUERIES

-- SELECT * FROM invoice 
-- WHERE invoice_id IN
-- (SELECT invoice_id FROM invoice_line 
--  WHERE unit_price > 0.99)

SELECT * FROM playlist_track
-- WHERE playlist_id IN
-- (SELECT playlist_id FROM playlist
--  WHERE name = 'Music')

-- SELECT name FROM track
-- WHERE track_id IN (
--   SELECT playlist_id FROM playlist_track
--   WHERE playlist_id = 5)


-- SELECT * FROM track
-- WHERE genre_id IN (
--   SELECT genre_id FROM genre
--   WHERE name = 'Comedy')

-- SELECT * FROM track
-- WHERE album_id IN (
--   SELECT album_id FROM album 
--   WHERE title = 'Fireball')

-- SELECT * FROM track
-- WHERE album_id IN (
--   SELECT album_id FROM album
--   WHERE artist_id IN (
--     SELECT artist_id FROM artist
--     	WHERE name = 'Queen'))


3. PRACTICE UPDATING ROWS

-- UPDATE customer
-- SET fax = NULL
-- WHERE fax IS NOT NULL

-- SELECT fax FROM customer

UPDATE customer
-- SET company = 'Self'
-- WHERE company IS NOT NULL


-- SELECT * FROM customer
-- WHERE first_name = 'Julia' AND last_name = 'Barnett'
-- UPDATE customer
-- SET last_name = 'Thompson'
-- WHERE customer_id = 28

-- SELECT * FROM customer
-- WHERE email = 'luisrojas@yahoo.cl'
-- UPDATE customer
-- SET support_rep_id = 4
-- WHERE customer_id = 57

-- UPDATE track
-- SET composer = 'The darkness around us'
-- WHERE genre_id IN (
--   SELECT genre_id FROM genre
--   	WHERE name = 'Metal')
-- AND composer IS NULL



3. GROUP BY

-- SELECT COUNT(*), g.name FROM track T
-- JOIN genre g ON t.genre_id = g.genre_id
-- GROUP BY g.name

-- SELECT COUNT(*) , g.name FROM track t
-- JOIN genre g ON g.genre_id = t.genre_id
-- WHERE g.name='Pop' AND g.name = 'Rock'
-- GROUP BY g.name

-- SELECT a.name, COUNT(alb.artist_id) FROM artist a
-- JOIN album alb ON a.artist_id = alb.artist_id
-- GROUP BY a.name


4. DISTINCT

-- SELECT DISTINCT(composer) FROM track

-- SELECT DISTINCT(billing_postal_code) FROM invoice

-- SELECT DISTINCT (company) FROM customer


5. DELETE ROWS

-- DELETE FROM practice_delete
-- WHERE type = 'bronze'

-- DELETE FROM practice_delete
-- WHERE type = 'silver'

-- DELETE FROM practice_delete
-- WHERE value = 150

-- SELECT * FROM practice_delete


6. eCommerce Simulation

-- CREATE TABLE users (
--   user_id SERIAL PRIMARY KEY,
--   name VARCHAR(100),
--   email VARCHAR(100)

-- );

-- CREATE TABLE products (
--   product_id SERIAL PRIMARY KEY,
--   name VARCHAR(100),
--   price INT

-- );

-- CREATE TABLE orders (
--   order_id SERIAL PRIMARY KEY,
--   user_id INTEGER REFERENCES users(user_id),
--   product_id INTEGER REFERENCES products(product_id)
--   );

-- INSERT INTO users (name, email)
-- VALUES ('Todd Gurley', 'Togur@email.com'), ('Chris Carson', 'Ccarson@email.com'), ('Lamar Miller', 'Lmiller@email.com')


-- INSERT INTO products (name, price)
-- VALUES ('cleats', 150), ('helment', 100), ('jersey', 95), ('football', 50)

-- ALTER TABLE orders
-- ADD COLUMN quantity INT

-- INSERT INTO orders (quantity)
-- VALUES (4)

-- UPDATE orders SET user_id = 4 WHERE order_id = 1

-- SELECT * FROM orders

-- SELECT p.name FROM products p
-- JOIN orders o ON p.product_id = o.product_id
-- WHERE order_id = 1

-- SELECT SUM(quantity) FROM orders

-- SELECT DISTINCT(quantity), u.name FROM orders o 
-- JOIN users u ON o.user_id = u.user_id

















