# SQL
SQL stands for Structured Query Language. It is a standardized programming language used to manage and manipulate relational databases. It enables users to perform a variety of tasks such as querying data, creating and modifying database structures, and managing access permissions.
## Project Title
**Krishi Interface Database**

### Description
This repository contains the SQL database for the **Krishi Interface** application, which links to the Indian agriculture government website to fetch and display key performance indicators (KPIs) and updates for farmers. This system helps farmers stay informed with the latest agricultural data to improve their productivity and access to government programs.

### Table of Contents
1. [Project Overview](#project-overview)
2. [Tech Stack](#tech-stack)
3. [Database Setup](#database-setup)
4. [Database Schema](#database-schema)
5. [SQL Queries](#sql-queries)
6. [How to Use](#how-to-use)
7. [Contributing](#contributing)
8. [License](#license)
9. [Acknowledgements](#acknowledgements)

---

## Project Overview

**Krishi Interface Database** is a backend database system that stores and manages essential agricultural data. It links with a user interface (built using Spring Boot and Angular) and displays real-time updates from the government to farmers.

---

## Tech Stack

- **Backend**: Spring Boot (Java)
- **Frontend**: Angular (HTML, CSS)
- **Database**: MySQL
- **Authentication**: Spring Security
- **Security**: JWT (JSON Web Token)

---

## Database Setup

### Prerequisites
- MySQL or a compatible database system
- MySQL client (e.g., MySQL Workbench or command-line client)
- A database user with sufficient privileges

### Installation Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/krishi-interface.git

   Navigate to the database folder where SQL files are located:

bash
Copy
Edit
cd krishi-interface/sql
Create a new database in MySQL (if it doesn't exist):

sql
Copy
Edit
CREATE DATABASE krishi_interface;
Import the SQL schema into your MySQL database:

bash
Copy
Edit
mysql -u <username> -p krishi_interface < krishi_interface_schema.sql
Database Schema
The database consists of several important tables designed to handle various aspects of agricultural data and user management:

users

Stores user authentication details.
Columns: user_id, username, password_hash, role
farmers

Stores farmer's personal details.
Columns: farmer_id, name, state, crop_type, contact_details
agriculture_updates

Stores the updates linked from the Indian agriculture government website.
Columns: update_id, title, content, date, related_crop
kpis

Stores KPIs (Key Performance Indicators) for agricultural performance.
Columns: kpi_id, name, value, date
SQL Queries
Below are some useful SQL queries to interact with the database.

Example Queries
Select all farmers:

sql
Copy
Edit
SELECT * FROM farmers;
Get the latest agriculture updates:

sql
Copy
Edit
SELECT * FROM agriculture_updates ORDER BY date DESC LIMIT 5;
Insert a new farmer:

sql
Copy
Edit
INSERT INTO farmers (name, state, crop_type) 
VALUES ('John Doe', 'Uttar Pradesh', 'Wheat');
Update KPI values:

sql
Copy
Edit
UPDATE kpis 
SET value = 85 
WHERE kpi_id = 1;
Get KPIs for a specific crop:

sql
Copy
Edit
SELECT * FROM kpis WHERE related_crop = 'Wheat';
How to Use
Connecting to the Database
Once the database is set up and the tables are created, you can connect your backend application (Spring Boot) to the database using the following configuration in application.properties:

properties
Copy
Edit
spring.datasource.url=jdbc:mysql://localhost:3306/krishi_interface
spring.datasource.username=<your-username>
spring.datasource.password=<your-password>
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
This allows the application to interact with the database and fetch real-time updates.

API Usage
Once the database is connected, you can use the REST API endpoints to access and update agricultural data. For example:

GET /api/farmers: Fetch all farmers
GET /api/agriculture-updates: Fetch the latest updates
POST /api/farmers: Add a new farmer
Contributing
If you'd like to contribute to the development of this project, please follow these steps:

Fork the repository
Create a new branch for your changes
Make your modifications and commit them
Push your changes to your fork
Open a pull request for review
We welcome all contributions, whether they're bug fixes, new features, or documentation improvements!

License
This project is open-source and available under the MIT License. See the LICENSE file for more details.

Acknowledgements
Indian Government's Agriculture Website for providing data
Spring Boot, Angular, MySQL for the tech stack

