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
## 🎨 UI/UX Design Planning

### 🧭 Design Goals

The primary goal of the UI/UX design is to ensure an intuitive, responsive, and seamless experience for users engaging with the platform—whether they're guests searching for stays, hosts managing listings, or admins overseeing operations. Key design principles include:

- **Clarity & Simplicity:** Reduce cognitive load with clean layouts and intuitive navigation.
- **Accessibility:** Ensure the platform is usable by all users, including those with disabilities.
- **Consistency:** Apply consistent visual and interaction patterns throughout the app.
- **Responsiveness:** Optimize for various screen sizes—desktop, tablet, and mobile.

### 🔑 Key Features to Implement

- Easy-to-navigate **property browsing** interface
- Informative **property detail** pages with high-quality visuals
- Streamlined **checkout process** with clear cost breakdowns
- Responsive layout with mobile-first design
- Clear **call-to-action buttons** for booking and messaging
- User feedback via **ratings and reviews**
- Error handling and form validations with user-friendly alerts

---

### 🗂️ Core Page Layouts

| Page                     | Description                                                                                                                                     | Key Components                                                                 |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| **Property Listing View** | Displays a scrollable or grid list of available properties with filters and search capabilities.                                               | Property image, title, price per night, location, filter/search bar, pagination |
| **Listing Detailed View**| Shows full information about a selected property. Includes photo gallery, availability calendar, host info, and reviews.                        | Image carousel, property description, amenities list, calendar, review section  |
| **Simple Checkout View** | Allows users to confirm booking details, input payment information, and complete their reservation.                                             | Booking summary, total cost, payment form, submit button, cancellation policy   |

---

### 💡 Importance of User-Friendly Design in a Booking System

A user-friendly design is critical in a booking system for several reasons:

- **Trust & Credibility**: Clean, professional design builds user confidence and credibility.
- **Conversion Optimization**: Streamlined interactions reduce drop-off rates during searches and checkouts.
- **Error Reduction**: Intuitive design helps users avoid mistakes in booking dates or payments.
- **Accessibility**: An inclusive design ensures a broader reach to users of all abilities.
- **Retention & Satisfaction**: A pleasant experience encourages users to return and recommend the platform.

### 🎨 Design Properties from Figma

#### 🎨 Color Styles

The Figma design uses a consistent color palette to provide visual clarity and maintain brand consistency across the interface. Below are the color styles used:

- **Primary Color:** #FF5A5F – Used for call-to-action buttons and highlights
- **Secondary Color:** #484848 – Used for titles and headings
- **Background Color:** #F7F7F7 – Light background for a clean look
- **Text Color (Body):** #222222 – Default text for readability
- **Accent Color:** #00A699 – Used to draw attention to icons or links
- **Error Color:** #FF0000 – Used for validation errors or alerts

#### 🔤 Typography

Typography is crucial for accessibility, readability, and visual hierarchy. The design uses:

- **Font Family:** `Inter`, sans-serif (alternatively `Roboto`, `Helvetica`, or system-ui)
- **Font Weights:**
  - **Regular:** 400 – For body text and descriptions
  - **Medium:** 500 – For buttons and labels
  - **Bold:** 700 – For headings and section titles
- **Font Sizes:**
  - **Heading 1 (H1):** 32px
  - **Heading 2 (H2):** 24px
  - **Heading 3 (H3):** 18px
  - **Body Text:** 16px
  - **Small Text / Captions:** 12px

---

### 🧠 Why Identifying Design Properties in Figma Matters

Identifying and documenting design properties (like color styles and typography) from a mockup in Figma is essential for the following reasons:

- **Consistency Across the App:** Ensures uniform look and feel across all components and pages.
- **Efficient Handoff to Developers:** Reduces ambiguity during implementation by providing exact specs.
- **Scalability:** Enables the reuse of components and styles, making the design system scalable and maintainable.
- **Accessibility:** Helps enforce contrast ratios, readable font sizes, and other usability standards.
- **Collaboration:** Facilitates clearer communication between designers and developers.

Figma serves as a single source of truth for design decisions, ensuring that the final product matches the original vision.

In a competitive market like short-term rentals, excellent UI/UX is not just aesthetic—it's a key business driver.

## 🧱 UI Component Patterns

To maintain a modular and scalable front-end architecture, the Airbnb Clone project will use reusable UI components. These components help streamline development, ensure visual consistency, and improve code maintainability. Below are the key UI components planned for implementation:

### 🔝 Navbar (Navigation Bar)
- **Purpose:** Provides consistent access to key pages like Home, Listings, Profile, and Login/Signup.
- **Features:**
  - Responsive layout (mobile + desktop)
  - Dropdown for user profile
  - Logo linking back to homepage
  - Search bar (optional in extended version)

---

### 🏠 Property Card
- **Purpose:** Displays individual properties in the Property Listing View.
- **Features:**
  - Image preview of the property
  - Property name and location
  - Price per night
  - Rating stars (based on reviews)
  - Clickable card linking to the detailed view

---

### 📄 Property Detailed View Layout
- **Purpose:** Provides full information about a selected property.
- **Features:**
  - Image carousel
  - Description, amenities, and host details
  - Reviews section
  - Booking availability (calendar widget)
  - "Book Now" button

---

### ✅ Checkout Summary Panel
- **Purpose:** Helps users review and confirm their bookings.
- **Features:**
  - Summary of property, dates, and guests
  - Total cost breakdown
  - Payment form (mock)
  - Secure booking button

---

### 📥 Footer
- **Purpose:** Provides supplemental navigation and platform information.
- **Features:**
  - Links to Terms, Privacy Policy, Contact
  - Social media icons
  - Language and currency selectors

---

### 📦 Additional Components (Planned for Extension)
- **Modal Windows:** For login, signup, and confirmation messages
- **Pagination Controls:** For listings navigation
- **Alert Messages:** For errors, confirmations, and notifications

By breaking the UI into clear, reusable patterns, the project becomes easier to scale, test, and maintain while improving the overall user experience.

---

## Technology Stack
- **Programming Language:** Python 3
- **Backend Framework:** Django
- **Frontend:** HTML5, CSS3, JavaScript
- **Database:** MySQL or SQLite
- **Version Control:** Git & GitHub
- **Design Tools:** Figma for UI/UX design


## Team Roles
- **Backend Developer:** Vincent Dushime
