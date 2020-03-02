# Products and Customers

Products and Customers is a simple web application that manages the products a vendor or distributor has under use by customers, and also manages the customers using those products

# Installation
This is a Maven/Spring Boot project with default WAR settings

Spring Boot will populate your MySQL file.  Just create the file and if different, change in the application.properties file


[comment]: # (mvn spring-boot:run)


# Usage

Vendors/distributors can track their customers by product, and product by customers.  

To start, in the Product side, add the various products that are in use.  Fields are:  
  * Name
  * Model
  * List Price
  * Description

Next, on the Customer side, add the various customers.  Fields are:
  * Name (Corporate)
  * Contact Name
  * Contact Email
  * Location

Next, the relationship between customers and products can be populated on either side.  This shows which customers hava a product and which products are in use by a customer.  These fields are:
  * Purchase Date
  * Serial Number
Note:  this means that adding or deleting a product to/from a customer also means that customer was added or deleted to/from that product


## API Documentation

### Customer side:

GET:

api/customers:  Shows all customers

api/customers-number-of:  Shows number of customers

api/customers-ids:  Shows list of valid customer ids as an arrayList of Integers

api/customers/{customerId}:  Shows customer with specified customer ID and maybe their products

api/customers/{customerId}/products:  Shows customer with specified customer ID and all their products.  If customer does not exist, then returns null for customer fields

POST:

api/customers:  adds a single customer. Required fields: String name [min 3 char]; String location [min 3 char]; String contactName [min 3 char]; String contactEmail [valid email format]

api/customers/{customerId}/products/{productId}:  Adds product {productId} to customer {customerId}.  Required fields:  none.  Expected fields:  Date purchaseDate pattern = "yyyy-MM-dd", String serialNumber 

DELETE:

api/customers/{customerId}/products/{productId}: Deletes specified product from specified customer

api/customers/{customerId}:  Deletes specified customer

PUT:
api/customers/{customerId}:  Modifies fields of existing customer.  Required fields: String name [min 3 char]; String location [min 3 char]; String contactName [min 3 char]; String contactEmail [valid email format]


### Product side:

GET:

api/products:  Shows all products

api/products/{productId}/customers:  Shows product with specified product ID and all their customers.  If product does not exist, then returns null for product fields

POST:

api/products:  adds a single product.  Required fields:  String name [min 3 char]; String description [min 3 char]; Double listPrice; String modelNumber [min 3 char]

api/products/{productsId}/customers/{customerId}:  Adds customer {customerId} to product {productId}.  Required fields:  none.  Expected fields:  Date purchaseDate pattern = "yyyy-MM-dd", String serialNumber

PUT:

api/customers{id}: Modifies fields of existing product.  Required fields:  String name [min 3 char]; String description [min 3 char]; Double listPrice; String modelNumber [min 3 char]


DELETE:

api/products/{productId}/customers/{customersId}: Deletes specified customer from specified product

api/products/{productId}:  Deletes the specified product


## Selected JSP Screenshots:

![Image](readmeimages/home.png "Home Page")  
![Image](readmeimages/customers.png "Customers Overview")  
![Image](readmeimages/products.png "Products Overview")  
![Image](readmeimages/customer.png "Detail One Customer")  
![Image](readmeimages/product.png "Detail One Product")  
![Image](readmeimages/newproduct.png "Create New Product")  





# Potential Future Features:

  * Added form input flexibility
  * Search, sort, or pagination to accommodate long lists







