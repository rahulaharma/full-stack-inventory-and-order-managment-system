# Inventory & Order Management System - Frontend

This is the frontend for a comprehensive Inventory and Order Management System, built with a modern, high-performance tech stack including React 19, React Router v7, and Tailwind CSS v4.

The application provides a user-friendly interface for managing products, inventory levels, customers, and sales orders. It features role-based access control to ensure that staff members can only access the features relevant to their roles.

You can access backend for the same here 
```bash
https://github.com/rahulaharma/inventory-and-order-management-system
```
---

## ✨ Key Features

* **Dashboard:** An overview of key metrics and system activity.
* **Product Management:** Full CRUD (Create, Read, Update, Delete) functionality for products.
* **Inventory Tracking:** Monitor stock levels and manage inventory updates.
* **Customer Management:** Maintain a database of customers with complete CRUD operations.
* **Order Processing:**
    * Create new sales orders.
    * View a list of all orders.
    * Drill down into detailed order information.
* **User Authentication:** Secure login and registration system using JWT.
* **Role-Based Access Control:** Custom routes and components (`ProtectedRoute`, `RoleBasedRoute`) restrict access based on user roles (e.g., Sales Staff).
* **Interactive Notifications:** User-friendly feedback through toast notifications.
  
---
## 🚀 Technologies Used

* **Framework:** **React 19**
* **Bundler:** **Parcel v2**
* **Routing:** **React Router DOM v7**
* **Styling:** **Tailwind CSS v4** & Heroicons
* **HTTP Client:** Axios
* **State Management:** React Context API (`AuthProvider`)
* **Notifications:** React Toastify
* **Authentication:** JWT Decode

---

## 🛠️ Installation & Setup

Follow these steps to get the development environment running locally.

### Prerequisites

* [Node.js](https://nodejs.org/) (version 18.x or higher recommended)
* [npm](https://www.npmjs.com/) (comes with Node.js)
  
### 1. Clone the Repository

```sh
git clone [https://github.com/rahulaharma/inventory-order-management-frontend.git](https://github.com/rahulaharma/inventory-order-management-frontend.git)
cd inventory-order-management-frontend
```
### 2. Install Dependencies

Install all the required npm packages.

```sh
npm install
```
### 3. Set Up Environment Variables

This project requires an API endpoint to connect to the backend.

1.  Create a new file in the root of the project named `.env`.
2.  Add the following variable, pointing to your backend server URL:

    ```env
    REACT_APP_API_BASE_URL=http://localhost:8080/api
    ```

    *(Adjust the URL if your backend server runs on a different port or domain.)*

### 4. Run the Development Server

Start the Parcel development server.

```sh
npm run start
```

The application should now be running on `http://localhost:1234`.


# Inventory & Order Management System - Backend

This is the backend for a comprehensive Inventory and Order Management System, built with a modern, high-performance tech stack including **Java 21**, **Spring Boot**, and **Spring Security**.

The application provides a robust, secure, and scalable RESTful API to manage products, inventory levels, customers, and sales orders. It features JWT-based authentication and a clear, service-oriented architecture to ensure maintainability and separation of concerns.

You can access frontend for the same here 
```bash
https://github.com/rahulaharma/inventory-order-management-frontend
```


---

## ✨ Key Features

* **Secure API:** Endpoints are secured using Spring Security, with role-based access control available for future expansion.
* **Product Management:** Full CRUD (Create, Read, Update, Delete) functionality for products, which automatically creates an associated inventory record.
* **Inventory Tracking:** Monitor and update stock levels for each product independently via dedicated API endpoints.
* **Customer Management:** Maintain a database of customers with complete CRUD operations.
* **Order Processing:**
    * Create new sales orders with multiple line items.
    * View a list of all orders, or filter orders by salesperson or customer.
    * Drill down into detailed order information.
    * Update the status of an order (e.g., NEW, PACKED, SHIPPED).
* **User Authentication:** Secure login (`/api/login`) and registration (`/api/register`) system using JWT.
* **Decoupled Service Layer:** Business logic is separated into service interfaces and implementations for better testing and maintenance (e.g., `ProductService`, `OrderService`).
* **Notification System:** A framework for creating, retrieving, and marking notifications as read for users.

---

## 🚀 Technologies Used

* **Framework:** Spring Boot
* **Language:** Java 21
* **Security:** Spring Security, JSON Web Token (JWT)
* **Data Persistence:** Spring Data JPA, Hibernate
* **Build Tool:** Gradle
* **API Specification:** RESTful services

---

## 🛠️ Installation & Setup

Follow these steps to get the development environment running locally.

### Prerequisites

* **Java Development Kit (JDK):** Version 21 or higher.
* **Gradle:** Version 8.8 or higher is recommended (the project includes a Gradle wrapper).
* **Database:** A running instance of a relational database like PostgreSQL or MySQL.

### 1. Clone the Repository

```bash
git clone <https://github.com/rahulaharma/inventory-and-order-management-system>
cd <inventory-and-order-management-system>
```

### 2. Configure the Database
* Navigate to app/src/main/resources.

* Create an application.properties file.

* Add the database connection properties

### 3. Run the Development Server

Start the Spring Boot application using the provided Gradle wrapper. This will handle dependency installation and run the server.

On macOS/Linux:
```bash
./gradlew bootRun
```
On Windows:
```bash
.\gradlew.bat bootRun
```
## 📂 Project Structure
The src/main/java folder is organized to maintain a clean and scalable architecture.

```text
src/main/java/org/example/
├── config/             # Spring Security and JWT filter configurations.
├── controller/         # REST API controllers (e.g., ProductController, OrderController).
├── model/              # JPA entity classes (e.g., Product, Order, User).
├── repository/         # Spring Data JPA repositories for database access.
├── Service/            # Business logic interfaces and implementations.
└── App.java            # Main Spring Boot application entry point.
```
## 🔐 Authentication Flow

* **Register/Login**: A new user can be created via POST /api/register. To log in, a user sends their credentials to POST /api/login.

* **Receive Token**: Upon successful login, the server generates a JWT and returns it to the client.

* **Authenticated Requests**: For all subsequent requests to protected endpoints, the client must include the JWT in the Authorization header as a Bearer token.

* **Example**: Authorization: Bearer <your_jwt_token>

* **Authorization**: The JWTFilter intercepts each request, validates the token, and sets the user's security context, enabling access to the authorized resources.

## 📄 API Endpoints
All endpoints are prefixed with /api. The application is configured to accept requests from http://localhost:1234.



| Method | Endpoint                           | Description                                           |
|--------|------------------------------------|-------------------------------------------------------|
| POST   | /register                          | Registers a new user.                                |
| POST   | /login                             | Authenticates a user and returns a JWT.              |
| GET    | /products                          | Retrieves a list of all products.                    |
| POST   | /products                          | Creates a new product.                               |
| GET    | /products/{id}                     | Retrieves a single product by its ID.                |
| PUT    | /products/{id}                     | Updates an existing product.                         |
| DELETE | /products/{id}                     | Deletes a product.                                   |
| GET    | /customers                         | Retrieves all customers.                             |
| POST   | /customers                         | Creates a new customer.                              |
| GET    | /customers/{id}                    | Retrieves a customer by ID.                          |
| PUT    | /customers/{id}                    | Updates a customer.                                  |
| DELETE | /customers/{id}                    | Deletes a customer.                                  |
| GET    | /orders                            | Retrieves all orders.                                |
| POST   | /orders                            | Creates a new order.                                 |
| GET    | /orders/{id}                       | Retrieves an order by ID.                            |
| PUT    | /orders/{id}/status                | Updates the status of an order.                      |
| GET    | /orders/sales/{salesId}            | Retrieves all orders for a specific salesperson.     |
| GET    | /inventory                         | Retrieves the entire inventory.                      |
| GET    | /inventory/product/{productId}     | Retrieves inventory for a specific product.          |
| PUT    | /inventory/product/{productId}     | Updates the inventory quantity for a product.        |


## Author

Create By Rahul Sharma


---

## 📜 Available Scripts

In the project directory, you can run:

* `npm run start`
    * Runs the app in development mode with hot-reloading.
* `npm run build`
    * Builds the app for production to the `dist` folder. It correctly bundles React and optimizes the build for the best performance.


---

## ✍️ Author

Created by **Rahul Sharma**.

---
