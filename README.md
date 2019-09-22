# SQL Practical Exercise

## Exercise  1 - Northwind Queries
<b>1.1</b>
```
SELECT CustomerID AS 'Customer ID', CompanyName AS 'Company Name', ContactName AS 'Contact Name',
ContactTitle AS 'Contact Title', Address, City, Region, PostalCode AS 'Postal Code', Country, Phone, Fax
FROM Customers
WHERE City = 'London' OR City = 'Paris';
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
WHERE e.Country = 'UK';
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
HAVING ROUND(SUM((od.UnitPrice*od.Quantity)*(1-od.Discount)),1) > 1000000;
```
<b>1.7</b>
```
SELECT COUNT(*) AS 'Total Orders with Freight greater than 100'
FROM Orders
WHERE ShipCountry = 'USA' OR ShipCountry = 'UK'
AND Freight > 100.00;
```
<b>1.8</b>
```
SELECT TOP 1 OrderID AS 'Order number with the highest amount of discount applied', Discount
FROM [Order Details]
ORDER BY Discount DESC;
```
## Exercise  2 - Create Database Schema
<b>2.1</b>
```
Table 1
CREATE TABLE SpartanInfo
(
SpartanID INT PRIMARY KEY,
SpartanFName VARCHAR(30),
SpartanLName VARCHAR(30),
CourseID INT
);

Table 2
CREATE TABLE TrainerthisTerm
(
TrainerID INT PRIMARY KEY,
TrainerFName VARCHAR(30),
TrainerLName VARCHAR(30),
CourseName VARCHAR(30)
);

Table 3
CREATE TABLE CourseInfo
(
CourseID INT PRIMARY KEY,
TrainerID INT,
CourseName VARCHAR(30),
StartDate DATE,
EndDate DATE,
Room INT
);

Table 4
CREATE TABLE RoomInfo
(
RoomID CHAR(2) PRIMARY KEY,
Room INT,
CourseID INT,
AcadameyID CHAR(3),
CourseName VARCHAR(30),
Capacity INT,
);

Table 5
CREATE TABLE CourseDuration
(
CourseID INT PRIMARY KEY,
CourseName VARCHAR(30),
StartDate DATE,
EndDate DATE
);

Table 6
CREATE TABLE AcademyInfo
(
AcademyID CHAR(3) PRIMARY KEY,
AcademyName VARCHAR(10)
);

Table 7
CREATE TABLE Employees
(
EmployeeID INT PRIMARY KEY,
EmployeeFame VARCHAR(30),
EmployeeLName VARCHAR(30),
StartDate DATE,
Position VARCHAR (30),
);
```
<b>2.2 </b>

```
INSERT INTO SpartanInfo
VALUES (1901, 'Adam', 'Smith', 38),
(1902, 'John', 'Williams', 38),
(1903, 'Nick', 'Willis', 38),
(1904, 'Jenny', 'Jones', 38),
(1905, 'Katie', 'Prince', 38),
(1906, 'Peter', 'Brown', 38),
(2101, 'Mo', 'Khan', 42),
(2102, 'Juan', 'Karlos', 42),
(2103, 'Jan', 'Miller', 42),
(2104, 'Kyle', 'Carpenter', 42),
(2105, 'Alvarao', 'Carlos', 42),
(2106, 'Margaret', 'Baker', 42),
(2107, 'Oti', 'Mwase', 42);

INSERT INTO TrainerthisTerm
VALUES (356, 'Tim', 'Cawte', 'BA-Test'),
(322, 'Richard', 'Gurney', 'Engineering');

INSERT INTO CourseInfo
VALUES (38, 356,'BA-Test', '2018-01-15', '2018-03-02', 1),
 (42, 322, 'Engineering', '2018-01-22', '2018-03-03', 3);

INSERT INTO RoomInfo
VALUES (1, 38, 'RA1', 'BA-Test', 25),
(3, 42, 'RA1', 'Engineering', 25);

INSERT INTO CourseDuration
VALUES (38, 'BA-Test', '2018-01-15', '2018-03-02'),
(42, 'Engineering', '2018-01-22', '2018-03-03');

INSERT INTO AcademyInfo
VALUES ('RA1', 'Richmond'),
('RA1','Richmond');

INSERT INTO Employees
VALUES (356, 'Tim', 'Cawte', 'BA-Test', '2018-01-15', 'Trainer'),
(322, 'Richard', 'Gurney', 'Engineering', '2018-01-22', 'Trainer');
```
<b>2.3</b>

ADDING CURRENT SPARTANS IN DEVOPS
```
INSERT INTO SpartanInfo
VALUES
(2108, 'Ben', 'Morgan', 42),
(2109, 'Sharik', 'Gurung', 42),
(2110, 'Sam', 'Forrester', 42),
(2111, 'David', 'Naim', 42),
(2112, 'Lennox', 'Bampoe-Addo', 42),
(2113, 'Sivaharan', 'Thevipagan', 42),
(2114, 'Vinuzan', 'Ratnasingam', 42),
(2115, 'Abror', 'Ilkhamov', 42),
(2116, 'Rory', 'Stokes', 42),
(2117, 'Miles', 'Eastwood', 42),
(2118, 'Jack', 'Wallace', 42),
(2119, 'Vishnu', 'Jeyarathnam', 42),
(2120, 'Moustapha', 'Akanmu', 42);
```
ADDING CURRENT TRAINERS IN SPARTA
```
INSERT INTO TrainerInfo
VALUES (348, 'Filipe', 'Paiva', 'Engineering'),
(316, 'Jonathan', 'Clarke', 'BA-Test');
```
ADDING A TRAINING ASSISTANT
```
INSERT INTO Employees
VALUES (399, 'Astha', 'Shaw', 'BA-Test', '2018-01-15', 'Training Assistant');
```

## Exercise  3 - Write SELECT statements for all of the following:
<b>3.1</b>

```
SELECT ttt.TrainerFName + ' ' + ttt.TrainerLName AS 'Trainer Name',
ci.CourseName AS 'Course', cd.StartDate AS 'Start Date', cd.EndDate AS 'End Date',
ri.Room, si.SpartanFName + ' ' + si.SpartanLName AS 'Spartan',
ai.AcademyName AS 'Academy Name'
FROM TrainerthisTerm ttt
JOIN CourseInfo ci
ON ci.CourseName = ttt.CourseName
JOIN CourseDuration cd
ON cd.CourseID = ci.CourseID
JOIN RoomInfo ri
ON ci.Room = ri.Room
JOIN SpartanInfo si
ON si.CourseID = ci.CourseID
JOIN AcademyInfo ai
ON ai.AcademyID = ri.AcademyID;
```
<b>3.2</b>

```
SELECT ttt.TrainerFName + ' ' + ttt.TrainerLName AS 'Trainer Name',
ci.CourseName AS 'Course', cd.StartDate AS 'Start Date', cd.EndDate AS 'End Date',
ri.Room, LEFT(si.SpartanFName,1) + '.' + LEFT(si.SpartanLName,1)AS 'Spartan Initials',
ai.AcademyName AS 'Academy Name'
FROM TrainerthisTerm ttt
JOIN CourseInfo ci
ON ci.CourseName = ttt.CourseName
JOIN CourseDuration cd
ON cd.CourseID = ci.CourseID
JOIN RoomInfo ri
ON ci.Room = ri.Room
JOIN SpartanInfo si
ON si.CourseID = ci.CourseID
JOIN AcademyInfo ai
ON ai.AcademyID = ri.AcademyID
```
<b>3.3</b>

```
ALTER TABLE CourseDuration
	ADD [Check Date] DATE

UPDATE CourseDuration
	SET [Check Date] = DATEADD(MM,2,EndDate)
	WHERE CourseID=38

UPDATE CourseDuration
	SET [Check Date] = DATEADD(mm,3,EndDate)
	WHERE CourseID=42
```
## Exercise  4 - Add Constraints
<b>4.1</b>

```
ALTER TABLE CourseInfo
ADD FOREIGN KEY (TrainerID)
REFERENCES TrainerthisTerm(TrainerID);
```
<b>4.2</b>

```
CREATE TABLE RoomInfo
(
RoomID CHAR(2) PRIMARY KEY,
Room INT,
CourseID INT,
AcadameyID CHAR(3),
CourseName VARCHAR(30),
Capacity INT,
);

INSERT INTO RoomInfo
VALUES (1, 38, 'RA1', 'BA-Test', 25),
(3, 42, 'RA1', 'Engineering', 25);
```
