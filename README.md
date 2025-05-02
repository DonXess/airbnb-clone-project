# airbnb-clone-project

## 👥 Team Roles

### 🔧 Backend Developer
**Project Responsibility:**
- Develop and maintain REST and GraphQL API endpoints.
- Write business logic for user authentication, property listings, bookings, payments, and reviews.
- Ensure proper integration with the database and asynchronous tools like Celery.

**General Description (from ITRexGroup):**
- Backend developers are the core of the development team, building the application's server-side logic, integrating APIs, and ensuring scalability and security.

---

### 🗃️ Database Administrator (DBA)
**Project Responsibility:**
- Design the relational database schema for users, properties, bookings, reviews, and payments.
- Implement indexing and caching strategies (e.g., Redis) for performance optimization.
- Ensure data integrity, backup, and disaster recovery processes.

**General Description (from ITRexGroup):**
- DBAs ensure the database is well-structured, reliable, and performs efficiently under load. They also handle tuning and scaling of the database.

---

### ⚙️ DevOps Engineer
**Project Responsibility:**
- Set up Docker containers and manage environment consistency.
- Configure and maintain CI/CD pipelines for automated testing and deployment.
- Monitor system performance, handle logging, and implement scaling strategies.

**General Description (from ITRexGroup):**
- DevOps engineers bridge the gap between development and operations by automating infrastructure, deployment, and monitoring to improve reliability and delivery speed.

---

### ✅ QA (Quality Assurance) Engineer
**Project Responsibility:**
- Design and run automated tests for all major endpoints and features.
- Validate that new features meet acceptance criteria and do not break existing functionality.
- Participate in bug tracking and regression testing before release.

**General Description (from ITRexGroup):**
- QA engineers ensure software quality through rigorous testing strategies, identifying bugs early and verifying that the system behaves as expected.



## 🧱 Technology Stack

The Airbnb Clone project uses a powerful combination of tools and technologies to ensure scalability, maintainability, and performance.

### 🐍 Django
A high-level Python web framework that encourages rapid development and clean, pragmatic design. It is used to build the core of the backend and handle HTTP requests, routing, and application logic.

### 🔗 Django REST Framework (DRF)
A flexible and powerful toolkit for building Web APIs on top of Django. It provides tools to serialize data, handle authentication, permissions, and CRUD operations for users, properties, bookings, etc.

### 🐘 PostgreSQL
A powerful, open-source relational database system used to store and manage structured data like users, bookings, payments, and property details.

### 🔎 GraphQL
A query language for APIs that allows clients to request only the data they need. It is used to offer a more efficient, flexible alternative to traditional REST endpoints.

### 🕒 Celery
An asynchronous task queue/job queue system used for handling background tasks such as sending booking confirmation emails or processing payments without blocking the main application flow.

### 🚀 Redis
An in-memory data store used as a caching layer to speed up data access and improve performance. Also used by Celery as a message broker for task management.

### 🐳 Docker
A containerization platform used to create reproducible, isolated environments for development and deployment, ensuring consistency across all stages of the project lifecycle.

### 🔄 CI/CD Pipelines (GitHub Actions or similar)
Continuous Integration and Continuous Deployment pipelines are set up to automatically test, build, and deploy the application, minimizing manual errors and improving development speed.



## 🗄️ Database Design

The database schema is designed to reflect the real-world structure and workflows of a property rental platform. Below are the core entities, their attributes, and relationships.

### 👤 Users
**Purpose:** Represents platform users, including both guests and hosts.

**Key Fields:**
- `id`: Primary key
- `username`: Unique username
- `email`: User email address
- `password`: Encrypted password
- `role`: Host or guest

**Relationships:**
- A user can list multiple properties (if a host).
- A user can make multiple bookings (if a guest).
- A user can leave multiple reviews.

---

### 🏠 Properties
**Purpose:** Represents listings created by hosts.

**Key Fields:**
- `id`: Primary key
- `title`: Name/title of the property
- `description`: Detailed description
- `location`: Address or city
- `price_per_night`: Cost of one night

**Relationships:**
- A property belongs to one user (host).
- A property can have multiple bookings.
- A property can receive multiple reviews.

---

### 📅 Bookings
**Purpose:** Represents a guest’s reservation of a property.

**Key Fields:**
- `id`: Primary key
- `user_id`: Foreign key (guest)
- `property_id`: Foreign key (property)
- `start_date`: Check-in date
- `end_date`: Check-out date

**Relationships:**
- A booking is made by one user.
- A booking is for one property.
- A booking can have one payment record.

---

### 💳 Payments
**Purpose:** Represents payment details for a booking.

**Key Fields:**
- `id`: Primary key
- `booking_id`: Foreign key
- `amount`: Payment amount
- `status`: Paid, pending, failed
- `transaction_date`: Date of transaction

**Relationships:**
- A payment is linked to one booking.

---

### ✍️ Reviews
**Purpose:** Represents reviews submitted by users for properties.

**Key Fields:**
- `id`: Primary key
- `user_id`: Foreign key (reviewer)
- `property_id`: Foreign key
- `rating`: Numerical rating
- `comment`: Review text

**Relationships:**
- A review is written by one user.
- A review is linked to one property.


