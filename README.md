# 💰 Personal Finance Management (PFM)

A **modern, production-ready Personal Expense Management web application** built using **Spring Boot (MVC)** and **PostgreSQL**. This project helps users track income, expenses, categories, and view financial summaries with a clean layered architecture.

---

## 🚀 Features

### 🔐 Security & Authentication
- Spring Security integration
- JWT-based authentication
- OAuth 2.0 login (Google)
- Forgot password & reset password flow
- Role-based access control (USER / ADMIN)
- Secure password storage (BCrypt)

### 💼 Core Functionalities
- User-based expense & income tracking
- Expense categorization (master data)
- Monthly & yearly summaries
- Analytics dashboard (charts)
- Export reports (PDF / Excel
- Email verification & notifications
- Refresh token rotation
- Clean MVC + Service + Repository architecture
- JPA Specifications for dynamic queries
- JSP-based UI (Spring MVC)
- PostgreSQL persistence

---

## 🛠️ Tech Stack

### Backend
- Java 17+
- Spring Boot
- Spring MVC
- Spring Security
- JWT (JSON Web Tokens)
- OAuth 2.0 (Google Login)
- Spring Data JPA (Hibernate)
- Maven

### Database
- PostgreSQL

### View Layer
- JSP
- JSTL

### DevOps & Tools
- Git & GitHub
- Railway (Deployment)
- Embedded Tomcat

---

## 📁 Project Structure

```text
PFM
├── src/main/java/com/pfm
│   ├── config          # Configuration (DB, MVC, Security)
│   ├── controller      # Controllers (UI handling)
│   ├── dto             # Data Transfer Objects
│   ├── entity          # JPA Entities
│   ├── repo            # Repository layer (JPA)
│   ├── service         # Business logic interfaces
│   ├── serviceimpl     # Business logic implementations
│   └── specification   # Dynamic query specifications
│
├── src/main/resources
│   └── application-example.properties
│
├── src/main/webapp/WEB-INF/views
│   └── *.jsp           # JSP pages
│
├── src/test/java       # Tests
├── target              # Build output (ignored)
└── pom.xml
```

---

## 🗄️ Database Schema (ER Diagram)

### 📌 Entities Overview

```text
USER
──────
- id (PK)
- name
- email (UNIQUE)
- password
- created_at

CATEGORY
────────
- id (PK)
- name
- type (INCOME / EXPENSE)

EXPENSE
────────
- id (PK)
- amount
- description
- date
- user_id (FK)
- category_id (FK)

INCOME
───────
- id (PK)
- amount
- source
- date
- user_id (FK)
```

### 🔗 Relationships

```text
USER 1 ──── * EXPENSE
USER 1 ──── * INCOME
CATEGORY 1 ──── * EXPENSE
```

### 🧠 ER Diagram (Logical View)

```text
+---------+        +-----------+
|  USER   |1      *|  EXPENSE  |
+---------+--------+-----------+
     |1                  *
     |                    |
     |1                  *
+---------+        +-----------+
| INCOME  |        | CATEGORY  |
+---------+        +-----------+
```

---

## ⚙️ Database Setup (PostgreSQL)

### Create Database

```sql
CREATE DATABASE pfm_db;
```

### application-example.properties

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/pfm_db
spring.datasource.username=postgres
spring.datasource.password=your_password

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect

server.port=8080
```

📌 **Note:**
- `application.properties` is ignored via `.gitignore`
- Copy example file and update credentials locally

---

## 🗃️ Database Initialization (data.sql)

The project uses a `data.sql` file to **pre-populate master data** (expense & income categories) automatically when the application starts.

### 📄 data.sql (PostgreSQL)

```sql
INSERT INTO category (id, name, type) VALUES
(1,'Shopping','EXPENSE'),
(2,'Movie','EXPENSE'),
(3,'Salary','INCOME'),
(4,'Travel','EXPENSE'),
(5,'EMI','EXPENSE'),
(6,'Groceries','EXPENSE'),
(7,'Mobile Recharge','EXPENSE'),
(8,'Rent','EXPENSE'),
(9,'Food','EXPENSE'),
(10,'Bills','EXPENSE'),
(11,'Other Expense','EXPENSE'),
(12,'Other Income','INCOME')
ON CONFLICT (id) DO NOTHING;
```

### 🧠 Why `ON CONFLICT DO NOTHING`?
- Prevents duplicate category insertion
- Safe for application restarts
- Production-friendly initialization

📌 Place this file at:
```
src/main/resources/data.sql
```

⚠️ Ensure this property is enabled:
```properties
spring.sql.init.mode=always
```

---

## ▶️ Running the Application

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/VishnuYelde/Personal-Expense-Management-using-Spring-MVC.git
cd PFM
```

### 2️⃣ Configure Database

```bash
cp src/main/resources/application-example.properties \
   src/main/resources/application.properties
```

Update DB credentials inside the file.
Open in Spring Tool Suite 4 or in the Eclipse IDE

### 3️⃣ Run the App

```bash
mvn spring-boot:run
```

or

```bash
mvn clean install
java -jar target/PFM-*.jar
```

---

## 📌 Best Practices Followed

- Layered architecture
- DTO-based data transfer
- JPA Specifications
- Secure config handling
- Clean Git history

---

## 🔮 Future Enhancements

- Account lockout & audit logs
- REST API version
- Cloud & Railway deployment ready
- React / Angular frontend
- Docker & CI/CD pipeline

---

## 👨‍💻 Author

**Vishnu Yelde**  
Java Full Stack Developer

---

## ⭐ Support

If you like this project, **give it a star ⭐** and feel free to fork or contribute!

