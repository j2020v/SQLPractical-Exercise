# SQL Practical Exercise

## Exercise  1 - Northwind Queries
<b>1.1</b>
```
SELECT CustomerID AS 'Customer ID', CompanyName AS 'Company Name', ContactName AS 'Contact Name',
ContactTitle AS 'Contact Title', Address, City, Region, PostalCode AS 'Postal Code', Country, Phone, Fax
FROM Customers
WHERE City = 'London' OR City = 'Paris'
```
<b>1.2</b>
```
SELECT ProductID AS 'Product ID', ProductName AS 'Product Name', SupplierID AS 'Supplier ID',
CategoryID AS 'Category ID', QuantityPerUnit AS 'Quantity Per Unit', UnitPrice AS 'Unit Price',
UnitsInStock AS 'Units In Stock', UnitsOnOrder AS 'Units On Order', ReorderLevel AS 'Reorder Level', Discontinued
FROM Products
WHERE QuantityPerUnit LIKE '%bottles';
```
<b>1.3</b>
```
SELECT s.CompanyName AS 'Company Name', s.Country, ProductID AS 'Product ID', ProductName AS 'Product Name',
p.SupplierID AS 'Supplier ID', CategoryID AS 'Category ID', QuantityPerUnit AS 'Quantity Per Unit',
UnitPrice AS 'Unit Price', UnitsInStock AS 'Units In Stock', UnitsOnOrder AS 'Units On Order', ReorderLevel AS 'Reorder Level', Discontinued
FROM Products p
JOIN Suppliers s
ON s.SupplierID = p.SupplierID
WHERE QuantityPerUnit LIKE '%bottles';
```
<b>1.4</b>
```
SELECT CategoryName AS 'Category Name', p.UnitsInStock AS 'Units In Stock'
FROM Categories c
JOIN Products p
ON p.CategoryID = c.CategoryID
ORDER BY 'Units In Stock' DESC;
```
<b>1.5</b>
```
SELECT TitleOfCourtesy AS 'Title of Courtesy', FirstName + ' ' + LastName AS 'Name', City
FROM Employees e
WHERE e.Country = 'UK'
```
<b>1.6</b>
```
Need to do
```
<b>1.7</b>
```
SELECT COUNT(*) AS 'Total Orders' FROM Orders o
WHERE ShipCountry = 'USA' AND Freight > 100
UNION
SELECT COUNT(*) AS 'Total Orders' FROM Orders o
WHERE ShipCountry = 'UK' AND Freight > 100
```
<b>1.8</b>
```
SELECT o.OrderID, od.Discount AS 'Total Discount'
FROM Orders o
JOIN [Order Details] od
ON o.OrderID = od.OrderID
WHERE 'Total Discount' IS NOT NULL
ORDER BY 'Total Discount' DESC;
```
## Exercise  2 - Northwind Queries
<b>2.1</b>
```
USE my_SQLProject

INSERT INTO Spartans
VALUES (1901, 'Adam', 'Smith', 38, 'BA-Test'),
(1902, 'John', 'Williams', 38, 'BA-Test'),
(1903, 'Nick', 'Willis', 38, 'BA-Test'),
(1904, 'Jenny', 'Jones', 38, 'BA-Test'),
(1905, 'Katie', 'Prince', 38, 'BA-Test'),
(1906, 'Peter', 'Brown', 38, 'BA-Test'),
(2101, 'Mo', 'Khan', 42, 'Engineering'),
(2102, 'Juan', 'Karlos', 42, 'Engineering'),
(2103, 'Jan', 'Miller', 42, 'Engineering'),
(2104, 'Kyle', 'Carpenter', 42, 'Engineering'),
(2105, 'Alvarao', 'Carlos', 42, 'Engineering'),
(2106, 'Margaret', 'Baker', 42, 'Engineering'),
(2107, 'Oti', 'Mwase', 42, 'Engineering');

INSERT INTO CourseDetails
VALUES (38, 356, 'BA-Test', 1901, 'Adam', 'Smith', '2018-01-15', '2018-03-02'),
(38, 356, 'BA-Test', 1902, 'John', 'Williams', '2018-01-15', '2018-03-02'),
(38, 356, 'BA-Test', 1903, 'Nick', 'Willis', '2018-01-15', '2018-03-02'),
(38, 356, 'BA-Test', 1904, 'Jenny', 'Jones','2018-01-15', '2018-03-02'),
(38, 356, 'BA-Test', 1905, 'Katie', 'Prince','2018-01-15', '2018-03-02'),
(38, 356, 'BA-Test', 1906, 'Peter', 'Brown', '2018-01-15', '2018-03-02'),
(42, 322, 'Engineering', 2101, 'Mo', 'Khan', '2018-01-15', '2018-03-03'),
(42, 322, 'Engineering', 2102, 'Juan', 'Karlos', '2018-01-15', '2018-03-03'),
(42, 322, 'Engineering', 2103, 'Jan', 'Miller', '2018-01-15', '2018-03-03'),
(42, 322, 'Engineering', 2104, 'Kyle', 'Carpenter', '2018-01-15', '2018-03-03'),
(42, 322, 'Engineering', 2105, 'Alvarao', 'Carlos','2018-01-15', '2018-03-03'),
(42, 322, 'Engineering', 2106, 'Margaret', 'Baker', '2018-01-15', '2018-03-03'),
(42, 322, 'Engineering', 2107, 'Oti', 'Mwase', '2018-01-15', '2018-03-03');

INSERT INTO Course
VALUES ('BA-Test', 38, 1, 356),
('Engineering', 42, 3, 322);

INSERT INTO Room
VALUES (1, 38, 'BA-Test'),
(3, 42, 'Engineering');

INSERT INTO Trainer
VALUES (356, 'Tim', 'Cawte'),
(322, 'Richard', 'Gurney');

INSERT INTO Duration
VALUES ('2018-01-15', '2018-03-02', 'BA-Test', 38),
('2018-01-15', '2018-03-03', 'Engineering', 42);

INSERT INTO Academy
VALUES ('Richmond', 356, 'Tim', 'Cawte', 'BA-Test', 38),
('Richmond', 322, 'Richard', 'Gurney', 'Engineering', 42);
```
