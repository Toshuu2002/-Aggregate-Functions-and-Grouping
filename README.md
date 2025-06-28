# -Aggregate-Functions-and-Grouping

-- Creating the table
CREATE TABLE sales (
    sale_id INTEGER PRIMARY KEY,
    product_id INTEGER,
    category TEXT,
    quantity INTEGER,
    price INTEGER
);

-- INSERT statements,
INSERT INTO sales (sale_id, product_id, category, quantity, price) VALUES (1,101, 'Books',3,10);
INSERT INTO sales (sale_id, product_id, category, quantity, price) VALUES (2,102, 'Books',2,15);
INSERT INTO sales (sale_id, product_id, category, quantity, price) VALUES (3,201, 'Electronics',1,100);
INSERT INTO sales (sale_id, product_id, category, quantity, price) VALUES (4,103, 'Books',20,50);
INSERT INTO sales (sale_id, product_id, category, quantity, price) VALUES (5,202, 'Electronics',4,80);
INSERT INTO sales (sale_id, product_id, category, quantity, price) VALUES (6,203, 'Electronics',8,120);

-- Select all columns
SELECT * FROM sales;

-- Total sales amount by category
SELECT category, SUM(quantity * price) AS total_sales FROM sales GROUP BY category;
    
-- Average quantity sold per product category
SELECT category, AVG(quantity) AS avg_quantity FROM sales GROUP BY category;
    
-- Number of sales per product category
SELECT category, COUNT(*) AS num_sales FROM sales GROUP BY category;
    
-- Total sales per category (only categories with sales > 100)
SELECT category, SUM(quantity * price) AS total_sales FROM sales GROUP BY category HAVING total_sales > 100;
    
--  Maximum sale amount per category
SELECT category, MAX(quantity * price) AS max_sale FROM sales GROUP BY category;
