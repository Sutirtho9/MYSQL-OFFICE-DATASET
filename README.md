# MYSQL-OFFICE-DATASET

```
use office;
CREATE TABLE Employee (
	emp_id INT PRIMARY KEY,
	first_name varchar(20),
	last_name varchar(20),
    birthdate DATE,
    sex CHAR,
    salary INT,
    super_id INT,
    branch_id INT,
    FOREIGN KEY (super_id) REFERENCES Employee(emp_id)
);
```

```
CREATE TABLE Branch(
	branch_id INT PRIMARY KEY,
    branch_name varchar(10),
    mgr_id INT,
    mgr_start_date DATE,
    FOREIGN KEY (mgr_id) REFERENCES Employee(emp_id)
);
```

![image](https://github.com/user-attachments/assets/cb9e02d3-e308-48b7-89ac-0c2532523c0f)

```
ALTER TABLE Employee
ADD CONSTRAINT fk_branch FOREIGN KEY(branch_id) REFERENCES Branch(branch_id)
ON DELETE SET NULL;
```
![image](https://github.com/user-attachments/assets/9e53750b-df01-41bc-a9d4-fb1b7e070419)

```
CREATE TABLE Client(
	client_id INT PRIMARY KEY,
    client_name varchar(20),
    branch_id INT,
    FOREIGN KEY (branch_id) REFERENCES Branch(branch_id)
    ON DELETE SET NULL
);
```
![image](https://github.com/user-attachments/assets/f53d6e6a-a8dd-45d2-9d89-58098e2cbff5)
```
CREATE TABLE Works_with(
	emp_id INT,
    client_id INT,
    total_sales INT,
    PRIMARY KEY(emp_id,client_id),
    FOREIGN KEY (emp_id) REFERENCES Employee(emp_id)
    ON DELETE CASCADE,
    FOREIGN KEY (client_id) REFERENCES Client(client_id)
    ON DELETE CASCADE
);

```
![image](https://github.com/user-attachments/assets/ef568a68-7734-46f0-b0f4-5d3a259e3148)


```
CREATE TABLE Branch_Supplier(
	branch_id INT,
    supplier_name varchar(20),
    supply_type varchar(20),
    PRIMARY KEY(branch_id,supplier_name),
    FOREIGN KEY (branch_id) REFERENCES Branch(branch_id) 
    ON DELETE CASCADE 
);
```
![image](https://github.com/user-attachments/assets/243df1aa-286f-47df-9138-2a4ef7b48dd5)

```
INSERT INTO Employee
VALUES (100,"David","Wallace","1967-11-17",'M',250000,NULL,NULL);

INSERT INTO branch
VALUES(1,"Corporate",100,"2006-02-09");

UPDATE Employee 
SET branch_id=1
WHERE emp_id=100;

INSERT INTO Employee
VALUES(102,"Micheal","Scott","1971-06-25",'M',75000,100,NULL),
	(106,"Josh","Porter","1969-09-05",'M',78000,100,NULL);

UPDATE Employee 
SET branch_id=1
WHERE super_id=100;

INSERT INTO branch
VALUES(2,"Scranton",102,"1992-04-06"),(3,"Stamford",106,"1998-02-13");
```
![image](https://github.com/user-attachments/assets/058d2540-a716-4448-9423-f555450732b5) ![image](https://github.com/user-attachments/assets/53b854ab-dace-4f81-acbb-6b8de1601213)







