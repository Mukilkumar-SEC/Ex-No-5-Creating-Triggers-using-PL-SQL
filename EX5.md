# Ex. No: 5 Creating Triggers using PL/SQL

### AIM:
To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:
```
CREATE TABLE exp5(
  regno NUMBER,
  USERNAME VARCHAR2(10),
  DEPT VARCHAR2(10),
  MARKS NUMBER
);

CREATE TABLE MARKS_log (
  log_id NUMBER GENERATED ALWAYS AS IDENTITY,
  regno NUMBER,
  USERNAME VARCHAR2(10),
  old_MARKS NUMBER,
  new_MARKS NUMBER,
  update_date DATE
);
-- Insert the values in the employee table
insert into exp5 values(1,'MUKESH','AIDS',55);
insert into exp5 values(2,'SAKTHI','AIDS',71)
insert into exp5 values(3,'SHREE','CSE',101)
```
### PLSQL Trigger code
```
-- Create the trigger
CREATE OR REPLACE TRIGGER log_MARKS_update
BEFORE UPDATE ON employe
FOR EACH ROW
BEGIN
  IF :OLD.sMARKS != :NEW.MARKS THEN
    INSERT INTO exp5_log (regno, USERNAME, old_MARKS, new_MARKS, update_date)
    VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
  END IF;
END;
/
-- Insert the values in the employee table
insert into exp5 values(1,'MUKESH','AIDS',55);
insert into exp5 values(2,'SAKTHI','AIDS',71)
insert into exp5 values(3,'SHREE','CSE',101)

-- Update the marks of an student
UPDATE exp5
SET MARKS =99
WHERE regno = 3;
-- Display the marks table
SELECT * FROM exp5;

-- Display the exp5_log table
SELECT * FROM exp5_log;
```

### Output:
![Screenshot (61)](https://github.com/Mukilkumar-SEC/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119559663/dbcfc625-48d0-402e-807c-6a9829248725)

### Result:
Thus the program implemented successfully.
