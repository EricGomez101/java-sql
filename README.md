# Introduction

Working with SQL

# Instructions

Surf to [SQL Try Editor at W3Schools.com](https://www.w3schools.com/Sql/tryit.asp?filename=trysql_select_top)  
Answer the following data queries. Keep track of the SQL you write by pasting it into this document under its appropriate header below. You will be submitting that through the regular fork, change, pull process.

### **Clicking the `Restore Database` button in the page will repopulate the database with the original data and discard all changes you have made**.

### find all customers that live in London. Returns 6 records.
* SELECT * FROM customers WHERE city = "London"
### find all customers with postal code 1010. Returns 3 customers.
* SELECT * FROM customers WHERE city = "London"
### find the phone number for the supplier with the id 11. Should be (010) 9984510.
* SELECT * FROM suppliers WHERE supplierID = 11
### list orders descending by the order date. The order with date 1997-02-12 should be at the top.
* SELECT * FROM Orders ORDER BY orderdate desc
### find all suppliers who have names longer than 20 characters. You can use `length(SupplierName)` to get the length of the name. Returns 11 records.
* SELECT * FROM suppliers WHERE len(suppliername) > 20
### find all customers that include the word "market" in the name. Should return 4 records.
* SELECT * FROM customers WHERE customername LIKE "%market%"
### add a customer record for _"The Shire"_, the contact name is _"Bilbo Baggins"_ the address is _"1 Hobbit-Hole"_ in _"Bag End"_, postal code _"111"_ and the country is _"Middle Earth"_.
* INSERT INTO customers (contactname, address, city, postalcode, country)
* VALUES ("BilboBaggins", "1 Hobbit-Hole", "Bag End", "111", "Middle Earth")
### update _Bilbo Baggins_ record so that the postal code changes to _"11122"_.
* UPDATE customers
* SET postalcode = "11122"
* WHERE contactname = "BilboBaggins"; 
### list orders grouped by customer showing the number of orders per customer. _Rattlesnake Canyon Grocery_ should have 7 orders.
* SELECT Customers.CustomerName, COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders
* LEFT JOIN Customers ON Orders.CustomerID = Customers.CustomerID
* GROUP BY CustomerName
### list customers names and the number of orders per customer. Sort the list by number of orders in descending order. _Ernst Handel_ should be at the top with 10 orders followed by _QUICK-Stop_, _Rattlesnake Canyon Grocery_ and _Wartian Herkku_ with 7 orders each.
* SELECT Customers.CustomerName, COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders
* LEFT JOIN Customers ON Orders.CustomerID = Customers.CustomerID
* GROUP BY CustomerName
* ORDER BY COUNT(Orders.OrderID) DESC;
### list orders grouped by customer's city showing number of orders per city. Returns 58 Records with _Aachen_ showing 2 orders and _Albuquerque_ showing 7 orders.
* SELECT COUNT(Orders.OrderID) AS NumberOfOrders, Customers.City 
* FROM Orders
* LEFT JOIN Customers ON Orders.CustomerID = Customers.CustomerID
* GROUP BY City
* ORDER BY city asc;

### delete all customers that have no orders. Should delete 17 (or 18 if you haven't deleted the record added) records.
* DELETE FROM customers WHERE CustomerID NOT IN (SELECT CustomerID from orders)
## Create Database and Table

### Keep track of the code you write and paste at the end of this document

- use [`SQLite Studio`](https://sqlitestudio.pl/index.rvt) to create a database, name it `budget.sqlite3`.
- add an `accounts` table with the following _schema_:

  - `id`, numeric value with no decimal places that should autoincrement.
  - `name`, string, add whatever is necessary to make searching by name faster.
  - `budget` numeric value.

- constraints
  - the `id` should be the primary key for the table.
  - account `name` should be unique.
  - account `budget` is required.

