# Social Media Dashboard

## Overview

The **Social Media Dashboard** is a hands-on project that demonstrates the development of a fully functional web application using **Node.js**, **Express**, and **MongoDB**. This project incorporates essential components such as **user authentication**, **API development**, **frontend integration**, and **data persistence**.

The application enables users to register, log in, create posts, update or delete posts, and manage sessions securely. Designed for scalability and security, the project also includes deployment through **Docker** for consistent environments.

---

## Features

- **User Management**: User registration and authentication using JWT tokens.
- **Post Management**: Create, edit, delete, and paginate posts.
- **Session Management**: Secure session handling with JSON Web Tokens (JWT).
- **Frontend Dashboard**: A responsive and interactive user interface.
- **Docker Deployment**: Simplified deployment with containerized environments.

---

## Technologies Used

### 1. **Backend**
- **Node.js & Express**:  
  Manages server-side logic, routing, and middleware for API endpoints.  
  Example: `app.post('/register')` handles user registration and creates a JWT token.

- **JWT (JSON Web Tokens)**:  
  Used for secure user authentication and maintaining session state.  
  Example: `authenticateJWT` middleware validates tokens for protected routes.

- **Session Management**:  
  `express-session` stores JWT tokens for persistent user authentication.

- **Mongoose**:  
  Provides schema-based validation and interaction with MongoDB.  
  Example: The `User` and `Post` schemas manage user and post data.

---

### 2. **Frontend**
- **HTML & CSS**:  
  - Creates a clean and responsive user interface for interactions like registration, login, and post management.
  - Includes dynamic elements like pagination and session-based controls.

- **JavaScript**:  
  - Handles dynamic features such as post creation, editing, deletion, and pagination without requiring page reloads.

---

### 3. **Database**
- **MongoDB**:  
  - Stores user credentials and post data using schema validation.
  - Collections:
    - **Users**: Fields include `username`, `email`, and `password`.
    - **Posts**: Fields include `userId` (relation to Users) and `text`.

---

### 4. **Authentication**
- **JWT Authentication**:  
  - Protects API routes by validating tokens before granting access.
  - Middleware examples:
    - `authenticateJWT`: Ensures API requests are from authenticated users.
    - `requireAuth`: Redirects unauthenticated users to the login page.

---

### 5. **Deployment**
- **Docker**:  
  - Containerizes the application for consistent deployment.
  - The `Dockerfile` defines the application’s Node.js environment, dependencies, and execution.
  - Example:
    ```dockerfile
    FROM node:18.12.1-bullseye-slim
    WORKDIR /app
    COPY . .
    RUN npm install
    EXPOSE 3000
    CMD ["node", "app.js"]
    ```

- **Docker Compose**:  
  - Manages multi-container setups for the Node.js app and MongoDB.
  - Example `docker-compose.yml`:
    ```yaml
    services:
      mongodb:
        image: mongo
        ports:
          - "27017:27017"
      app:
        build: .
        ports:
          - "3000:3000"
        depends_on:
          - mongodb
    ```
---

## Installation and Usage

### Prerequisites
- **Node.js** (version 18 or later)
- **MongoDB** (local or cloud-based)
- **Docker** and **Docker Compose**

### Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/social-media-dashboard.git
   cd social-media-dashboard
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Update the MongoDB URI in `app.js` if running locally:
   ```javascript
   const uri = "mongodb://localhost:27017";
   mongoose.connect(uri, { dbName: 'SocialDB' });
   ```

4. Start the server:
   ```bash
   node app.js
   ```

5. Access the application:
   - Visit: `http://localhost:3000`.

6. To deploy using Docker:
   - Build the Docker image:
     ```bash
     docker build . -t socialapp
     ```
   - Start services:
     ```bash
     docker-compose up
     ```

---

## Key Features

- **Secure Authentication**:  
  Passwords are encrypted, and JWT tokens are generated and validated for each session.

- **CRUD Operations**:
  - **Create**: Add new posts.
  - **Read**: View posts with pagination.
  - **Update**: Modify existing posts.
  - **Delete**: Remove posts.

- **Frontend Interactions**:  
  - Dynamic buttons and forms adjust based on the user's authentication state.

---

## Learning Objectives

By completing this project, you will learn:
1. How to create and manage databases using MongoDB.
2. How to implement secure user authentication with JWTs.
3. How to set up RESTful API endpoints for user and post management.
4. How to build and integrate a responsive frontend.
5. How to deploy a full-stack application using Docker.

---

Feel free to reach out with any feedback or suggestions!
