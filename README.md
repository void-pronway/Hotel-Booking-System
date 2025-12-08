# 🏨 Hotel Reservation System

A full-stack **Hotel Reservation System** built with **Spring Boot (backend)** and **Angular (frontend)**.  
The system allows **users** to search and book rooms and **admins** to manage rooms, bookings, and reports.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
  - [Backend Structure (Spring Boot)](#backend-structure-spring-boot)
  - [Frontend Structure (Angular)](#frontend-structure-angular)
- [How to Run the Backend](#how-to-run-the-backend)
- [How to Run the Frontend](#how-to-run-the-frontend)
- [Backend: Controllers & Layers](#backend-controllers--layers)
- [Features in Detail](#features-in-detail)
  - [Room Management (Member 1)](#room-management-member-1)
  - [Booking Management (Member-2)](#booking-management-member-2)
  - [Search--availability-member-3](#search--availability-member-3)
  - [User--guest-management-member-4](#user--guest-management-member-4)
  - [Admin--reporting-member-5](#admin--reporting-member-5)
- [Database Setup](#database-setup)
- [Backend Configuration (applicationproperties)](#backend-configuration-applicationproperties)
- [Sample API Endpoints](#sample-api-endpoints)
- [Future Improvements](#future-improvements)

---

## 🔍 Overview

The **Hotel Reservation System** supports:

- Managing **rooms** (CRUD, status, filtering)
- Creating and managing **bookings** with date validation
- Searching room **availability** by date, type, capacity, and price
- Managing **users/guests** (register, profile, soft delete, booking history)
- **Admin** features like daily reports, booking statistics, and revenue reports

The project is structured to follow **OOP principles** and a **layered architecture**:

- **Frontend**: Angular (SPA)
- **Backend**: Spring Boot REST API
- **Database**: MySQL (or in-memory for testing)

---

## 🧰 Tech Stack

### Backend

- Java (17+ recommended)
- Spring Boot
- Spring Web
- Spring Data JPA (Hibernate)
- MySQL
- Maven

### Frontend

- Angular
- TypeScript
- HTML / SCSS
- Angular Router

---

## 🗂 Project Structure

### Backend Structure (Spring Boot)

```text
backend/
 └── src/
     └── main/
         ├── java/
         │   └── com/example/hotel
         │       ├── controller/
         │       │    ├── RoomController.java
         │       │    ├── BookingController.java
         │       │    ├── UserController.java
         │       │    └── AdminController.java
         │       ├── service/
         │       │    ├── RoomService.java
         │       │    ├── BookingService.java
         │       │    ├── UserService.java
         │       │    └── ReportService.java
         │       ├── repository/
         │       │    ├── RoomRepository.java
         │       │    ├── BookingRepository.java
         │       │    └── UserRepository.java
         │       ├── model/
         │       │    ├── Room.java
         │       │    ├── Booking.java
         │       │    ├── User.java
         │       │    ├── Customer.java
         │       │    └── Admin.java
         │       └── HotelApplication.java
         └── resources/
             ├── application.properties
             └── static/



frontend/
 └── src/
     ├── app/
     │   ├── components/
     │   │   ├── room-list/
     │   │   ├── room-form/
     │   │   ├── booking-list/
     │   │   ├── booking-form/
     │   │   ├── user-profile/
     │   │   └── admin-dashboard/
     │   ├── pages/
     │   │   ├── home/
     │   │   ├── search/
     │   │   ├── bookings/
     │   │   └── admin/
     │   ├── services/
     │   │   ├── room.service.ts
     │   │   ├── booking.service.ts
     │   │   ├── user.service.ts
     │   │   └── report.service.ts
     │   ├── app-routing.module.ts
     │   └── app.component.ts
     ├── assets/
     └── index.html


▶️ How to Run the Backend

Go to the backend folder:

cd backend


Build the project (optional, but good to confirm):

mvn clean install


Run the Spring Boot application:

mvn spring-boot:run


Backend will be available at:

http://localhost:8080

💻 How to Run the Frontend

Go to the frontend folder:

cd frontend


Install dependencies:

npm install


Start the Angular development server:

npm start


or

ng serve


Frontend will be available at:

http://localhost:4200

🧱 Backend: Controllers & Layers
Controller Layer

Handles HTTP requests and maps them to service methods.

RoomController

Handles /api/rooms endpoints (CRUD, filters)

BookingController

Handles /api/bookings endpoints (create, update, cancel, list)

UserController

Handles /api/users endpoints (register, update, soft delete, history)

AdminController

Handles /api/admin endpoints (reports, booking status changes)

Service Layer

Contains business logic.

RoomService

Validations and logic related to rooms

BookingService

Date validation, overlap prevention, booking status

UserService

User management, profile changes, soft delete

ReportService

Daily bookings, revenue, booking counts

Repository Layer

Handles database operations via Spring Data JPA.

RoomRepository

BookingRepository

UserRepository

🧩 Features in Detail
Room Management (Member 1)

Handled by:

Room (model)

RoomRepository

RoomService

RoomController

Features:

Add new room

Admin can create a room with type, price, capacity, and status.

Edit room details

Update price, room type, and capacity.

Delete room

Soft delete or hard delete depending on design.

List rooms filtered by type

Example: Single, Double, Suite.

Mark room as “out of service”

Change room status (e.g., AVAILABLE, BOOKED, OUT_OF_SERVICE).

Booking Management (Member 2)

Handled by:

Booking (model)

BookingRepository

BookingService

BookingController

Features:

Create booking (with date validation)

Ensure checkInDate < checkOutDate.

Ensure room is available in that date range.

Cancel booking

Change status to CANCELLED and free the room if needed.

Update booking dates (reschedule)

Re-validate dates & room availability.

List bookings by user

Get all bookings for a given user ID.

Prevent double booking

Reject creation if room is already booked for overlapping dates.

Search & Availability (Member 3)

Handled by:

RoomService

BookingService

RoomController / dedicated SearchController (optional)

Features:

Search available rooms by date range

Returns rooms not booked in the given date range.

Filter by room type & capacity

Query by roomType and capacity.

Show price range filter

Filter by min and max price.

Next available date

If room not available, suggest the next date where it becomes free.

Paginated room listing

Implement pagination parameters: page, size.

User / Guest Management (Member 4)

Handled by:

User, Customer (models)

UserRepository

UserService

UserController

Features:

Register user

Create new customer with name, email, phone, etc.

Update user profile

Edit name, email, phone.

Soft delete user (mark inactive)

Add active flag and set it to false.

View user’s booking history

Fetch all bookings related to a user.

Basic login simulation

Very simple login (e.g., by username or email, no real security).

Admin / Reporting (Member 5)

Handled by:

Admin (model)

ReportService

AdminController

BookingRepository

Features:

View all bookings for a particular day

Filter bookings by bookingDate or checkInDate.

Report: number of bookings per room

Group bookings by roomId and count.

Report: revenue per day/week

Sum totalPrice for a date range.

Change booking status

Admin can set PENDING, CONFIRMED, CANCELLED, etc.

Auditing

Store createdAt and updatedAt in entities.

🗄 Database Setup

Open MySQL or your DB tool.

Create the database:

CREATE DATABASE hotel_db;


Make sure the same database name is referenced in application.properties.

⚙️ Backend Configuration (application.properties)
spring.datasource.url=jdbc:mysql://localhost:3306/hotel_db?useSSL=false&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.database-platform=org.hibernate.dialect.MySQLDialect


Change username and password if your MySQL credentials are different.

🔗 Sample API Endpoints
Room Endpoints
GET    /api/rooms
GET    /api/rooms/{id}
POST   /api/rooms
PUT    /api/rooms/{id}
DELETE /api/rooms/{id}
GET    /api/rooms/type/{type}
GET    /api/rooms/available?from=yyyy-mm-dd&to=yyyy-mm-dd

Booking Endpoints
POST   /api/bookings
GET    /api/bookings/{id}
GET    /api/bookings/user/{userId}
PUT    /api/bookings/{id}
DELETE /api/bookings/{id}

User Endpoints
POST   /api/users/register
PUT    /api/users/{id}
DELETE /api/users/{id}       // soft delete
GET    /api/users/{id}/bookings
POST   /api/users/login      // simple login simulation

Admin / Report Endpoints
GET  /api/admin/reports/bookings?date=yyyy-mm-dd
GET  /api/admin/reports/bookings-per-room
GET  /api/admin/reports/revenue?from=yyyy-mm-dd&to=yyyy-mm-dd
PUT  /api/admin/bookings/{id}/status?value=CONFIRMED

🚀 Future Improvements

Proper authentication & authorization (JWT)

Payment integration (e.g., Stripe)

File upload for room images

Email notifications (booking confirmation, reminders)

Advanced search and filtering UI in Angular
