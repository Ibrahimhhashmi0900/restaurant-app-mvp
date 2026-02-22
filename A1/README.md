# 🍽️ Restaurant App MVP

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![React Native](https://img.shields.io/badge/React%20Native-MVP-green)
![Status](https://img.shields.io/badge/status-in%20development-yellow)

## 📋 Table of Contents
- [Project Overview](#project-overview)
- [Repository Structure](#repository-structure)
- [Assignment 1 Deliverables](#assignment-1-deliverables)
  - [1. Software Requirements Specification (SRS)](#1-software-requirements-specification-srs)
  - [2. UML Diagrams](#2-uml-diagrams)
  - [3. MVP Frontend Specifications](#3-mvp-frontend-specifications)
- [Installation Guide](#installation-guide)
- [Student Information](#student-information)
- [Submission Checklist](#submission-checklist)

---

## 🎯 Project Overview

The **Restaurant App MVP** is a mobile application designed to revolutionize the dining experience by allowing customers to browse menus, check table availability, make reservations, and place pickup orders directly from their phones. Restaurant managers can efficiently manage their digital menu, reservations, and orders through a dedicated interface.

### Problem Statement
- **Customers** face long queues and want to ensure their food is ready when they arrive
- **Restaurant Managers** struggle with phone-in orders and inefficient reservation management

### Solution
A dedicated mobile app that bridges the gap between customers and restaurants, digitizing the entire dining experience.

---

## 📁 Repository Structure
restaurant-app-mvp/
├── 📄 README.md # This file - project documentation
├── 📁 A1/ # Assignment 1 - SRS and UML Diagrams
│ ├── 📄 SRS.md # Complete Software Requirements Specification
│ └── 📁 uml-diagrams/ # UML Diagrams folder
│ ├── 🖼️ use_case_diagram.png # Use Case Diagram
│ ├── 🖼️ class_diagram.png # Class Diagram
│ ├── 🖼️ sequence_diagram.png # Sequence Diagram
│ └── 🖼️ activity_diagram.png # Activity Diagram
└── (React Native app will be added in Assignment 2)


---

## 📚 Assignment 1 Deliverables

### 1. Software Requirements Specification (SRS)

**File Location:** [`A1/SRS.md`](./A1/SRS.md)

The SRS document provides a comprehensive overview of the restaurant app requirements and includes:

#### 📑 Document Sections

| Section | Description |
|---------|-------------|
| **1. Introduction** | Purpose, scope, definitions, and acronyms |
| **2. Overall Description** | User roles, permissions, and user stories |
| **3. Functional Requirements** | 14 detailed requirements with IDs FR-01 to FR-14 |
| **4. Non-Functional Requirements** | 6 requirements with IDs NFR-01 to NFR-06 |
| **5. Database Schema** | NoSQL collections for users, menuItems, reservations, orders |
| **6. UML Diagrams** | References to all UML diagrams |
| **7. MVP Frontend** | Specifications for 6 core screens |

#### 👥 User Roles

| Role | Key Permissions | Goals |
|------|-----------------|-------|
| **Customer** | Browse menu, view specials, check availability, make reservations, place orders | Save time, avoid queues, seamless experience |
| **Restaurant Manager** | Manage menu, view reservations, update order status | Reduce phone-in orders, efficient management |

#### 📊 Functional Requirements Summary

| ID | Requirement | User Role |
|----|-------------|-----------|
| FR-01 | User Registration/Login | All |
| FR-02 | Browse Menu | Customer |
| FR-03 | View Daily Specials | Customer |
| FR-04 | Check Availability | Customer |
| FR-05 | Make a Reservation | Customer |
| FR-06 | Place Pickup Order | Customer |
| FR-07 | View My Orders/Reservations | Customer |
| FR-08 | Cancel Reservation/Order | Customer |
| FR-09 | Manager Login | Manager |
| FR-10 | Manage Menu | Manager |
| FR-11 | View Reservations | Manager |
| FR-12 | Update Reservation Status | Manager |
| FR-13 | View Pickup Orders | Manager |
| FR-14 | Update Order Status | Manager |

#### 💾 Database Schema (NoSQL)

| Collection | Purpose | Key Fields |
|------------|---------|------------|
| **users** | Store user profiles | userId, email, name, role |
| **menuItems** | Store menu information | itemId, name, price, category, isSpecial |
| **reservations** | Store table bookings | reservationId, customerId, date, time, partySize, status |
| **orders** | Store pickup orders | orderId, customerId, items, totalAmount, pickupTime, status |

---

### 2. UML Diagrams

**File Location:** [`A1/uml-diagrams/`](./A1/uml-diagrams/)

#### 📊 Diagram 1: Use Case Diagram
**Filename:** `use_case_diagram.png`

This diagram illustrates the high-level interactions between actors (Customer and Restaurant Manager) and the system's functionalities.

**Actors:**
- 👤 **Customer** - Can register/login, browse menu, view specials, check availability, make reservations, place orders
- 👤 **Restaurant Manager** - Can login, manage menu, view reservations, update order status

**Use Cases:**
- Customer System (9 use cases)
- Manager System (4 use cases)

#### 📊 Diagram 2: Class Diagram
**Filename:** `class_diagram.png`

This diagram shows the static structure of the system with classes, attributes, methods, and relationships.

**Classes:**
| Class | Key Attributes | Key Methods |
|-------|---------------|-------------|
| **User** | userId, email, name, role | login(), register() |
| **MenuItem** | itemId, name, price, category | updatePrice(), toggleAvailability() |
| **Reservation** | reservationId, date, time, partySize, status | confirm(), cancel() |
| **Order** | orderId, items, totalAmount, status | calculateTotal(), updateStatus() |

**Relationships:**
- User 1 --- * Reservation (One user can have many reservations)
- User 1 --- * Order (One user can have many orders)
- Order 1 --- * MenuItem (One order contains many menu items)

#### 📊 Diagram 3: Sequence Diagram
**Filename:** `sequence_diagram.png`

This diagram depicts the sequence of interactions for a customer placing a pickup order.

**Lifelines:**
- :Customer
- :AppUI
- :OrderController
- :Database

**Message Flow:**
1. Customer adds item to cart
2. Customer places order
3. AppUI calls OrderController to create order
4. OrderController saves order to Database
5. Database confirms save
6. OrderController confirms to AppUI
7. AppUI shows confirmation to Customer

#### 📊 Diagram 4: Activity Diagram
**Filename:** `activity_diagram.png`

This diagram models the workflow of the table reservation process from start to finish.

**Flow:**
- Start → Check Availability → Decision [Available?]
  - **YES Branch:** Create Reservation → Pending → Manager Confirms → Confirmed → Customer Arrives → Completed → End
  - **NO Branch:** Show Alternative Times → Back to Check Availability

---

### 3. MVP Frontend Specifications

The React Native app (to be developed in Assignment 2) will include these screens:

#### 📱 Screen 1: Login/Signup Screen
- Email and password fields
- Toggle between Login and Sign Up
- Role selection (Customer/Manager) during sign-up
- Forgot password link
- Navigation to appropriate home screen

#### 📱 Screen 2: Customer Home Screen
- Welcome banner with personalized greeting
- Daily Specials carousel with images and prices
- Quick action buttons: "Book a Table" and "Order for Pickup"
- My Activity section showing upcoming reservations/orders

#### 📱 Screen 3: Menu Browsing Screen
- Category tabs (All, Appetizers, Mains, Desserts, Drinks)
- Vertically scrollable menu list
- Each item shows name, description, price, and "Add to Cart"
- Search bar to find specific items

#### 📱 Screen 4: Reservation Screen
- Date picker
- Time picker
- Party size selector (+/-)
- Availability check button
- Confirmation screen with booking details

#### 📱 Screen 5: Order Cart & Checkout Screen
- Cart list with items, quantities, and running total
- Pickup time selector
- Place order button
- Order confirmation screen

#### 📱 Screen 6: Manager Dashboard Screen
- Tab bar for Menu Management, Reservations, Orders
- Menu Management: List with Edit/Delete icons, Add New Item button
- Reservations: List with status update buttons (Confirm, Cancel)
- Orders: List with status update buttons (Mark as Ready)

---

## 🚀 Installation Guide

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- React Native CLI or Expo CLI
- Android Studio (for Android development) or Xcode (for iOS development)

### Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/restaurant-app-mvp.git
cd restaurant-app-mvp

# The A1 folder contains all documentation
cd A1
# Open SRS.md to view requirements
# Open uml-diagrams/ to view all UML diagrams

# Install dependencies
npm install

# Run on iOS
npx react-native run-ios
# OR
expo start --ios

# Run on Android
npx react-native run-android
# OR
expo start --android
