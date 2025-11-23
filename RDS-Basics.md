# RDS-Basics.md

# Amazon RDS (Relational Database Service)

## What is RDS?
- Managed service for relational databases on AWS.
- No need to handle physical server, OS, software install — AWS manages it.
- Supports engines: MySQL, PostgreSQL, Oracle, MariaDB, SQL Server, Amazon Aurora.

---

## Databases & DBMS

- **Database:** Structured data, stored electronically.
- **DBMS:** Software for managing databases (MySQL, PostgreSQL, MongoDB, Oracle, SQL Server).

---

## DBMS vs RDBMS

| Feature           | DBMS (e.g. MS Access)      | RDBMS (e.g. MySQL, Postgres) |
|-------------------|----------------------------|------------------------------|
| Structure         | Stores as files            | Tables (rows/columns)        |
| Relationship      | No relationships           | Supports relationships (FKs) |
| Data Integrity    | Low                        | High                         |
| Multi-user        | Limited                    | Yes                          |

---

## RDS Core Features

- Automated backups & recovery  
- Scalability (increase/decrease storage, RAM, CPU anytime)  
- High availability (multi-AZ replication)  
- Automatic software patching  
- Security (IAM, encryption, VPC)  
- Monitoring (CloudWatch integrated)  
- Cost-efficient (pay as you use)

---

## Supported Engines

| Engine     | Description                                             |
|------------|---------------------------------------------------------|
| MySQL      | Popular, open-source                                    |
| PostgreSQL | Advanced features, complex queries                      |
| MariaDB    | MySQL-compatible, community driven                      |
| Oracle     | Enterprise proprietary, commercial                      |
| SQL Server | Microsoft’s RDBMS                                       |
| Aurora     | AWS’s high-performance (MySQL/Postgres compatible)      |

---

## Step-by-Step Example (Create MySQL Database on RDS)

1. **Create RDS Instance**
    - AWS Console → RDS → Create DB
    - Standard Create → MySQL
    - Free tier, set instance identifier, master username/password
    - Storage: General Purpose SSD, make DB publicly accessible (for learning), choose VPC
    - Click Create

2. **Connect to RDS**
    - Once available, note endpoint, port, username, password

3. **Connect from EC2/Local**
    ```
    sudo apt update
    sudo apt install mysql-client -y
    mysql -h your-rds-endpoint.amazonaws.com -P 3306 -u admin -p
    ```
    (Enter password. You’re now inside MySQL shell.)

4. **Basic SQL**
    ```
    SHOW DATABASES;
    CREATE DATABASE company;
    USE company;
    CREATE TABLE employee (id INT, name VARCHAR(30));
    INSERT INTO employee VALUES (1, 'Tejas');
    SELECT * FROM employee;
    ```

---

## Default Ports

| Engine     | Port |
|------------|------|
| MySQL      | 3306 |
| PostgreSQL | 5432 |
| Oracle     | 1521 |
| SQL Server | 1433 |
| MariaDB    | 3306 |

---

## RDS Advantages

- Easy setup/management
- Automated backups
- High availability (multi-AZ)
- Read replicas
- Auto failover
- Scale up/down easily
- CloudWatch monitoring
- IAM integration
- Secure VPC networks
- Pay for use, maintenance free

---

## Summary Table

| Feature          | Description                                 |
|------------------|---------------------------------------------|
| Service Type     | Managed RDBMS                               |
| Provider         | AWS                                         |
| Popular Engines  | MySQL, PostgreSQL, Aurora, SQL Server, etc. |
| Default Port     | MySQL - 3306                                |
| Main Benefit     | No manual setup or backup                    |

