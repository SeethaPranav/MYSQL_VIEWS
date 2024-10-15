# MYSQL_VIEWS
A concise guide on SQL views, demonstrating how to create, manage, and utilize them for simplified data access and enhanced security.Create a database named Product and create a table called Customer with the following fields in the Product database:Customer_Id - Make PRIMARY KEY First_name Last_name Email Phone_no Address City State Zip_code Country 

CREATE DATABASE Product;

USE Product;

CREATE TABLE Customer (
    Customer_Id INT PRIMARY KEY,
    First_name VARCHAR(50),
    Last_name VARCHAR(50),
    Email VARCHAR(100),
    Phone_no VARCHAR(15),
    Address VARCHAR(255),
    City VARCHAR(50),
    State VARCHAR(50),
    Zip_code VARCHAR(10),
    Country VARCHAR(50)
);

DESC Customer;

INSERT INTO Customer (Customer_Id, First_name, Last_name, Email, Phone_no, Address, City, State, Zip_code, Country)
VALUES 
    (1, 'John', 'Doe', 'john.doe@example.com', '123-456-7890', '123 Elm St', 'Springfield', 'IL', '62701', 'USA'),
    (2, 'Jane', 'Smith', 'jane.smith@example.com', '234-567-8901', '456 Oak St', 'Shelbyville', 'Ontario', '62565', 'USA'),
    (3, 'Alice', 'Johnson', 'alice.johnson@example.com', '345-678-9012', '789 Pine St', 'Capitol City', 'IL', '62704', 'USA'),
    (4, 'Bob', 'Brown', 'bob.brown@example.com', '456-789-0123', '101 Maple St', 'Springfield', 'England', '62701', 'USA'),
    (5, 'Carol', 'Davis', 'carol.davis@example.com', '567-890-1234', '202 Birch St', 'Champaign', 'CA', '61820', 'USA'),
    (6, 'David', 'Wilson', 'david.wilson@example.com', '678-901-2345', '303 Cedar St', 'Peoria', 'England', '61602', 'USA'),
    (7, 'Eva', 'Clark', 'eva.clark@example.com', '789-012-3456', '404 Spruce St', 'Joliet', 'NSW', '60431', 'USA'),
    (8, 'Frank', 'Lewis', 'frank.lewis@example.com', '890-123-4567', '505 Redwood St', 'Aurora', 'IL', '60506', 'USA'),
    (9, 'Grace', 'Walker', 'grace.walker@example.com', '901-234-5678', '606 Ash St', 'Naperville', 'Berlin', '60540', 'USA'),
    (10, 'Henry', 'Adams', 'henry.adams@example.com', '012-345-6789', '707 Hickory St', 'Bloomington', 'AZ', '61701', 'USA');
    
SELECT * FROM Customer;

#1. Create a view named customer_info for the Customer table that displays Customer’s Full name and email address.Then perform the SELECT operation for the customer_info view. 

CREATE VIEW customer_info AS

SELECT CONCAT(First_name, ' ', Last_name) AS Full_Name, Email FROM Customer;

SELECT * FROM customer_info;

![image](https://github.com/user-attachments/assets/384d36d4-2a88-415f-bb61-2a451ae5e0c6)

#2. Create a view named US_Customers that displays customers located in the US. 

CREATE VIEW US_Customers AS

SELECT * FROM Customer WHERE Country = 'USA';

SELECT * FROM US_Customers;

![image](https://github.com/user-attachments/assets/a26a36f5-a7f7-4143-857a-7b08d91e09a8)

#3. Create another view named Customer_details with columns full name(Combine first_name and last_name), email, phone_no, and state.

CREATE VIEW Customer_details AS

SELECT CONCAT(First_name, ' ', Last_name) AS Full_Name,Email,Phone_no,State FROM Customer;

SELECT * FROM Customer_details;

![image](https://github.com/user-attachments/assets/e9d7c9ce-3b23-43da-b642-4fa4a9984c86)
 
#4. Update phone numbers of customers who live in England for Customer_details view. 

UPDATE Customer_details SET Phone_No = 1111111111 WHERE State = 'England';

SELECT * FROM Customer_details;

![image](https://github.com/user-attachments/assets/c4fb0bc0-909d-491c-be30-b5a52b2de0fc)

#5. Count the number of customers in each state and show only states with more than 2 customers.

SELECT State, COUNT(*) AS Customer_Count FROM Customer GROUP BY State HAVING Customer_Count >=2;

![image](https://github.com/user-attachments/assets/3be9cfa9-029d-46fa-a950-94273db2d83d)

#6. Write a query that will return the number of customers in each state, based on the "state" column in the "customer_details" view.

SELECT State, COUNT(*) AS Customer_Count FROM Customer_details GROUP BY State;

![image](https://github.com/user-attachments/assets/ce61abd6-9e61-44e6-adc8-2c93c00ee320)

#7. Write a query that returns all the columns from the "customer_details" view, sorted by the "state" column in ascending order.

SELECT * FROM Customer_details ORDER BY State ASC;

![image](https://github.com/user-attachments/assets/a2edf7ed-5129-4138-b7cb-cfb3186fce0b)


