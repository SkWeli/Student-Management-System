# Student-Management-System

A production-grade RESTful backend for managing students, courses, and enrollments at the Department of Software Engineering, KDU. Built with Spring Boot 3, PostgreSQL, and JWT-based authentication.

---

## 🛠 Tech Stack

| Layer        | Technology                          |
|--------------|-------------------------------------|
| Language     | Java 17                             |
| Framework    | Spring Boot 3.2.x                   |
| Security     | Spring Security + JWT (JJWT 0.12.x) |
| Database     | PostgreSQL 15                       |
| ORM          | Spring Data JPA / Hibernate         |
| Build Tool   | Maven                               |
| Containers   | Docker                              |
| IDE          | IntelliJ IDEA                       |

---

## 📁 Project Structure

```
src/main/java/com/senuda/sms/
├── config/ # Security & app configuration
├── controller/ # REST API layer
├── dto/
│ ├── request/ # Incoming request bodies
│ └── response/ # Outgoing response bodies
├── entity/ # JPA entities (DB tables)
├── exception/ # Custom exceptions & global handler
├── repository/ # Spring Data JPA interfaces
├── security/ # JWT filter & service
└── service/ # Business logic
```


---

## ⚙️ Prerequisites

- Java 17+
- Maven 3.8+
- Docker 20+
- Git 2+

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/SkWeli/student-management-system.git
cd student-management-system
```

### 2. Start PostgreSQL with Docker
```bash
docker run --name sms-postgres \
  -e POSTGRES_DB=smsdb \
  -e POSTGRES_USER=smsuser \
  -e POSTGRES_PASSWORD=smspass \
  -p 5432:5432 \
  -d postgres:15-alpine
```

### 3. Run the application
```bash
mvn spring-boot:run
```
App starts on **http://localhost:8080**

---

## 🔐 Authentication

All protected routes require a Bearer token in the `Authorization` header.

**Login:**
```bash
POST /api/auth/login
{
  "username": "admin",
  "password": "Admin@12345"
}
```
Returns: `{ "token": "eyJ...", "username": "admin", "role": "ADMIN" }`

Use the token: `Authorization: Bearer eyJ...`

---

## 📡 API Endpoints

### Auth
| Method | Endpoint          | Access  | Description   |
|--------|-------------------|---------|---------------|
| POST   | /api/auth/login   | Public  | Get JWT token |

### Students
| Method | Endpoint            | Access       | Description          |
|--------|---------------------|--------------|----------------------|
| POST   | /api/students       | ADMIN        | Create student       |
| GET    | /api/students       | Authenticated| List all students    |
| GET    | /api/students/{id}  | Authenticated| Get student by ID    |
| DELETE | /api/students/{id}  | ADMIN        | Delete student       |

### Courses *(coming soon)*
### Enrollments *(coming soon)*

---

## 🗄️ Database Schema
```
users ──────────── students
│ │
│ (lecturer) │ OneToMany
▼ ▼
courses ──────── enrollments
```


---

## 🧪 Running Tests

```bash
mvn test
```

---

## 👤 Author

**Senuda Kenula Weliwatta**  
Software Engineering Undergraduate — KDU  
[GitHub](https://github.com/SkWeli) · [LinkedIn](https://www.linkedin.com/in/senuda-weliwatta/) · [Portfolio](https://portfolio-d-bse-23-0009.vercel.app/)

---

## 📄 License
MIT LICENSE
