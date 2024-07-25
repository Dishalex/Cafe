# Cafe
Restaurant Management System

## Project Overview
The project is a restaurant order management system that allows efficient organization of staff workflows, control of product and dish inventory, and processing of orders from guests and employees. The system is implemented using modern technologies such as FastAPI for the backend, PostgreSQL for the database, and Docker for containerization.

## Technology Stack
- **Programming Language**: Python
- **Framework**: FastAPI (asynchronous)
- **Database**: PostgreSQL
- **Containerization**: Docker
- **Dependency Management Tools**: Poetry
- **User Interfaces**: Web application and integration with Telegram

## User Roles
- **Administrator**
- **Chef**
- **Bar**
- **Kitchen**
- **Staff**
- **Guest**

### Chef
- Adds products for dish preparation (table "Products" includes name, caloric content, unit of measurement).
- Creates dishes (table "Dishes" is expandable. Each entry has properties: composition (linked to products), caloric content per serving (calculated based on the products table), photo, available quantity in stock).
- Creates and edits the list of dishes for the "Permanent Menu" that rarely changes.
- Creates and edits the list of dishes for the "Daily Menu" for a week ahead.
- Creates and edits the list of dishes for the "Buffet Menu" for a week ahead.
- Receives a summary table of orders for the next day.
- Forms kitchen orders for the preparation of a list of dishes with calculated quantities of necessary products.
- Receives/edits reports on product and production balances.

### Administrator
- Generates reports on completed orders.
- Generates reports on the number of meals purchased and calculates compensation from the enterprise.
- Creates and edits the list of dishes for each menu.

### Staff
- Selects orders for the next day from the available menu in the application (positions and quantities).
- Generates a QR code from the application for quick identification and ordering at the bar.

### Guest
- Selects orders from the available menu.
- Generates a QR code from the application for quick ordering at the bar.

### Bar (Order Reception in Restaurant)
- Scans the user's QR code or reads the pass and receives information about their order.
- Creates/edits the user's order (staff/guest).
- Tops up the staff account by indicating the paid amount.
- Confirms the order for fulfillment if the user's balance is positive.
- Receives payment (cash or card) if the user's balance is insufficient, updates the user's balance, and confirms the order for fulfillment.
- Prints a receipt with order information.

### Kitchen
- Views orders from the chef for dish preparation (name, quantity).
- Receives information about order issuance.
- Marks the order as OK after issuance.
- Prints a receipt with items to be issued (result of the confirmed order at the restaurant reception).

### Equipment
- Touchscreen terminal at reception
- Touchscreen terminal in the kitchen
- Receipt printer at reception
- Receipt printer in the kitchen
- Each menu has its own history of position and price changes.

### Order History
- Date, time, user, order, status

# Development Environment

### .env File
Create your own `.env` file based on `deploy/env-examples` with your variables.

<details>
  <summary>LOCAL DEVELOPMENT</summary>

- Git repository: https://github.com/Dishalex/Rest, default branch `dev`
- Each developer creates their own branches from `dev` and updates them through `merge`. Branch naming convention: `username` for permanent branches, `username-feature` for temporary branches, which are deleted after merging.
- Merge to `dev` only through `pull-request`.
- Python >=3.10, <=3.12
- Poetry
- `.cmd` scripts for Windows.
- `.sh` scripts for Linux and Mac.
- The root Git project contains several independent subprojects:
    - BACKEND
    - FRONTEND
    - DATABASE
- Each subproject is an independent product and has its own Docker.
- They communicate through a shared database, which can be local (Docker) or remote (elephantsql) during development.
- Environment variable settings are shared in the `/deploy/.env` file. Local development uses only the relative path to this file.
- **Security**: Each Docker container takes only the necessary settings from the `.env` file, not the entire file. Place the `.env` file outside the Docker container.
- FRONTEND and BACKEND each have their own virtual environment managed by Poetry.

### To work with FRONTEND:

```
cd FRONTEND
poetry shell
poetry update
```
### To work with BACKEND:
```
cd BACKEND
poetry shell
poetry update
```

If using VS Code Workspace, add subprojects to it (File->Add folder to Workspace).
When launching the terminal, specify the directory.

#### For a local database, follow these steps:
```
scripts/docker_db.cmd
```
Database data will be created in `Database/postgres-data/` (excluded from Git).

To stop the database:
```
scripts/docker_db_stop.cmd
```

### Running and Maintaining the Application in Docker

#### To run the app locally:
```
cd BACKEND
uvicorn src.main --reload
```
#### To export Poetry packages to `requirements.txt`:
```
cd BACKEND
poetry export --without-hashes > requirements.txt
```
#### Or use the script:
```
scripts/gen_req_txt.cmd
```
#### To migrate database changes:
```
cd FRONTEND/cafe
python manage.py migrate
```

#### To run the entire project with subprojects in Docker:
```
scripts/docker_app_run.cmd
```

### <summary>Procedures for Initial Dev Setup</summary>

1. git checkout dev
2. git pull
3. cd FRONTEND
4. poetry shell
5. poetry update
6. cd ..
7. cd scripts
8. docker_db.cmd - run DB local docker, skip if remote used postgres
9. migrate_dev_app.cmd - migrate DB
10. run_dev_app.cmd - run app
11. open browser: http://127.0.0.1:8000


#### On the server, the project is executed in several `docker` containers, which are united by the settings file: `deploy\docker-compose-project.yml`.
