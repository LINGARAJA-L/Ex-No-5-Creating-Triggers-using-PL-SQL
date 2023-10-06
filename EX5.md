# Ex. No: 5 Creating Triggers using PL/SQL

### AIM: To create a Trigger using PL/SQL.

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

### Create employee table
![1](https://github.com/LINGARAJA-L/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/129825857/c9673129-32da-456c-b6b8-e96a37885564)


### Create salary_log table
![2](https://github.com/LINGARAJA-L/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/129825857/2ae061d6-9989-4b86-9d28-ef48bbc1ab9c)

### PLSQL Trigger code
```
 set serveroutput on
SQL> CREATE OR REPLACE TRIGGER log_salary_update
     BEFORE UPDATE ON emp
     FOR EACH ROW
     DECLARE
     old_salary NUMBER;
     new_salary NUMBER;
     begin
     old_salary := :OLD.salary;
     new_salary := :NEW.salary;
     IF v_old_salary <> v_new_salary THEN
     INSERT INTO sal_log(empid, empname, old_salary, new_salary, update_date)
     VALUES(:OLD.empid, :OLD.empname, old_salary, new_salary, SYSDATE);
     END IF;
     END;
     /

```
### Output:

![3](https://github.com/LINGARAJA-L/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/129825857/ec64c144-4cda-458a-bbd6-e675ddfc382f)

