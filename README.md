# Data Definition Language (DDL) Checkpoint

## Overview
This project involves creating a relational database model based on a provided schema. The objective is to implement the relational model using SQL, including specified constraints and additional modifications.

## Objectives
- Create the relational model using SQL statements.
- Apply the appropriate data types and constraints.
- Add new columns to existing tables as specified.

## Database Structure
The database consists of the following tables:

1. **CUSTOMER**
   - CustomerID (NUMBER(10), Primary Key)
   - Name (VARCHAR2(50), NOT NULL)
   - Address (VARCHAR2(100))
   - Phone (VARCHAR2(15))

2. **PRODUCT**
   - ProductID (NUMBER(10), Primary Key)
   - Name (VARCHAR2(50), NOT NULL)
   - Price (NUMBER(10,2))
   - StockQuantity (NUMBER(10))
   - Category (VARCHAR2(20))

3. **ORDERS**
   - OrderID (NUMBER(10), Primary Key)
   - CustomerID (NUMBER(10), Foreign Key references CUSTOMER(CustomerID))
   - OrderDate (DATE, Default: SYSDATE)

4. **ORDER_DETAILS**
   - OrderDetailID (NUMBER(10), Primary Key)
   - OrderID (NUMBER(10), Foreign Key references ORDERS(OrderID))
   - ProductID (NUMBER(10), Foreign Key references PRODUCT(ProductID))
   - Quantity (NUMBER(10))

## SQL Commands
### Creating Tables
```sql
-- CUSTOMER Table
CREATE TABLE CUSTOMER (
    CustomerID NUMBER(10) PRIMARY KEY,
    Name VARCHAR2(50) NOT NULL,
    Address VARCHAR2(100),
    Phone VARCHAR2(15)
);

-- PRODUCT Table
CREATE TABLE PRODUCT (
    ProductID NUMBER(10) PRIMARY KEY,
    Name VARCHAR2(50) NOT NULL,
    Price NUMBER(10,2),
    StockQuantity NUMBER(10)
);

-- ORDERS Table
CREATE TABLE ORDERS (
    OrderID NUMBER(10) PRIMARY KEY,
    CustomerID NUMBER(10),
    OrderDate DATE DEFAULT SYSDATE,
    FOREIGN KEY (CustomerID) REFERENCES CUSTOMER(CustomerID)
);

-- ORDER_DETAILS Table
CREATE TABLE ORDER_DETAILS (
    OrderDetailID NUMBER(10) PRIMARY KEY,
    OrderID NUMBER(10),
    ProductID NUMBER(10),
    Quantity NUMBER(10),
    FOREIGN KEY (OrderID) REFERENCES ORDERS(OrderID),
    FOREIGN KEY (ProductID) REFERENCES PRODUCT(ProductID)
);
```

### Modifying Tables
```sql
-- Add Category column to PRODUCT table
ALTER TABLE PRODUCT
ADD Category VARCHAR2(20);

-- Add OrderDate column to ORDERS table with default value
ALTER TABLE ORDERS
ADD OrderDate DATE DEFAULT SYSDATE;
```

## Repository
You can find the full project on GitHub:
[Data-definition-language-DDL-Checkpoint](https://github.com/omarmechergui/Data-definition-language-DDL-Checkpoint.git)

## Requirements
- Database Management System (e.g., Oracle Database)
- SQL knowledge for creating and modifying tables

## Installation
1. Clone the repository:

    ```bash
    git clone https://github.com/omarmechergui/Data-definition-language-DDL-Checkpoint.git
    cd Data-definition-language-DDL-Checkpoint
    ```

2. Execute the SQL script to create the schema:

    ```bash
    sqlplus username/password@database < schema.sql
    ```

## Usage
- Perform CRUD operations on CUSTOMER, PRODUCT, ORDERS, and ORDER_DETAILS tables.
- Query and analyze customer orders and product information.

## Contributing
Contributions are welcome! Feel free to submit a pull request with improvements or fixes.

## License
This project is licensed under the MIT License.

## Contact
For questions or support, reach out to (mailto:oo2377107@gmail.com).

