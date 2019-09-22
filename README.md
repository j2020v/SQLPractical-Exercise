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
SELECT ROUND(SUM((od.UnitPrice*od.Quantity)*(1-od.Discount)),1) AS 'Total Sales',
r.RegionDescription 'Region'
FROM [Order Details] od
JOIN Orders o
ON o.OrderID = od.Discount
JOIN EmployeeTerritories et
ON et.EmployeeID = o.EmployeeID
JOIN Territories t
ON t.TerritoryID = et.TerritoryID
JOIN Region r
ON t.RegionID = r.RegionID
GROUP BY r.RegionDescription
HAVING ROUND(SUM((od.UnitPrice*od.Quantity)*(1-od.Discount)),1) > 1000000
```
<b>1.7</b>
```
SELECT COUNT(*) AS 'Total Orders with Freight greater than 100'
FROM Orders
WHERE ShipCountry = 'USA' OR ShipCountry = 'UK'
AND Freight > 100.00
```
<b>1.8</b>
```
SELECT TOP 1 o.OrderID, od.Discount AS 'Total Discount'
FROM Orders o
JOIN [Order Details] od
ON o.OrderID = od.OrderID
WHERE 'Total Discount' IS NOT NULL
ORDER BY 'Total Discount' DESC;
```
## Exercise  2 - Create Database Schema
<b>2.1</b>
