
# SQL Filtering Commands

### 1. WHERE – Filter rows based on condition  
The WHERE clause is used to filter records that meet specific criteria.

**Syntax:**
```sql
SELECT * FROM table_name
WHERE condition;
```

**Example:**
```sql
SELECT * FROM employees
WHERE department = 'HR';
```
Retrieves only employees who work in the HR department.

---

### 2. LIMIT – Restrict the number of rows returned  
Use LIMIT to control how many rows are returned.

**Example:**
```sql
SELECT * FROM employees
LIMIT 5;
```

Shows only the first 5 employees.

---

### 3. AND – Combine multiple conditions  
The AND operator requires all conditions to be true.

**Syntax:**
```sql
SELECT * FROM employees
WHERE department = 'Sales' AND salary > 50000;
```

Shows employees who are in Sales and earn more than 50,000.

---

### 4. OR – One of the conditions must be true  
The OR operator returns rows where at least one condition is true.

**Example:**
```sql
SELECT * FROM employees
WHERE department = 'HR' OR department = 'Finance';
```

Returns employees from either HR or Finance.

---

### 5. IN – Match against a list of values  
IN is used to filter rows where a column matches any value in a list.  
The IN operator allows you to specify multiple values in a WHERE clause.  
The IN operator is a shorthand for multiple OR conditions.

**Syntax:**
```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```

**Example:**
```sql
SELECT * FROM employees
WHERE department IN ('Sales', 'HR', 'IT');
```

Returns employees in Sales, HR, or IT departments.

---

#### NOT IN  
By using the NOT keyword in front of the IN operator, you return all records that are NOT any of the values in the list.

**Example**  
Return all customers that are NOT from 'Germany', 'France', or 'UK':

```sql
SELECT * FROM Customers
WHERE Country NOT IN ('Germany', 'France', 'UK');
```

---

### 6. BETWEEN – Filter within a range  
BETWEEN is used for filtering values between a specific range.  
It is inclusive, meaning it includes both the lower and upper boundary values.  
Works with numerical, date, and time values.

**Syntax:**
```sql
SELECT *
FROM table_name
WHERE column_name BETWEEN lower_value AND upper_value;
```

**Example:**
```sql
SELECT * FROM employees
WHERE salary BETWEEN 30000 AND 60000;
```

Finds employees earning between 30,000 and 60,000 (inclusive).

**Using date example:**
```sql
SELECT * FROM orders
WHERE order_date BETWEEN '2023-01-01' AND '2023-12-31';
```

Gets orders made in the year 2023.

---
### 7. FETCH – Similar to LIMIT (PostgreSQL-style)  
In PostgreSQL, FETCH is the SQL standard alternative to LIMIT.

**Example:**
```sql
SELECT * FROM employees
FETCH FIRST 5 ROWS ONLY;
```

Equivalent to LIMIT 5.

---

### 8. OFFSET – Skip rows  
OFFSET lets you skip a specific number of rows before displaying results.

**Example:**
```sql
SELECT * FROM employees
OFFSET 5;
```

Skips the first 5 rows.

**NOTE that:** You can combine OFFSET with LIMIT:

**Example:**
```sql
SELECT * FROM employees
OFFSET 5
LIMIT 5;
```

Skips 5 rows, then returns the next 5.

---



### Tip: Combine filters  
You can mix them:

```sql
SELECT * FROM employees
WHERE department = 'IT'
  AND salary BETWEEN 40000 AND 70000
  AND hire_date BETWEEN '2020-01-01' AND '2022-12-31';
```
