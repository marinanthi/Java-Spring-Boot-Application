# Lesson Management Microservice

## Overview

This project is a **Spring Boot RESTful microservice** that manages **Lessons**. It provides endpoints to create lessons and retrieve them from a **PostgreSQL** database using **Spring Data JPA (Hibernate)**.

---

##  Architecture

The application follows a classic 3-layer architecture:

```
Controller → Service → Repository → Database
```

* **Controller layer**: Exposes REST API endpoints
* **Service layer**: Contains business logic
* **Repository layer**: Handles database access using JPA

---

##  REST API Endpoints

###  Create a Lesson

**POST** `/api/v1/lessons`

Request body:

```json
{
  "lessonTitle": "Databases"
}
```

---

###  Get All Lessons

**GET** `/api/v1/lessons/all`

Response:

```json
[
  {
    "id": 1,
    "lessonTitle": "Databases"
  }
]
```

---

###  Get Lesson by ID

**GET** `/api/v1/lessons/{id}`

Example:

```
/api/v1/lessons/1
```

Returns the lesson with the given ID or throws a `LessonNotFoundException` if it does not exist.

---

###  Get Lessons by Title

**GET** `/api/v1/lessons?title={lessonTitle}`

Example:

```
/api/v1/lessons?title=Databases
```

Returns a list of lessons with the specified title. If no lessons are found, a `LessonNotFoundException` is thrown.

---

##  Database Configuration

The application uses **PostgreSQL** as its database.

* `ddl-auto: update` automatically updates the database schema
* SQL queries are logged to the console

---

##  Run with Docker (PostgreSQL)

Start the PostgreSQL database using Docker Compose:

```bash
docker-compose up -d
```
---

##  Run the Application

```bash
mvn clean install
mvn spring-boot:run
```

The application will start on:

```
http://localhost:8080
```

