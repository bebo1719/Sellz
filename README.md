# Sellz

Description
Sellz is a back-end application for managing an e-commerce platform, designed to handle the core functionalities of an online store. It provides API endpoints to manage product listings, categories, and tags, and includes functionality to handle associations between products and tags. Sellz uses Node.js, Express.js, PostgreSQL, and Sequelize to deliver a RESTful API for efficient product management.

This back-end service supports the creation, updating, deletion, and querying of product data, categories, and tags. It also allows the association of tags with products for more effective organization.

Table of Contents
Installation
Usage
API Endpoints
Categories Routes
Products Routes
Tags Routes
Schema
Walkthrough
License
Installation
Clone the repository:

bash
Copy code
git clone https://github.com/yourusername/sellz-backend.git
Navigate to the project directory:

bash
Copy code
cd sellz-backend
Install dependencies:

bash
Copy code
npm install
Set up the PostgreSQL database:

Create a .env file at the root of the project with the following content:
bash
Copy code
DB_NAME=sellz_db
DB_USER=your_postgres_username
DB_PASSWORD=your_postgres_password
DB_HOST=localhost
DB_PORT=5432
Ensure PostgreSQL is running and create the database using the PostgreSQL shell:
bash
Copy code
createdb sellz_db
Run Sequelize migrations to create the database schema:

bash
Copy code
npx sequelize db:migrate
Seed the database (optional):

bash
Copy code
npx sequelize db:seed:all
Usage
Start the server:

bash
Copy code
npm start
The server will start on http://localhost:3001.

Development mode (with live-reload using nodemon):

bash
Copy code
npm run dev
Use Insomnia or Postman to test the API endpoints.

API Endpoints
Categories Routes
GET /api/categories

Get all categories with associated products.
GET /api/categories/:id

Get a single category by id with associated products.
POST /api/categories

Create a new category.
Request body:
json
Copy code
{
  "category_name": "New Category"
}
PUT /api/categories/:id

Update a category by id.
Request body:
json
Copy code
{
  "category_name": "Updated Category"
}
DELETE /api/categories/:id

Delete a category by id.
Products Routes
GET /api/products

Get all products with associated categories and tags.
GET /api/products/:id

Get a single product by id with associated categories and tags.
POST /api/products

Create a new product.
Request body:
json
Copy code
{
  "product_name": "New Product",
  "price": 49.99,
  "stock": 20,
  "category_id": 1,
  "tagIds": [1, 2]
}
PUT /api/products/:id

Update a product by id.
Request body:
json
Copy code
{
  "product_name": "Updated Product",
  "price": 59.99,
  "stock": 15,
  "tagIds": [1, 3]
}
DELETE /api/products/:id

Delete a product by id.
Tags Routes
GET /api/tags

Get all tags with associated products.
GET /api/tags/:id

Get a single tag by id with associated products.
POST /api/tags

Create a new tag.
Request body:
json
Copy code
{
  "tag_name": "New Tag"
}
PUT /api/tags/:id

Update a tag by id.
Request body:
json
Copy code
{
  "tag_name": "Updated Tag"
}
DELETE /api/tags/:id

Delete a tag by id.
Schema
The database schema consists of four models: Category, Product, Tag, and ProductTag. Below is an overview of the table structures:

Category
id: Integer, primary key, auto-increment.
category_name: String, not null.
Product
id: Integer, primary key, auto-increment.
product_name: String, not null.
price: Decimal, not null.
stock: Integer, not null, default value 10.
category_id: Integer, references Category model's id.
Tag
id: Integer, primary key, auto-increment.
tag_name: String.
ProductTag
id: Integer, primary key, auto-increment.
product_id: Integer, references Product model's id.
tag_id: Integer, references Tag model's id.
Walkthrough
Creating the Schema: Run the following command in the PostgreSQL shell to create the schema:

bash
Copy code
npx sequelize db:migrate
Seeding the Database: Use this command to populate the database with seed data:

bash
Copy code
npx sequelize db:seed:all
Starting the Server: Run the application using:

bash
Copy code
npm start
Testing API Routes: Use Insomnia or Postman to send requests to the endpoints described above for managing categories, products, and tags.

License
This project is licensed under the MIT License. See the LICENSE file for details.


<video src=""></video>