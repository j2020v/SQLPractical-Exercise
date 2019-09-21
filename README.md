# SQL Practical Exercise

## Exercise  1 - Northwind Queries
<b>1.1</b> SELECT CustomerID AS 'Customer ID', CompanyName AS 'Company Name', ContactName AS 'Contact Name',
ContactTitle AS 'Contact Title', Address, City, Region, PostalCode AS 'Postal Code', Country, Phone, Fax
FROM Customers
WHERE City = 'London' OR City = 'Paris'

<b>1.2</b> SELECT ProductID AS 'Product ID', ProductName AS 'Product Name', SupplierID AS 'Supplier ID',
CategoryID AS 'Category ID', QuantityPerUnit AS 'Quantity Per Unit', UnitPrice AS 'Unit Price',
UnitsInStock AS 'Units In Stock', UnitsOnOrder AS 'Units On Order', ReorderLevel AS 'Reorder Level', Discontinued
FROM Products
WHERE QuantityPerUnit LIKE '%bottles';

<b>1.3</b> SELECT s.CompanyName AS 'Company Name', s.Country, ProductID AS 'Product ID', ProductName AS 'Product Name',
p.SupplierID AS 'Supplier ID', CategoryID AS 'Category ID', QuantityPerUnit AS 'Quantity Per Unit',
UnitPrice AS 'Unit Price', UnitsInStock AS 'Units In Stock', UnitsOnOrder AS 'Units On Order', ReorderLevel AS 'Reorder Level', Discontinued
FROM Products p
JOIN Suppliers s
ON s.SupplierID = p.SupplierID
WHERE QuantityPerUnit LIKE '%bottles';

<b>1.4</b> SELECT CategoryName AS 'Category Name', p.UnitsInStock AS 'Units In Stock'
FROM Categories c
JOIN Products p
ON p.CategoryID = c.CategoryID
ORDER BY 'Units In Stock' DESC;

<b>1.5</b> SELECT TitleOfCourtesy AS 'Title of Courtesy', FirstName + ' ' + LastName AS 'Name', City
FROM Employees e
WHERE e.Country = 'UK'

</b>1.6</b>


<b>1.7</b> SELECT COUNT(* ) AS 'Total Orders' FROM Orders o
WHERE ShipCountry = 'USA' AND Freight > 100
UNION
SELECT COUNT(* ) AS 'Total Orders' FROM Orders o
WHERE ShipCountry = 'UK' AND Freight > 100

<b>1.8</b> SELECT o.OrderID, od.Discount AS 'Total Discount'
FROM Orders o
JOIN [Order Details] od
ON o.OrderID = od.OrderID
WHERE 'Total Discount' IS NOT NULL
ORDER BY 'Total Discount' DESC;