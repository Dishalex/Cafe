# Frontend Sketches for Cafe

### 1. Home Page
The landing page for all users. Displays a welcome message and basic navigation options.
```
---------------------------------------------------------
| Cafe - Restaurant Management System                   |
---------------------------------------------------------
| Home | Menu | Orders | Account                         |
---------------------------------------------------------
| Welcome to Cafe!                                      |
| Please choose an option from the menu above.          |
---------------------------------------------------------
```
### 2. Menu Page
Displays the list of available dishes in different menus (Permanent, Daily, Buffet).
```
---------------------------------------------------------
| Cafe - Restaurant Management System                   |
---------------------------------------------------------
| Home | Menu | Orders | Account                         |
---------------------------------------------------------
| Menu                                                   |
|-------------------------------------------------------|
| Permanent Menu     | Daily Menu        | Buffet Menu   |
---------------------------------------------------------
| Dish Name | Calories | Price | Add to Order           |
|-------------------------------------------------------|
| Dish 1    | 250      | $10   | [Add to Order]         |
| Dish 2    | 300      | $12   | [Add to Order]         |
| Dish 3    | 150      | $8    | [Add to Order]         |
---------------------------------------------------------
```
### 3. Orders Page
Allows users to view and manage their current and past orders.
```
---------------------------------------------------------
| Cafe - Restaurant Management System                   |
---------------------------------------------------------
| Home | Menu | Orders | Account                         |
---------------------------------------------------------
| Orders                                                 |
|-------------------------------------------------------|
| Order ID | Date       | Status     | Total   | Details|
|-------------------------------------------------------|
| 12345    | 2023-07-01 | Confirmed  | $30     | [View] |
| 12346    | 2023-07-02 | Pending    | $25     | [View] |
| 12347    | 2023-07-03 | Completed  | $40     | [View] |
---------------------------------------------------------
| [Create New Order]                                     |
---------------------------------------------------------
```
### 4. Account Page
Displays user account details and options for managing account settings.
```
---------------------------------------------------------
| Cafe - Restaurant Management System                   |
---------------------------------------------------------
| Home | Menu | Orders | Account                         |
---------------------------------------------------------
| Account                                                |
|-------------------------------------------------------|
| Username: [username]                                   |
| Email: [email@example.com]                             |
| Role: [User Role]                                      |
|-------------------------------------------------------|
| [Edit Profile] [Change Password] [Logout]              |
---------------------------------------------------------
```
### 5. Admin Dashboard (Administrator Role)
A dashboard for administrators to manage the system, including users, reports, and settings.
```
---------------------------------------------------------
| Cafe - Restaurant Management System                   |
---------------------------------------------------------
| Home | Menu | Orders | Account | Dashboard             |
---------------------------------------------------------
| Dashboard                                              |
|-------------------------------------------------------|
| [Manage Users] [View Reports] [System Settings]        |
---------------------------------------------------------
| Total Orders: 100                                      |
| Total Revenue: $5000                                   |
| Pending Orders: 5                                      |
---------------------------------------------------------
| [View All Orders]                                      |
---------------------------------------------------------
```
### 6. Chef Dashboard (Chef Role)
A dashboard for chefs to manage dishes, ingredients, and kitchen orders.
```
---------------------------------------------------------
| Cafe - Restaurant Management System                   |
---------------------------------------------------------
| Home | Menu | Orders | Account | Kitchen               |
---------------------------------------------------------
| Kitchen                                                |
|-------------------------------------------------------|
| [Manage Dishes] [Manage Ingredients] [View Orders]     |
---------------------------------------------------------
| Dish Name | Stock  | Actions                           |
|-------------------------------------------------------|
| Dish 1    | 10     | [Edit] [Delete]                   |
| Dish 2    | 5      | [Edit] [Delete]                   |
| Dish 3    | 20     | [Edit] [Delete]                   |
---------------------------------------------------------
| [Add New Dish]                                         |
---------------------------------------------------------
```
### 7. Bar Interface (Bar Role)
Interface for bar staff to manage and process orders from guests and staff.
```
---------------------------------------------------------
| Cafe - Restaurant Management System                   |
---------------------------------------------------------
| Home | Menu | Orders | Account | Bar                   |
---------------------------------------------------------
| Bar Interface                                          |
|-------------------------------------------------------|
| Scan QR Code: [Scan Button]                            |
---------------------------------------------------------
| Order ID: 12345                                        |
| User: John Doe                                         |
| Items:                                                 |
| - Dish 1 (2)                                           |
| - Dish 2 (1)                                           |
| Total: $30                                             |
---------------------------------------------------------
| [Confirm Order] [Edit Order] [Process Payment]         |
---------------------------------------------------------
```
### 8. Kitchen Interface (Kitchen Role)
Interface for kitchen staff to view and update the status of orders.
```
---------------------------------------------------------
| Cafe - Restaurant Management System                   |
---------------------------------------------------------
| Home | Menu | Orders | Account | Kitchen               |
---------------------------------------------------------
| Kitchen Interface                                      |
|-------------------------------------------------------|
| Order ID | Dish Name | Quantity | Status               |
|-------------------------------------------------------|
| 12345    | Dish 1    | 2        | Preparing            |
| 12346    | Dish 2    | 1        | Completed            |
| 12347    | Dish 3    | 3        | Pending              |
---------------------------------------------------------
| [Update Order Status]                                  |
---------------------------------------------------------
```
