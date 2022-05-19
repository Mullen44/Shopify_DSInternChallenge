# Shopy_DSInternChallenge

Fall 2022 Data Science Intern Challenge 

Please complete the following questions, and provide your thought process/work. You can attach your work in a text file, link, etc. on the application page. Please ensure answers are easily visible for reviewers!


Question 1: Given some sample data, write a program to answer the following: click here to access the required data set

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 

Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 
What metric would you report for this dataset?
What is its value?


## Q1 Answer
a. Think about what could be going wrong with our calculation. Think about a better way to evaluate this data.
- AOV is the mean of the dollar amount of each order.  Taking the mean of a dataset leaves the result susceptible to outliers.  To better evaluate the data I would seek to better understand the dataset first through visualizations and then try a value that is less susceptible to outlier influence.

b. What metric would you report for this dataset?
- The metric I would report for this dataset would be the median order value as at this value 50% of the customers have a lower order amount and 50% have a higher order amount.

c. What is its value?
- Median Order Value = 284.00

##### Link to Jupyter Notebook: https://github.com/Mullen44/Shopy_DSInternChallenge/blob/main/DS_Challenge_Q1.ipynb

Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

LINK: https://www.w3schools.com/SQL/TRYSQL.ASP?FILENAME=TRYSQL_SELECT_ALL

## Q2 Answer

a. How many orders were shipped by Speedy Express in total?

SELECT COUNT(OrderID)
FROM (SELECT * FROM Orders
LEFT JOIN Shippers
ON Shippers.ShipperID = Orders.ShipperID)

WHERE Shippers.ShipperName IN ('Speedy Express');

Answer =  54

b. What is the last name of the employee with the most orders?

SELECT TOP 1 Employees.LastName, COUNT(Orders.OrderID)
FROM Orders
LEFT JOIN Employees
ON Employees.EmployeeID = Orders.EmployeeID
GROUP BY Employees.LastName
ORDER BY COUNT(Orders.OrderID) DESC;

Answer = Peacock

c. What product was ordered the most by customers in Germany

SELECT TOP 1 Products.ProductName, SUM(OrderDetails.Quantity)
FROM (((Customers
INNER JOIN Orders ON Customers.CustomerID = Orders.CustomerID)
INNER JOIN OrderDetails ON Orders.OrderID = OrderDetails.OrderID)
INNER JOIN Products ON OrderDetails.ProductID = Products.ProductID)
WHERE Customers.Country='Germany'
GROUP BY Products.ProductName
ORDER BY SUM(OrderDetails.Quantity) DESC;

Boston Crab Meat —> 160

#### Link to Txt File: https://github.com/Mullen44/Shopy_DSInternChallenge/blob/main/DS_Challenge_Q2.txt

