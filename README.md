# AirBnB Clone Project

## Project Overview
This project is a clone of the AirBnB web application. The goal is to recreate key features of the platform including listing properties, booking stays, and managing users. This is a foundational project in backend web development.
---

## 🧩 Feature Breakdown

The Airbnb Clone project is designed to replicate key functionalities of the real Airbnb platform. Below are the core features implemented in the application:

### 👤 User Management
Users can register, log in, and manage their profiles. Depending on their role (guest, host, or admin), they can perform actions such as booking properties, listing properties, or managing platform operations.

### 🏠 Property Management
Hosts can list properties with details such as name, description, location, and price per night. They can also edit or remove their listings, helping them maintain an up-to-date rental inventory.

### 📅 Booking System
Guests can search and book available properties for specific dates. The system calculates the total cost and prevents double-booking, ensuring a smooth reservation experience.

### 💳 Payment Processing
Each booking includes a payment record that tracks the amount paid, payment method, and payment date. This ensures transparency and reliability in financial transactions between guests and hosts.

### ⭐ Reviews and Ratings
After completing a stay, users can leave a review and rating for the property. This feature promotes trust within the community and helps future guests make informed decisions.

### 💬 Messaging System
Users can send messages to one another to coordinate bookings, ask questions, or resolve issues. This peer-to-peer communication supports a more engaging and efficient booking process.

---
## 📊 Database Design

This project utilizes a relational database to manage core Airbnb-style functionality. Below is an overview of the key entities and their relationships.

### 🧑 User
Users can act as guests, hosts, or admins.
- **user_id** (UUID, Primary Key)
- **first_name**
- **last_name**
- **email** (Unique)
- **role** (guest, host, admin)

➡️ A user can:
- Host multiple properties
- Make multiple bookings
- Send and receive messages
- Leave reviews on properties

---

### 🏠 Property
Properties are created by users who act as hosts.
- **property_id** (UUID, Primary Key)
- **host_id** (FK to User)
- **name**
- **location**
- **price_per_night**

➡️ A property:
- Belongs to one host (User)
- Can have many bookings
- Can receive many reviews

---

### 📅 Booking
Represents a reservation made by a user for a property.
- **booking_id** (UUID, Primary Key)
- **property_id** (FK to Property)
- **user_id** (FK to User)
- **start_date / end_date**
- **total_price**

➡️ A booking:
- Is made by one user
- Is for one property
- Has one associated payment

---

### 💳 Payment
Tracks payment transactions for bookings.
- **payment_id** (UUID, Primary Key)
- **booking_id** (FK to Booking)
- **amount**
- **payment_date**
- **payment_method**

➡️ A payment:
- Belongs to one booking
- Stores the method and amount used for that booking

---

### ⭐ Review
Captures feedback from users on properties they’ve stayed at.
- **review_id** (UUID, Primary Key)
- **property_id** (FK to Property)
- **user_id** (FK to User)
- **rating**
- **comment**

➡️ A review:
- Is left by one user
- Is for one property

---

### 💬 Message
Enables users to communicate with one another.
- **message_id** (UUID, Primary Key)
- **sender_id / recipient_id** (FK to User)
- **message_body**
- **sent_at**

➡️ A message:
- Is sent from one user to another
- Supports many-to-many communication (indirectly)

---

### 🔗 Relationships Summary

- A **User** can create multiple **Properties**
- A **User** can make multiple **Bookings**
- A **Property** can have many **Bookings**
- Each **Booking** has one **Payment**
- A **User** can leave many **Reviews**
- A **Property** can receive many **Reviews**
- **Messages** connect users in a many-to-many communication model

---
## 🔒 API Security

Security is a critical component of this Airbnb Clone project, especially because it handles sensitive user information, payments, and communication. The following measures are implemented to ensure the backend APIs remain secure and reliable:

### 🔐 Authentication
All API endpoints that involve user-specific actions require secure authentication using tokens (e.g., JWT). This ensures that only verified users can access their data and perform authorized operations.

**Why it matters:** Prevents unauthorized access to user accounts and ensures only legitimate users can interact with the system.

---

### 🛡️ Authorization
Role-based access control (RBAC) is used to determine user privileges. For instance, only hosts can create or update properties, and only the booking owner can cancel a booking.

**Why it matters:** Protects the system from privilege escalation and ensures users cannot perform actions beyond their access level.

---

### 🚦 Rate Limiting
API endpoints are rate-limited to prevent abuse, brute force attacks, and denial-of-service (DoS) attempts. This helps maintain system stability and fair usage.

**Why it matters:** Defends against automated attacks and keeps the system responsive for all users.

---

### 🔒 Secure Payments
All payment-related data is transmitted and stored securely. Integration with trusted payment providers like Stripe or PayPal includes best practices for handling sensitive financial information.

**Why it matters:** Ensures the protection of financial data and builds user trust in the platform.

---

### 🧪 Input Validation & Sanitization
All incoming data is validated and sanitized to prevent injection attacks (e.g., SQL injection, XSS).

**Why it matters:** Protects the database and front end from malicious data inputs and preserves the integrity of the application.
---
These security layers are foundational for building a trustworthy and reliable Airbnb-like platform.
---
## 🔁 CI/CD Pipeline

CI/CD (Continuous Integration and Continuous Deployment) pipelines automate the building, testing, and deployment of code. This approach helps development teams detect bugs early, deliver features faster, and maintain high-quality code through frequent integration and deployment.

In this project, a CI/CD pipeline ensures that every change pushed to the repository is automatically tested and deployed if it passes the necessary checks. This process improves reliability, speeds up development, and reduces manual errors.

### ⚙️ Tools Used:
- **GitHub Actions**: Automates testing, linting, and deployment directly from GitHub.
- **Docker**: Provides containerized environments for consistent builds and deployments across different platforms.
- **Heroku / Vercel / AWS (optional)**: Can be used for deploying the backend or front-end services with minimal setup.

With CI/CD in place, this Airbnb Clone project can scale efficiently and be safely updated in a collaborative development environment.

---

## Technology Stack
- **Programming Language:** Python 3
- **Backend Framework:** Django
- **Frontend:** HTML5, CSS3, JavaScript
- **Database:** MySQL or SQLite
- **Version Control:** Git & GitHub

## Team Roles
- **Backend Developer:** Vincent Dushime
