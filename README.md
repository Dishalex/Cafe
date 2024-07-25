# Cafe
Restaraunt managment system

# Project Overview: Restaurant Order Management System

## Introduction
The project is a restaurant order management system that allows efficient organization of staff workflows, control of product and dish inventory, and processing of orders from guests and employees. The system is implemented using modern technologies such as FastAPI for the backend, PostgreSQL for the database, and Docker for containerization.

## Technology Stack
- Programming Language: Python
- Framework: FastAPI (asynchronous)
- Database: PostgreSQL
- Containerization: Docker
- Dependency Management Tools: Poetry
- User Interfaces: Web application and integration with Telegram

## Main Roles and Their Functions

1. **Administrator**
   - Generate reports on completed orders.
   - Generate reports on the number of meals purchased and calculate compensation.
   - Create and edit dish lists for all menus.

2. **Chef**
   - Add ingredients for dish preparation.
   - Create and edit dishes, their composition, and caloric content.
   - Manage product and dish inventory.
   - Create menus (permanent, daily, buffet).
   - Formulate kitchen orders and manage product inventory.

3. **Staff**
   - Select orders for the next day from the available menu.
   - Generate QR codes for order identification at the bar.

4. **Guest**
   - Select orders from the available menu.
   - Generate QR codes for quick ordering at the bar.

5. **Bar (Order Reception in Restaurant)**
   - Scan QR codes or read passes to obtain order information.
   - Create and edit user orders.
   - Top up user accounts and confirm orders for fulfillment.
   - Print receipts with order information.

6. **Kitchen**
   - View orders from the chef.
   - Issue orders and update their status.
   - Print receipts with items to be issued.
