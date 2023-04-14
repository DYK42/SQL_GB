CREATE DATABASE market;
USE market;

CREATE TABLE phone
(
id_phone INT PRIMARY KEY NOT NULL,
product_name VARCHAR(30) NOT NULL,
manufacturer VARCHAR(30) NOT NULL,
product_count INT NOT NULL,
price INT NOT NULL
);

INSERT phone
(
id_phone, product_name, manufacturer, product_count, price
)
VALUES
(1, "iPhone X", "Apple", 3, 76000),
(2, "iPhone 8", "Apple", 2, 51000),
(3, "Galaxy S9", "Samsung", 2, 56000),
(4, "Galaxy S8", "Samsung", 1, 41000),
(5, "P20 Pro", "Huawei", 5, 36000);

SELECT product_name, manufacturer, price
FROM phone
WHERE product_count > 2;

SELECT product_name, product_count, price
FROM phone
WHERE manufacturer = "Samsung";

SELECT product_name
FROM phone
WHERE product_name REGEXP "iPhone";

SELECT product_name
FROM phone
WHERE manufacturer REGEXP "Samsung";

SELECT product_name
FROM phone
WHERE product_name REGEXP "8";
