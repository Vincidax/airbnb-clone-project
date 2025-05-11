# AirBnB Clone Project

## Project Overview
This project is a clone of the AirBnB web application. The goal is to recreate key features of the platform including listing properties, booking stays, and managing users. This is a foundational project in backend web development.

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

## Technology Stack
- **Programming Language:** Python 3
- **Backend Framework:** Django
- **Frontend:** HTML5, CSS3, JavaScript
- **Database:** MySQL or SQLite
- **Version Control:** Git & GitHub

## Team Roles
- **Backend Developer:** Vincent Dushime
