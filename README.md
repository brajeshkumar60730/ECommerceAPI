# ECommerceAPI
The ECommerceAPI is a software interface designed to facilitate e-commerce operations. It provides functionalities for managing various aspects of an online store, such as: Product Management, Order Management, Customer Management, Payment Processing, Cart Management, Authentication and Authorization, Reporting and Analytics
Creating an E-Commerce Application using ASP.NET Core Web API
Let us start by Creating an E-Commerce application using ASP.NET Core Web API and performing database operations using ADO.NET Core with T-SQL statements. This involves several steps, from designing the database, creating an ASP.NET Core Web API, and efficiently handling database operations.

Database Design For E-Commerce Application:
In our E-Commerce Application, we will use the following database tables.

Products Table: Stores information about products like ID, name, price, and quantity.
Customers Table: Contains customer details such as ID, name, and email.
Orders Table: Tracks each order, linking to the customer via a foreign key.
OrderItems Table: Details each item in an order, linking to the orders and products tables.
Payments Table: Records payment transactions, including the payment method and amount linked to orders.
Customers Table
It Stores information about customers. The meaning of the Columns is as follows:

CustomerId: The primary key that uniquely identifies each customer. It is auto-incremented.
Name: Stores the customer’s name.
Email: Stores the customer’s email address. It is unique across the table.
Address: Stores the customer’s address.
IsDeleted: A flag indicating whether the customer is considered deleted (logical delete rather than physical delete).
Relationships: Acts as the parent table for Orders, where CustomerId is referenced.

Products Table
It Contains details about products being sold. The meaning of the Columns of this table is as follows:

ProductId: The primary key uniquely identifies each product. It is auto-incremented.
Name: Product name, which is unique.
Price: The selling price of the product.
Quantity: The quantity of the product available in stock.
Description: A detailed description of the product.
IsDeleted: Indicates whether the product is considered deleted.
Relationships: Acts as the parent table for OrderItems, where ProductId is referenced.

Orders Table
It Stores records of customer orders. The meaning of the Columns of this table is as follows:

OrderId: The primary key uniquely identifies each order. It is auto-incremented.
CustomerId: Foreign key links to the Customers table, indicating which customer placed the order.
TotalAmount: The total monetary amount of the order.
Status: The current status of the order (e.g., Pending, Failed, Processing, Shipped, and Delivered).
OrderDate: The date and time the order was placed.
Relationships: Parent table for Payments and OrderItems.

Payments Table
This table Records details of payments made for orders. The meaning of the Columns of this table is as follows:

PaymentId: The primary key uniquely identifies each payment. It is auto-incremented.
OrderId: Foreign key referencing the Orders table, linking each payment to a specific order.
Amount: The amount of money paid.
Status: The payment status (e.g., Pending, Completed, Failed, or Refunded).
PaymentType: The payment method (e.g., CC, DC, COD).
PaymentDate: The date and time the payment was made.
Relationships: Links each payment to a specific order, establishing a many-to-one relationship with Orders.

OrderItems Table
It links products to orders, detailing which products are included in each order and in what quantity. The meaning of the Columns of this table is as follows:

OrderItemId: The primary key uniquely identifies each order item entry. It is auto-incremented.
OrderId: Foreign key that references the Orders table.
ProductId: Foreign key that references the Products table.
Quantity: The quantity of the product ordered.
PriceAtOrder: The PriceAtOrder field stores the product’s actual price at the time the order is made.
Relationships: Links to Orders and Products, establishing a many-to-one relationship with both (an order can contain multiple products, and a product can be in multiple orders).

Database Relationships Overview
Customers and Orders: One-to-many (one customer can have multiple orders).
Orders and Payments: One-to-one (one order can have one payment).
Orders and OrderItems: One-to-many (one order can contain multiple products).
Products and OrderItems: Many-to-many (products can appear in many orders, and orders can contain many products, mediated through the OrderItems table).
