
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

# Live Query:
- trovare per ogni annata quanti Customer sono nati in quell'anno
```sql
SELECT YEAR(date_of_birth) AS 'anno di nascita', COUNT(*) 
FROM Customer 
GROUP BY YEAR(date_of_birth)
```

- trovare l'anno di nascita del Customer piu' giovane
```sql
SELECT MAX(YEAR(date_of_birth)) AS 'anno di nascita'
FROM Customer
```

- trovare l'anno di nascita del Customer piu' vecchio
```sql
SELECT MIN(YEAR(date_of_birth)) AS 'anno di nascita'
FROM Customer
```

- trovare l'anno di nascita medio dei Customer 
```sql
SELECT AVG(YEAR(date_of_birth)) AS 'anno di nascita'
FROM Customer
```

- trovare gli anni in cui e' nato piu' di un Customer
```sql
SELECT YEAR(date_of_birth) AS 'anno di nascita', COUNT(*) 
FROM Customer
GROUP BY YEAR(date_of_birth)
HAVING COUNT(*) > 1
```

- ordinare i risultato per annual_income discendente
```sql
SELECT *
FROM Customer 
ORDER BY annual_income DESC 
```

- selezionare il Customer con reddito piu' alto
```sql
SELECT *
FROM Customer
ORDER BY annual_income DESC
LIMIT 1
```

- selezionare i 3 Customer con reddito piu' alto dal terzo in poi
```sql
SELECT *
FROM Customer
ORDER BY annual_income DESC
LIMIT 3 OFFSET 3;
```
# Es: Query
## Level 1
- Seleziona tutti i dettagli dei clienti il cui reddito annuo è superiore a 40.000 euro
```sql
SELECT *
FROM Customer
WHERE annual_income > 40000;
```
- Recupera i nomi e le date di nascita dei clienti che hanno più di 100 punti fedeltà
```sql
SELECT first_name, date_of_birth
FROM Customer 
WHERE loyalty_points > 100
```
- Mostra tutti i campi dei clienti nati dopo il 1° gennaio 1990
```sql
-- -- VERSION 1
SELECT *
FROM Customer
WHERE date_of_birth >= '1990-01-01'

-- -- VERSION 2 (1° gennaio incluso)
SELECT *
FROM Customer
WHERE YEAR(date_of_birth) >= 1990;
```
- Elenca i clienti con un reddito annuo compreso tra 30.000 e 35.000 euro
```sql
-- -- VERSION 1
SELECT *
FROM Customer 
WHERE annual_income >= 30000
	AND annual_income <= 35000;
	
-- -- VERSION 2
SELECT *
FROM Customer 
WHERE annual_income BETWEEN 30000 AND 35000;
```
### Bonus
- Seleziona i nomi dei clienti il cui nome inizia con la lettera 'M'
```sql
SELECT *
FROM Customer
WHERE first_name LIKE 'm%'
```

## Level 2: GROUP BY + aggregazione
- Calcola il numero medio di punti fedelta' (`loyalty_points`) dei clienti raggruppati per anno di nascita
```sql
SELECT YEAR(date_of_birth), AVG(loyalty_points)
FROM Customer
GROUP BY YEAR(date_of_birth)
```
- Trova il reddito annuo massimo e minimo tra tutti i clienti (anche in due query separate)
```sql
-- -- VERSION 1
SELECT MIN(annual_income), MAX(annual_income)
FROM Customer

-- -- VERSION 2
-- -- -- MIN
SELECT annual_income 
FROM Customer 
ORDER BY annual_income 
LIMIT 1

-- -- -- MAX
SELECT annual_income 
FROM Customer 
ORDER BY annual_income DESC 
LIMIT 1
```
### Bonus
- Calcola la somma totale dei punti fedeltà per ogni anno di nascita.
```sql
SELECT YEAR(date_of_birth), SUM(loyalty_points)
FROM Customer 
GROUP BY YEAR(date_of_birth)
```

## Level 3: HAVING + ORDER BY + LIMIT/OFFSET
- Elenca i clienti con un reddito annuo superiore a 35.000 euro, ordinati dal più alto al più basso reddito, mostrando solo i primi 5 risultati
```sql
SELECT *
FROM Customer
WHERE annual_income > 35000
ORDER BY annual_income DESC 
LIMIT 5
```
- Trova gli anni di nascita che hanno più di 2 clienti, ordinati in ordine decrescente di numero di clienti
```sql
SELECT YEAR(date_of_birth), COUNT(*) AS nCustomer
FROM Customer
GROUP BY YEAR(date_of_birth)
HAVING nCustomer > 2
ORDER BY nCustomer DESC
```
- Seleziona i clienti che hanno accumulato più di 100 punti fedeltà, ordina i risultati per punti fedeltà in ordine decrescente e limita la visualizzazione ai primi 3 clienti
```sql
SELECT *
FROM Customer
WHERE loyalty_points > 100
ORDER BY loyalty_points DESC
LIMIT 3
```
### Bonus
- Calcola il reddito annuo medio per ogni anno di nascita e mostra solo quelli con una media superiore a 35.000, ordinati per media in ordine crescente.
```sql
SELECT YEAR(date_of_birth), AVG(annual_income) AS avgAnnualIncome
FROM Customer
GROUP BY YEAR(date_of_birth)
HAVING avgAnnualIncome > 35000
ORDER BY avgAnnualIncome 
```
