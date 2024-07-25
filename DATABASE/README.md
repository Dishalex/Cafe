# Database Schema and Relationships
This section provides an overview of the database schema and the relationships between various models in the Cafe restaurant management system.

## Summary of Key Relationships
- **Users ↔ Orders:** Each user can place multiple orders.
- **Orders ↔ OrderItems:** Each order consists of multiple order items.
- **OrderItems ↔ Dishes:** Each order item links to a specific dish.
- **Dishes ↔ DishProducts:** Each dish is composed of multiple products.
- **Menus ↔ Dishes:** Each menu contains multiple dishes.
- **OrderHistory:** Tracks changes in order status over time.
- **MenuHistory:** Records changes to menu contents and prices.

## 1. Users
- **Table**: Users
- **Fields**: id (PK), username, email, password_hash, role (Enum: Administrator, Chef, Bar, Kitchen, Staff, Guest), balance
- **Description**: Each user has a role that determines their permissions and functionalities within the system.
## 2. Products
- **Table**: Products
- **Fields**: id (PK), name, calories, unit, quantity
- **Description**: Managed by the Chef, these are the ingredients used to prepare dishes.
## 3. Dishes
- **Table**: Dishes
- **Fields**: id (PK), name, calories, photo, stock, menu_id (FK), chef_id (FK)
- **Description**: Created and managed by the Chef, each dish is associated with one or more products (many-to-many relationship via the DishProducts table).
## 4. DishProducts
- **Table**: DishProducts
- **Fields**: id (PK), dish_id (FK), product_id (FK), quantity
- **Description**: This table links dishes to products, specifying the quantity of each product used in a dish.
## 5. Menus
- **Table**: Menus
- **Fields**: id (PK), name (Enum: Permanent, Daily, Buffet), start_date, end_date
- **Description**: There are three types of menus: Permanent, Daily, and Buffet. Each menu contains multiple dishes.
## 6. Orders
- **Table**: Orders
- **Fields**: id (PK), user_id (FK), status (Enum: Pending, Confirmed, Completed), total, created_at, updated_at
- **Description**: An order can be placed by a staff member or guest and consists of multiple order items (many-to-one relationship).
## 7. OrderItems
- **Table**: OrderItems
- **Fields**: id (PK), order_id (FK), dish_id (FK), quantity, price
- **Description**: Links individual dishes to an order, specifying the quantity and price of each dish.
## 8. OrderHistory
- **Table**: OrderHistory
- **Fields**: id (PK), order_id (FK), status, timestamp
- **Description**: Tracks the status changes of an order over time.
## 9. MenuHistory
- **Table**: MenuHistory
- **Fields**: id (PK), menu_id (FK), dish_id (FK), price, date
- **Description**: Keeps a record of changes to the menus, including dish prices and availability.


## Database Schema

```
Users
---------
| id            | Integer (PK)
| username      | String
| email         | String
| password_hash | String
| role          | String (Enum: Administrator, Chef, Bar, Kitchen, Staff, Guest)
| balance       | Float


Products
---------
| id           | Integer (PK)
| name         | String
| calories     | Float
| unit         | String
| quantity     | Float


Dishes
---------
| id           | Integer (PK)
| name         | String
| calories     | Float (calculated)
| photo        | String (URL)
| stock        | Integer
| menu_id      | Integer (FK)
| chef_id      | Integer (FK)


DishProducts
---------
| id           | Integer (PK)
| dish_id      | Integer (FK)
| product_id   | Integer (FK)
| quantity     | Float


Menus
---------
| id           | Integer (PK)
| name         | String (Enum: Permanent, Daily, Buffet)
| start_date   | Date
| end_date     | Date


Orders
---------
| id           | Integer (PK)
| user_id      | Integer (FK)
| status       | String (Enum: Pending, Confirmed, Completed)
| total        | Float
| created_at   | DateTime
| updated_at   | DateTime


OrderItems
---------
| id           | Integer (PK)
| order_id     | Integer (FK)
| dish_id      | Integer (FK)
| quantity     | Integer
| price        | Float


OrderHistory
---------
| id           | Integer (PK)
| order_id     | Integer (FK)
| status       | String
| timestamp    | DateTime


MenuHistory
---------
| id           | Integer (PK)
| menu_id      | Integer (FK)
| dish_id      | Integer (FK)
| price        | Float
| date         | Date

```

## Entity-Relationship Diagram (ERD)

```
+-------------------+       +-----------------+       +----------------+      +-----------------+      +----------------+
|      Users        |       |    Products     |       |     Dishes     |      |      Menus      |      |     Orders     |
+-------------------+       +-----------------+       +----------------+      +-----------------+      +----------------+
| id (PK)           |       | id (PK)         |       | id (PK)        |      | id (PK)         |      | id (PK)        |
| username          |       | name            |       | name           |      | name            |      | user_id (FK)   |
| email             |       | calories        |       | calories       |      | start_date      |      | status         |
| password_hash     |       | unit            |       | photo          |      | end_date        |      | total          |
| role              |       | quantity        |       | stock          |      +-----------------+      | created_at     |
| balance           |       +-----------------+       | menu_id (FK)   |                             | updated_at     |
+-------------------+                                  | chef_id (FK)   |      +-----------------+      +----------------+
                                                       +----------------+      |  OrderItems    |
                                                                               +-----------------+
+-----------------+     +-----------------+     +-------------------+          | id (PK)        |
| DishProducts    |     |  OrderHistory   |     |   MenuHistory     |          | order_id (FK)  |
+-----------------+     +-----------------+     +-------------------+          | dish_id (FK)   |
| id (PK)         |     | id (PK)         |     | id (PK)           |          | quantity       |
| dish_id (FK)    |     | order_id (FK)   |     | menu_id (FK)      |          | price          |
| product_id (FK) |     | status          |     | dish_id (FK)      |          +-----------------+
| quantity        |     | timestamp       |     | price             |
+-----------------+     +-----------------+     | date              |
                                                +-------------------+

```