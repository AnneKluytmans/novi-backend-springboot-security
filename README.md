# Car API Security Implementation with JWT– NOVI Backend Assignment

## Overview

This repository contains my solution for a backend assignment from the Backend module at [Novi University](https://www.novi.nl).
The goal of this project is to secure an existing **Car RESTful API** by implementing:

- User authentication and authorization
- Login functionality with JWT tokens
- Protected endpoints for managing car data

This assignment demonstrates how to use **Spring Boot Security**, **Maven**, and **JWT (JSON Web Tokens)** to secure a REST API in Java.

---

## Table of Contents

- [Tech Stack](#tech-stack)
- [Key features](#key-features)
- [Authentication Flow](#authentication-flow)
- [API Endpoints](#api-endpoints)
- [How to Run](#how-to-run)
- [Credits](#credits)
- [License](#license)

---

## Tech Stack

- **Java 17+**
- **Spring Boot** 3.x (REST API)
- **Maven**
- **Spring Security**
- **JPA** / **Hibernate**
- **JWT** (JSON Web Tokens) for authentication
- **Bean Validation** (Jakarta / Hibernate Validator)


---

## Key Features

- User registration and storage via **User Entity** and **UserRepository**
- Custom `UserDetailsService` for authentication
- Basic security with username/password login
- Token-based authentication using JWT
- Secure endpoints to protect car data (CRUD operations)
- JWT validation filter to ensure valid tokens for API access
- Properties-driven configuration for secret keys and token settings

---

## Authentication Flow

1. **User login request:**  
   Client sends a `POST` request with username and password to `/login`.

2. **JWT token generation:**  
   If credentials are valid, the server responds with a signed JWT token.

3. **Accessing secured endpoints:**  
   Clients must include the token in the `Authorization: Bearer <token>` header for API requests.

4. **Token validation:**  
   The `JwtRequestFilter` intercepts requests, validates tokens, and authorizes the user before allowing access.

___

## API Endpoints

## Authentication

| Method | Endpoint | Description                              |
|--------|----------|------------------------------------------|
| POST   | `/login` | Authenticate user and receive JWT token  |

---

## Car API (secured)

| Method | Endpoint        | Description                                   |
|--------|-----------------|-----------------------------------------------|
| GET    | `/cars`         | Retrieve all cars (requires valid JWT token)  |
| POST   | `/cars`         | Create a new car                              |
| PUT    | `/cars/{id}`    | Update car details                            |
| DELETE | `/cars/{id}`    | Delete a car                                  |


### Car Registration Controller (`/cars/{carId}/carregistrations`)
| Method | Endpoint                                                      | Description                         |
|--------|---------------------------------------------------------------|-------------------------------------|
| POST   | `/cars/{carId}/carregistrations`                              | Create a new registration for car   |
| GET    | `/cars/{carId}/carregistrations/{registrationId}`             | Get a specific registration         |
| PUT    | `/cars/{carId}/carregistrations/{registrationId}`             | Update a registration               |
| DELETE | `/cars/{carId}/carregistrations/{registrationId}`             | Delete a registration               |

---

## Example Login Request

```json
{
  "username": "testuser",
  "password": "password123"
}
```

### Example Login Response

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```
---
## How to Run

### Using IntelliJ IDEA

1. Open the project.
2. Locate the `CarApplication` main class.
3. Click the green play️ button to run the application or use the terminal:
    ```bash
    ./mvnw spring-boot:run
   ```
4. The server will start at: `http://localhost:8080`

---

## Credits
> "This assignment was developed as part of the Backend Java module in the NOVI Software Development program. All instructions, logic, and structure are part of the official coursework."

## License
> "This repository is intended for educational purposes only. You are welcome to use the code for learning, but not for commercial use."