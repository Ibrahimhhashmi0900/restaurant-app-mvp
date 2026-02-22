# Software Requirements Specification (SRS) for Restaurant App MVP

## 1. Introduction

### 1.1. Purpose
This document provides a detailed overview of the software requirements for the development of the Restaurant App MVP (Minimum Viable Product). It outlines the purpose, features, functionalities, and behavior of the application. This document is intended for the development team, stakeholders, and testers to ensure a shared understanding of the project's scope and goals.

### 1.2. Scope
The initial version (MVP) of the Restaurant App will serve two primary user roles: Customers and Restaurant Managers. The app will focus on streamlining the dining experience by digitizing core operations.

The following functionalities are in scope for the initial version:
- User Authentication: Secure sign-up and login for Customers and Restaurant Managers.
- Customer Features:
    - Browse the digital menu with items, descriptions, and prices.
    - View daily specials.
    - Check real-time table availability for a desired date and time.
    - Make, view, and cancel table reservations.
    - Place a food order for pickup.
- Restaurant Manager Features:
    - Secure login to an admin interface.
    - Manage menu items (add, edit, delete) including item name, description, price, and category.
    - View and manage incoming reservations (confirm, cancel).
    - View and manage incoming pickup orders (mark as ready, complete).
- System Features:
    - Notifications (in-app or push) to confirm reservation/order status.

### 1.3. Definitions and Acronyms
- MVP: Minimum Viable Product
- SRS: Software Requirements Specification
- UI: User Interface
- UX: User Experience
- NoSQL: A non-relational database type (e.g., MongoDB, Firestore)
- Customer: An end-user of the app looking to dine at or order from the restaurant
- Restaurant Manager: A staff member responsible for managing the restaurant's digital presence within the app

## 2. Overall Description

### 2.1. User Roles

| Role | Key Permissions & Goals |
| :--- | :--- |
| **Customer** | **Permissions:** Browse menu, view specials, check table availability, make reservations, place pickup orders. <br><br> **Goals:** Save time, avoid queues, ensure food is ready upon arrival, have a convenient and seamless dining experience. |
| **Restaurant Manager** | **Permissions:** Log in to admin panel, manage menu items, view and manage all reservations and orders. <br><br> **Goals:** Reduce phone-in orders, manage reservations efficiently, easily update the digital menu, reduce operational workload. |

### 2.2. User Stories
- As a Customer, I want to view the daily specials so that I can decide what to order quickly.
- As a Customer, I want to check table availability for 7:00 PM so that I know if I can book a table.
- As a Customer, I want to place an order for pickup so that my food is ready when I arrive and I don't have to wait in line.
- As a Restaurant Manager, I want to log in securely so that I can access the restaurant's management features.
- As a Restaurant Manager, I want to easily update the menu (prices, descriptions, items) so that customers always see accurate information.
- As a Restaurant Manager, I want to see a list of all reservations for the day so that I can prepare the seating chart accordingly.

## 3. Functional Requirements

| ID | Requirement | Description | User Role |
| :--- | :--- | :--- | :--- |
| FR-01 | User Registration/Login | The system shall allow users (Customer/Manager) to register and log in using an email and password. | All |
| FR-02 | Browse Menu | The system shall display a list of menu items, organized by category (e.g., Appetizers, Mains, Desserts, Drinks). | Customer |
| FR-03 | View Daily Specials | The system shall highlight a dedicated section for daily specials on the home screen. | Customer |
| FR-04 | Check Availability | The system shall allow a customer to select a date and time and display available tables. | Customer |
| FR-05 | Make a Reservation | The system shall allow a customer to book an available table by providing name, phone number, and party size. | Customer |
| FR-06 | Place Pickup Order | The system shall allow a customer to select items from the menu, add them to a cart, and place an order for pickup at a specific time. | Customer |
| FR-07 | View My Orders/Reservations | The system shall allow a customer to view their upcoming and past reservations and orders. | Customer |
| FR-08 | Cancel Reservation/Order | The system shall allow a customer to cancel an upcoming reservation or order. | Customer |
| FR-09 | Manager Login | The system shall provide a separate login flow for Restaurant Managers. | Manager |
| FR-10 | Manage Menu | The system shall allow a manager to add, edit, or delete menu items (name, description, price, category, image URL). | Manager |
| FR-11 | View Reservations | The system shall display all incoming reservations in a list, sorted by date and time. | Manager |
| FR-12 | Update Reservation Status | The system shall allow a manager to change the status of a reservation (e.g., Pending, Confirmed, Cancelled, Completed). | Manager |
| FR-13 | View Pickup Orders | The system shall display all incoming pickup orders. | Manager |
| FR-14 | Update Order Status | The system shall allow a manager to update the status of an order (e.g., Received, Preparing, Ready for Pickup, Picked Up). | Manager |

## 4. Non-Functional Requirements

| ID | Requirement | Category | Description |
| :--- | :--- | :--- | :--- |
| NFR-01 | Usability | UX | The app shall have an intuitive and clean interface. A customer should be able to book a table or place an order in under 3 minutes. |
| NFR-02 | Performance | Performance | The app should load the main menu and home screen within 2 seconds on a standard 4G connection. |
| NFR-03 | Reliability | Reliability | The system should have 99.5% uptime during peak hours (e.g., 6-9 PM). Reservation and order data must never be lost. |
| NFR-04 | Security | Security | All user passwords must be hashed. All communication between the app and backend must be encrypted via HTTPS. |
| NFR-05 | Compatibility | Platform | The React Native app must function without critical bugs on both iOS (version 14+) and Android (version 10+). |
| NFR-06 | Scalability | Scalability | The backend/database should be able to handle a 500% increase in traffic during a holiday promotion without crashing. |

## 5. Database Schema (NoSQL - e.g., Firebase Firestore)

| Collection Name | Fields | Description |
| :--- | :--- | :--- |
| users | `userId` (string, auto), `email` (string), `passwordHash` (string), `name` (string), `phone` (string), `role` (string: "customer" / "manager"), `createdAt` (timestamp) | Stores user profile and authentication data. |
| menuItems | `itemId` (string, auto), `name` (string), `description` (string), `price` (number), `category` (string), `imageUrl` (string), `isSpecial` (boolean), `isAvailable` (boolean) | Stores all information about food and drink items. |
| reservations | `reservationId` (string, auto), `customerId` (reference to users), `customerName` (string), `customerPhone` (string), `date` (string), `time` (string), `partySize` (number), `status` (string: "pending", "confirmed", "cancelled", "completed"), `createdAt` (timestamp) | Stores all table booking details. |
| orders | `orderId` (string, auto), `customerId` (reference to users), `customerName` (string), `items` (array of objects: `{itemId, name, price, quantity}`), `totalAmount` (number), `pickupTime` (string), `status` (string: "received", "preparing", "ready", "picked up"), `createdAt` (timestamp) | Stores all food pickup order details. |

## 6. UML Diagrams

The following UML diagrams have been created and are available in the `A1/uml-diagrams/` folder:
- use_case_diagram.png
- class_diagram.png
- sequence_diagram.png
- activity_diagram.png

## 7. MVP Frontend Development (React Native)

### 7.1. Login/Signup Screen
- Simple form with email and password fields
- Toggle between "Login" and "Sign Up"
- Role selection (Customer/Manager) during sign-up
- "Forgot Password?" link
- Navigation to the appropriate home screen upon successful authentication

### 7.2. Customer Home Screen (Dashboard)
- Welcome Banner: Personalized greeting ("Welcome back, [Name]!")
- Daily Specials Carousel: Horizontally scrollable list highlighting special menu items with images and prices
- Quick Actions: Prominent buttons for "Book a Table" and "Order for Pickup"
- My Activity: A short summary of the user's upcoming reservation or order status

### 7.3. Menu Browsing Screen
- Category Tabs: Tabs at the top (e.g., All, Appetizers, Mains) to filter the menu
- Menu List: A vertically scrollable list of menu items. Each item shows its name, brief description, price, and an "Add to Cart" button
- Search Bar: To find specific items by name

### 7.4. Reservation Screen
- Date & Time Picker: User-friendly selectors for choosing a date and time
- Party Size Selector: Stepper (+/-) to choose the number of people
- Availability Check Button: Triggers a check for open tables
- Confirmation Screen: Shows details and a "Confirm Booking" button

### 7.5. Order Cart & Checkout Screen
- Cart List: Displays all items added, with quantities and a running total
- Pickup Time Selector: To specify when the customer will arrive
- Place Order Button: Finalizes the order and navigates to a confirmation screen

### 7.6. Manager Dashboard Screen
- Management Tabs: A tab bar to switch between "Menu Management," "Reservations," and "Orders"
- Menu Management View: A list of all menu items with "Edit" and "Delete" icons, plus a prominent "Add New Item" button
- Reservations View: A list of all reservations for the current day, with buttons to change their status (Confirm, Cancel)
- Orders View: A list of all pending pickup orders, with buttons to update their status (Mark as Ready)
