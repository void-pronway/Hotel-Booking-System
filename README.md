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


# ▶️ How to Run the Backend

### 1️⃣ Go to the backend folder:
```bash
cd backend
mvn clean install
mvn spring-boot:run
http://localhost:8080
cd frontend
npm install
npm start
ng serve
http://localhost:4200
