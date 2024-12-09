# DB Intro
## Generare tabella
```sql
CREATE TABLE Customer (
    id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    date_of_birth DATE,
    annual_income INT NOT NULL,
    loyalty_points INT DEFAULT 0
);
```

## Inserimento dati
```sql
INSERT INTO Customer (first_name, date_of_birth, annual_income, loyalty_points) VALUES
('Luca', '1990-05-15', 35000, 120),
('Maria', '1985-11-20', 45000, 200),
('Paolo', '1995-07-08', 30000, 80),
('Giulia', '1988-03-18', 40000, 150),
('Simone', '1992-09-25', 28000, 90),
('Elena', '1990-01-12', 38000, 180),
('Marco', '1982-10-05', 50000, 250),
('Ilaria', '1993-08-19', 32000, 110),
('Davide', '1980-12-30', 55000, 300),
('Chiara', '1996-04-22', 27000, 70);
```

## Lettura dei dati
### Select
- selezionare tutti i `Customer` con tutti i suoi attributi
```sql
SELECT *
FROM Customer 
```
- selezionare tutti i `nomi` e i `data di nascita` dei `Customer` presenti in tabella
```sql
SELECT first_name, date_of_birth 
FROM Customer
```
- selezionare tutti i campi dei `Customer` con un `income annuale` superiore ai 40K
```sql
SELECT *
FROM Customer
WHERE annual_income > 40000
```
- selezionare solo il nome dei `Customer` con un `income annuale` inferiore ai 30K
```sql
SELECT *
FROM Customer
WHERE annual_income < 30000
```
#### Bonus
- selezionare solo il nome dei `Customer` con un `income annuale` superiore ai 30K e inferiore ai 40K
```sql
-- VERSIONE 1
SELECT *
FROM Customer
WHERE annual_income < 40000 
	AND annual_income > 30000

-- VERSIONE 2
SELECT *
FROM Customer
WHERE annual_income BETWEEN 30000 AND 40000
```