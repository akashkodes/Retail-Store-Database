# Retail-Store-Database!


The retail database is designed to hold the information of a retail store. It holds customer information, various types of products and employees table.
The entities in the database are as follows:

1) Customers:  It has all the customer information
2) Products : It has all the product information
3) Employees : It has all the employees information
4) Orders: It contains order details
5) Order_items: This is a bridging table to accommodate multiple products in single order
6) Payment_details: This is confidential information of customer’s credit/debits cards
7) Reviews: It contains comments made by verified customers on products
8) Offers: Special promotional offers available on selected products
9) Addresses: It is a bridging table to accommodate various customer’s addresses
10) Service: It collects data of customers and employee responsible to help the customers
11) Service_review: This is a feedback collection of services given to customers
12) Area_Codes: It contains codes of areas of where employees work
13) Departments: It contains information of employee’s departments
14) Security Clearance: It ensures that only authorized employees have access to confidential data

The database ensures that at every stage feedback is taken from customers to improve customer satisfaction. To collect this information I have a review table for product reviews and a service_review table to collect feedback given by the customers who contacted the service department for various reasons. The database will collect data from the online portal as well as from the retail stores available. The data won’t be separate but rather kept together as it is expected that for initial few years online traffic for retail or grocery shopping is not a lot.

Mission Statement:

The mission of the retail database is to provide a comprehensive and efficient solution for managing the information of a retail store. The database aims to facilitate the organization and retrieval of customer information, product data, employee records, order details, payment information, reviews, offers, addresses, service data, service reviews, area codes, and departments. Through accurate and accessible data, we strive to enable our users to make informed decisions, improve operational efficiency, and enhance customer satisfaction. The goal is to maintain a reliable and user-friendly database that supports the success of the retail store by delivering high-quality service and maximizing profitability.


Objectives:
1) To provide an organized and efficient system for managing customer information, including contact details and purchase history, to help improve customer service and sales.
2) To maintain an accurate and up-to-date record of products, including inventory levels, prices, and descriptions, to facilitate easy ordering, restocking, and sales tracking.
3) To enable effective employee management by keeping track of employee details, including contact information, employment history, and performance metrics.
4) To facilitate the ordering and processing of customer orders, including the ability to track order status and generate invoices and receipts.
5) To maintain a detailed record of order items, including product details, quantities, and prices, to help with inventory management and sales tracking.
6) To keep track of payment details, including payment method, amount, and date, to ensure accurate accounting and financial reporting.
7) To enable customers to submit product reviews and ratings, providing valuable feedback for product improvement and marketing purposes.
8) To provide a system for creating and managing special offers and promotions, helping to increase sales and customer loyalty.

Business Rules:
1) Customers can exist in the customer table even if they haven’t order anything
2) Products can exist in the product table even if they are not purchased
3) One order id can have only one payment id
4) Only customers who have bought a product can review the product
5) It is possible that various products from single order are delivered on different dates
6) Payment details should be confidential
7) Employees should have different clearance levels to access confidential information
8) One customer can have multiple addresses and should be classified as home, office or other.

![retail erd](https://user-images.githubusercontent.com/128107742/229370328-747272d4-6204-44dd-aad2-0c385eeaf0c5.png)

Data Dictionary Table: (PK = primary keys, FK = foreign keys, idx = indexes)
| Table Name | Column Name | Data Type | Default Value | Nullable
| --------- | ------------| ---------- | ---------| -------- |
customers	| cust_id (PK) (idx) |	int(11) | | N |
| | cust_fname (idx)|	varchar(45)	| | N |
| | cust_lname(idx)	| varchar(45) |	null |	Y |
| | cust_dob |	date	| |	N |
| | cust_email |	varchar(45) |	null |	Y |
| | cust_username |	varchar(45) |	null |	Y |
| | cust_contact_number |	varchar(13)	| |	N |
| products|	prod_id (PK) (Auto Generated)	| int(11)	| |	N |
| | prod_name	| varchar(45)	| |	N |
| | prod_category	| varchar(45)	| null |	Y |
| | prod_price	| varchar(45)	| null |	Y |
| | prod_color |	varchar(45) |	null	| Y |
| | prod_weight	| varchar(45) |	null |	Y |
| employees	| emp_id (PK) idx	| int(11) |	 |	N |
|	| emp_area_code (FK) idx | int(11) |	|	N |
| |	emp_dept_id (FK) idx	| int(11)	| |	N |
|	| emp_clearance_id (FK) idx |	int(11)	| |	N |
|	| emp_fname	| varchar(45)	|	| N |
| |	emp_lname	| varchar(45)	| null | Y |
| |	emp_dob	| varchar(45)	| | 	N |
| |	emp_email_id	| varchar(45)	| |	Y |
| |	emp_contact_number	| varchar(45)	| |	Y |
| |	emp_preferred_name |	varchar(45)	| null |	Y |
| |	emp_designation	| varchar(45)	| |	N |
| |	emp_joining_date |	date	| null	| N |
| |	emp_status |	enum(0,1) |	0 |	N |
| addresses	| address_id (PK) idx	| int(11) | |		N |
| |	add_cust_id (FK) idx |	int(11)	| |	N |
| |	address_type idx	| enum(home,office,other)	| other	| Y |
| |	cust_street_address	| varchar(45)	| |	N |
| |	cust_city	| varchar(45)	|	| N |
| |	cust_state	| varchar(45)	| |	N |
| |	cust_zipcode	| varchar(45)	| |	N |
| |	cust_country |	varchar(45)	| |	N |
| offers | offer_id (PK) idx | int(11) |  | N | 
| | offer_prod_id (FK) idx | int(11) |  | N | 
| | offer_code | varchar(45) | null | Y | 
| | offer_start_date | date | null | Y | 
| | offer_end_date | date | null | Y | 
| | offer_type | varchar(45) | null | Y | 
| | offer_policy | varchar(45) | null | Y | 
| | offer_limit | varchar(45) | null | Y | 
| | active | enum(0,1) | 0 | Y | 
| reviews | review_id (PK) idx | int(11) |  | N | 
| | review_prod_id (FK) idx | int(11) |  | N | 
| | review_cust_id (FK) idx | int(11) |  | N | 
| | comment | varchar(300) |  | N | 
| | review_date | datetime |  | N | 
| service_reviews | service_review_id (PK) idx | int(11) |  | N | 
| | service_review_serv_id (FK) idx | int(11) |  | N | 
| | rating | enum( 1 to 10) |  | N | 
| | title | varchar(45) | null | Y | 
| | comments | varchar(300) | null | Y | 
| | serv_review_date | datetime |  | N |
| orders | orders_id (PK) idx | int(11) |  | N | 
| | orders_cust_id (FK) idx | int(11) |  | N | 
| | payment_id (FK) idx | int(11) |  | N | 
| | order_date | date |  | N | 
| | order_amount | decimal(8,2) |  | N | 
| | shipping_address | varchar(45) |  | N | 
| | shipping_city | varchar(45) |  | N | 
| | shipping_state | varchar(45) |  | N | 
| | shipping_zip_code | varchar(45) |  | N | 
| payment_detais | payment_id(PK) idx | int(11) |  | N | 
| | cust_id(FK) idx | int(11) |  | N | 
| | card_number | varchar(45) |  | N | 
| | card_type | varchar(45) | null | Y | 
| | cardholder_name | varchar(45) |  | N | 
| | card_cvv | varchar(45) |  | N | 
| | card_expiry_date | varchar(45) |  | N | 
| | payment_type | varchar(45) | null | Y | 
| | payment_datetime | datetime |  | N | 
| order_item | order_item_id(PK) idx | int(11) |  | N | 
| | order_item_prod_id(FK) idx | int(11) |  | N | 
| | order_item_cust_id(FK)idx | int(11) |  | N | 
| | order_item_order_id(FK)idx | int(11) |  | N | 
| | order_item_delivery_date | date | null | Y | 
| service | service_id(PK) idx | int(11) |  | N | 
| | serv_cust_id(FK) idx | int(11) |  | N | 
| | serv_emp_id(FK) idx | int(11) |  | N | 
| | serv_type | varchar(45) |  | Y | 
| | serv_status | ENUM('active', 'closed', 'pending', 'terminated') |  | N | 
| | serv_start_date | datetime |  | N | 
| | serv_end_date | datetime |  | Y | 
| area_code | area_id(PK) | int(11) |  | N | 
| | area_code | varchar(45) |  | N | 
| | area_name | varchar(45) |  | N | 
| | area_street_address | varchar(45) |  | N | 
| | area_city | varchar(45) |  | N | 
| | area_state | varchar(45) |  | N | 
| | area_zip_code | varchar(45) |  | N | 
| departments | dept_id(PK) | int(11) |  | N | 
| | dept_name | varchar(45) |  | N | 
| | dept_domain | varchar(45) | null | Y | 
| | dept_head | varchar(45) |  | N | 
| | dept_desc | varchar(45) | null | Y | 
| security_clearance | clearance_id idx | int(11) |  | N | 
| | clearance_level | varchar(45) |  | N | 
| | desc | varchar(45) |  | N | 
