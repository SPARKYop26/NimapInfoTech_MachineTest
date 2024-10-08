# NimapInfoTech_MachineTest

This project is a RESTful web service built using Spring Boot, JPA, Hibernate, and MySQL. It provides CRUD operations for managing Categories and Products, along with server-side pagination. Categories and Products have a one-to-many relationship, with one category having multiple products.

# Features
Category Management: Create, Read, Update, Delete (CRUD) operations.
Product Management: Create, Read, Update, Delete (CRUD) operations.
One-to-Many Relationship: Categories can have multiple products.
Server-Side Pagination: Efficiently fetch paginated data from the server.
REST API: The project exposes REST endpoints to perform operations.

# Technologies Used
Spring Boot: Framework for building the application.
Spring Data JPA: For interacting with the database.
Hibernate: ORM tool for managing database entities.
MySQL: Relational database for storing data.
Maven: Project management and dependency management.
Java 17: Programming language used for development.

# Prerequisites
JDK 17 or higher.
Maven 3.8.x or higher.
MySQL 8.0 or higher.
IDE such as IntelliJ IDEA or Eclipse.
Postman (optional, for API testing).
Database Configuration
The project uses MySQL as the database. Before running the application, configure the database connection in application.properties:

# Database Configuration and Hibernate Configuration
spring.application.name=ShopApp

server.port=8080

spring.datasource.url= jdbc:mysql://localhost:3306/shop
spring.datasource.username=root
spring.datasource.password=Kccemsr@123
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver


spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.show-sql=true

spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.MySQL8Dialect
Replace your_database_name, your_username, and your_password with your actual MySQL database details.

# Running the Application
Clone the repository or download the source code.
Configure the MySQL database and update the application.properties file as mentioned in the Database Configuration section.
Run the application using Maven.
mvn spring-boot:run
The application will start at http://localhost:8080.

# REST API Endpoints
# Category APIs

GET All Categories with Pagination:
GET /api/categories?page={id}
Example: http://localhost:8080/api/categories?page=0

POST Create a New Category:
POST /api/categories
Example: http://localhost:8080/api/categories
Body (JSON):
{
    "name": "Electronics",
    "description": "Mobiles and Laptops"
}

GET Category by ID:
GET /api/categories/{id}
Example: http://localhost:8080/api/categories/1

PUT Update a Category by ID:
PUT /api/categories/{id}
Example: http://localhost:8080/api/categories/1
Body (JSON):
{
    "name": "Updated category name",
    "description": "Add description"
}

DELETE Delete a Category by ID:
DELETE /api/categories/{id}
Example: http://localhost:8080/api/categories/1

# Product APIs

GET All Products with Pagination:
GET /api/products?page={id}
Example: http://localhost:8080/api/products?page=0

POST Create a New Product:
POST /api/products
Example: http://localhost:8080/api/products
Body (JSON):
{
    "name": "burger",
    "category": {
        "id": 11
    },
    "price": 250,
    "description": "extra cheese"
}


GET Product by ID:
GET /api/products/{id}
Example: http://localhost:8080/api/products/1

PUT Update a Product by ID:
PUT /api/products/{id}
Example: http://localhost:8080/api/products/3
Body (JSON):
{
    "name": "pasta",
    "description": "creamy and cheese",
    "price": 200
}

DELETE Delete a Product by ID:
DELETE /api/products/{id}
Example: http://localhost:8080/api/products/1

# One-to-Many Relationship (Category-Products)
Each Category can have multiple Products.
When fetching a product by its ID, the corresponding category details will also be included.

# Pagination
Server-side pagination is implemented using Pageable and PageRequest in Spring Data JPA.
You can pass page and size parameters in the API to fetch paginated data.
