# Introduction
# Express PostgreSQL CRUD API

This project is a simple Express.js API that connects to a PostgreSQL database and performs basic CRUD (Create, Read, Update, Delete) operations on a `users` table.

## Table of Contents

- [Project Overview](#project-overview)  
- [Features](#features)  
- [Technologies](#technologies)  
- [Prerequisites](#prerequisites)  
- [Setup Instructions](#setup-instructions)  
- [API Endpoints](#api-endpoints)  
- [Testing](#testing)  
- [Notes](#notes)  
- [License](#license)  

## Project Overview

This project demonstrates how to build a RESTful API using Express.js with PostgreSQL as the database. It provides endpoints to create, read, update, and delete users stored in a PostgreSQL database.

## Features

- Connects to PostgreSQL database using `pg` library  
- CRUD operations on `users` table (`id`, `name`, `email`, `age`)  
- Basic error handling for API endpoints  
- JSON request/response handling  
- Clean, modular Express.js code  

## Technologies

- Node.js  
- Express.js  
- PostgreSQL  
- pg (PostgreSQL client for Node.js)  

## Prerequisites

- [Node.js](https://nodejs.org/en/) installed  
- [PostgreSQL](https://www.postgresql.org/download/) installed and running  
- Basic knowledge of command line and REST APIs  

## Setup Instructions

1. **Clone the repository or create a new project directory:**

   ```bash
   mkdir express-postgres-crud
   cd express-postgres-crud
   ```

2. **Initialize Node.js project and install dependencies:**

   ```bash
   npm init -y
   npm install express pg
   ```

3. **Set up PostgreSQL database:**

   - Start PostgreSQL server.
   - Open PostgreSQL command line or GUI tool.
   - Create a new database (replace `mydatabase` with your choice):

     ```sql
     CREATE DATABASE mydatabase;
     ```

4. **Create the `users` table:**

   Connect to your database and run:

   ```sql
   CREATE TABLE users (
     id SERIAL PRIMARY KEY,
     name VARCHAR(100),
     email VARCHAR(100),
     age INTEGER
   );
   ```

5. **Create `app.js` file and paste the application code (provided in this project).**

6. **Configure database connection in `app.js`:**

   Update the PostgreSQL credentials inside the `Pool` configuration:

   ```js
   const pool = new Pool({
     user: 'your_username',     // your PostgreSQL username
     host: 'localhost',
     database: 'mydatabase',    // your database name
     password: 'your_password', // your PostgreSQL password
     port: 5432,
   });
   ```

7. **Start the Express.js server:**

   ```bash
   node app.js
   ```

8. **Your API will run on:** `http://localhost:3000`

## API Endpoints

| Method | Endpoint        | Description              | Request Body                 | Response                  |
|--------|-----------------|--------------------------|------------------------------|---------------------------|
| GET    | `/users`        | Retrieve all users       | None                         | Array of user objects     |
| GET    | `/users/:id`    | Retrieve user by ID      | None                         | User object               |
| POST   | `/users`        | Create a new user        | `{name, email, age}`         | Created user object       |
| PUT    | `/users/:id`    | Update user by ID        | `{name, email, age}`         | Updated user object       |
| DELETE | `/users/:id`    | Delete user by ID        | None                         | 204 No Content            |

> All request and response bodies are in JSON format.

## Testing

You can use [Postman](https://www.postman.com/) or any other HTTP client to test the API endpoints.

- Example POST body to create user:

  ```json
  {
    "name": "John Doe",
    "email": "john@example.com",
    "age": 30
  }
  ```

- Example PUT body to update user:

  ```json
  {
    "name": "Jane Doe",
    "email": "jane@example.com",
    "age": 28
  }
  ```

## Notes

- Ensure your PostgreSQL server is running before starting the API server.  
- Consider using environment variables or a config file to store sensitive credentials in production.  
- This project is intended for learning and basic use cases; for production, add more robust validation, authentication, and error handling.  

## License

This project is released under no License.
