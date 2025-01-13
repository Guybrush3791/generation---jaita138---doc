# Repo

`gen-jaita138-db-query-1`

# Modalita' di Consegna

Foglio di testo riportante accoppiata domanda-query

# Database

## Descrizione

Certamente! Ecco una proposta per il tuo database con una tabella centrale, una relazione 1 a N e una relazione M a N:

### **Struttura delle Tabelle**

1. **Utenti**

   - `id_utente` (INT, PRIMARY KEY, AUTO_INCREMENT)
   - `nome` (VARCHAR(50))
   - `cognome` (VARCHAR(50))
   - `email` (VARCHAR(100))
   - `data_iscrizione` (DATE)

2. **Articoli**

   - `id_articolo` (INT, PRIMARY KEY, AUTO_INCREMENT)
   - `id_utente` (INT, FOREIGN KEY REFERENCES `Utenti`(`id_utente`))
   - `titolo` (VARCHAR(150))
   - `contenuto` (TEXT)
   - `data_pubblicazione` (DATETIME)
   - `prezzo` (DECIMAL)

3. **Categorie**

   - `id_categoria` (INT, PRIMARY KEY, AUTO_INCREMENT)
   - `nome_categoria` (VARCHAR(100))
   - `descrizione` (TEXT)

4. **Articoli_Categorie**

   - `id_articolo` (INT, FOREIGN KEY REFERENCES `Articoli`(`id_articolo`))
   - `id_categoria` (INT, FOREIGN KEY REFERENCES `Categorie`(`id_categoria`))
   - **PRIMARY KEY:** (`id_articolo`, `id_categoria`)

### **Schema delle Relazioni**

- **Utenti** (1) ↔ (N) **Articoli**
- **Articoli** (M) ↔ (M) **Categorie** tramite **Articoli_Categorie**

## Dump SQL

Script di creazione e inserimento dati

```sql
-- Creazione delle tabelle

CREATE TABLE Utenti (
    id_utente INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    cognome VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL,
    data_iscrizione DATE NOT NULL
);

CREATE TABLE Articoli (
    id_articolo INT PRIMARY KEY AUTO_INCREMENT,
    id_utente INT NOT NULL,
    titolo VARCHAR(150) NOT NULL,
    contenuto TEXT NOT NULL,
    data_pubblicazione DATETIME NOT NULL,
    prezzo DECIMAL(10,2) NOT NULL, -- Nuovo campo per il prezzo
    FOREIGN KEY (id_utente) REFERENCES Utenti(id_utente)
);

CREATE TABLE Categorie (
    id_categoria INT PRIMARY KEY AUTO_INCREMENT,
    nome_categoria VARCHAR(100) NOT NULL,
    descrizione TEXT
);

CREATE TABLE Articoli_Categorie (
    id_articolo INT NOT NULL,
    id_categoria INT NOT NULL,
    PRIMARY KEY (id_articolo, id_categoria),
    FOREIGN KEY (id_articolo) REFERENCES Articoli(id_articolo),
    FOREIGN KEY (id_categoria) REFERENCES Categorie(id_categoria)
);

-- Inserimenti nella tabella Utenti

INSERT INTO Utenti (nome, cognome, email, data_iscrizione) VALUES
('Luca', 'Rossi', 'luca.rossi@example.com', '2023-01-15'),
('Maria', 'Bianchi', 'maria.bianchi@example.com', '2023-02-20'),
('Giovanni', 'Verdi', 'giovanni.verdi@example.com', '2023-03-10'),
('Anna', 'Neri', 'anna.neri@example.com', '2023-04-05'),
('Marco', 'Gialli', 'marco.gialli@example.com', '2023-05-18'),
('Sara', 'Blu', 'sara.blu@example.com', '2023-06-22'),
('Paolo', 'Arancioni', 'paolo.arancioni@example.com', '2023-07-30'),
('Elena', 'Viola', 'elena.viola@example.com', '2023-08-14'),
('Stefano', 'Grigi', 'stefano.grigi@example.com', '2023-09-09'),
('Francesca', 'Rosa', 'francesca.rosa@example.com', '2023-10-25'),
('Alessandro', 'Bianco', 'alessandro.bianco@example.com', '2023-11-11'),
('Laura', 'Marroni', 'laura.marroni@example.com', '2023-12-01'),
('Davide', 'Azzurri', 'davide.azzurri@example.com', '2024-01-19'),
('Chiara', 'Ceneri', 'chiara.ceneri@example.com', '2024-02-07'),
('Simone', 'Turchini', 'simone.turchini@example.com', '2024-03-16'),
('Valentina', 'Porcelli', 'valentina.porcelli@example.com', '2024-04-23'),
('Riccardo', 'Ruggine', 'riccardo.ruggine@example.com', '2024-05-05'),
('Giorgia', 'Zaffiri', 'giorgia.zaffiri@example.com', '2024-06-12'),
('Matteo', 'Oro', 'matteo.oro@example.com', '2024-07-29'),
('Federica', 'Argenti', 'federica.argenti@example.com', '2024-08-08');

-- Inserimenti nella tabella Categorie

INSERT INTO Categorie (nome_categoria, descrizione) VALUES
('Tecnologia', 'Articoli relativi alle ultime novità tecnologiche.'),
('Salute', 'Consigli e informazioni sulla salute e il benessere.'),
('Viaggi', 'Guide e racconti di viaggio in diverse destinazioni.'),
('Cucina', 'Ricette e consigli culinari.'),
('Sport', 'Notizie e approfondimenti sul mondo dello sport.'),
('Arte', 'Discussioni e recensioni di opere d\'arte.'),
('Educazione', 'Articoli sull\'istruzione e l\'apprendimento.'),
('Finanza', 'Consigli finanziari e notizie economiche.'),
('Moda', 'Tendenze e consigli di stile.'),
('Ambiente', 'Informazioni e notizie sull\'ambiente e la sostenibilità.'),
('Intrattenimento', 'Recensioni di film, musica e libri.'),
('Politica', 'Analisi e notizie politiche.'),
('Scienza', 'Scoperte scientifiche e ricerche.'),
('Automotive', 'Novità e recensioni nel mondo dell\'automobile.'),
('Lifestyle', 'Consigli per uno stile di vita equilibrato.'),
('Casa', 'Idee e consigli per l\'arredamento domestico.'),
('Gastronomia', 'Focus su cibi e bevande di qualità.'),
('Letteratura', 'Recensioni e discussioni di opere letterarie.'),
('Gaming', 'Notizie e recensioni sul mondo dei videogiochi.'),
('Musica', 'Articoli e recensioni musicali.');

-- Inserimenti nella tabella Articoli

INSERT INTO Articoli (id_utente, titolo, contenuto, data_pubblicazione, prezzo) VALUES
(1, 'Le ultime novità in ambito tecnologico', 'Contenuto dell\'articolo sulla tecnologia...', '2024-01-10 10:30:00', 49.99),
(2, '10 consigli per una vita sana', 'Contenuto dell\'articolo sulla salute...', '2024-01-15 14:20:00', 29.50),
(3, 'Guida ai migliori luoghi da visitare nel 2024', 'Contenuto dell\'articolo sui viaggi...', '2024-02-05 09:00:00', 39.00),
(4, 'Ricetta per una pasta perfetta', 'Contenuto dell\'articolo sulla cucina...', '2024-02-20 12:45:00', 15.75),
(5, 'Le partite più emozionanti della stagione', 'Contenuto dell\'articolo sullo sport...', '2024-03-01 18:30:00', 25.00),
(6, 'L\'influenza dell\'arte moderna', 'Contenuto dell\'articolo sull\'arte...', '2024-03-15 11:10:00', 35.20),
(7, 'Strategie di apprendimento efficace', 'Contenuto dell\'articolo sull\'educazione...', '2024-04-01 08:25:00', 20.00),
(8, 'Come gestire le tue finanze personali', 'Contenuto dell\'articolo sulla finanza...', '2024-04-20 16:50:00', 45.30),
(9, 'Tendenze moda primavera/estate 2024', 'Contenuto dell\'articolo sulla moda...', '2024-05-05 13:35:00', 30.00),
(10, 'Importanza della sostenibilità ambientale', 'Contenuto dell\'articolo sull\'ambiente...', '2024-05-22 07:40:00', 22.50),
(11, 'Recensione del nuovo film di fantascienza', 'Contenuto dell\'articolo sull\'intrattenimento...', '2024-06-10 20:15:00', 18.99),
(12, 'Analisi delle elezioni europee', 'Contenuto dell\'articolo sulla politica...', '2024-06-25 17:05:00', 27.80),
(13, 'Scoperte recenti nel campo della fisica', 'Contenuto dell\'articolo sulla scienza...', '2024-07-08 10:00:00', 33.50),
(14, 'Le migliori auto elettriche del 2024', 'Contenuto dell\'articolo sull\'automotive...', '2024-07-20 15:30:00', 55.00),
(15, 'Consigli per un lifestyle equilibrato', 'Contenuto dell\'articolo sul lifestyle...', '2024-08-01 09:45:00', 19.99),
(16, 'Come arredare il tuo salotto', 'Contenuto dell\'articolo sulla casa...', '2024-08-15 14:10:00', 40.00),
(17, 'I migliori vini italiani del 2024', 'Contenuto dell\'articolo sulla gastronomia...', '2024-09-05 18:20:00', 60.00),
(18, 'Recensione del nuovo romanzo di fantascienza', 'Contenuto dell\'articolo sulla letteratura...', '2024-09-20 12:00:00', 24.50),
(19, 'Le novità nel mondo dei videogiochi', 'Contenuto dell\'articolo sul gaming...', '2024-10-01 16:40:00', 34.99),
(20, 'Intelligenza artificiale: opportunità e sfide', 'Contenuto dell\'articolo sulla tecnologia...', '2024-10-15 11:30:00', 48.75),
(1, 'Alimentazione e benessere mentale', 'Contenuto dell\'articolo sulla salute...', '2024-11-05 10:15:00', 28.60),
(2, 'Viaggiare in sicurezza durante le feste', 'Contenuto dell\'articolo sui viaggi...', '2024-11-20 09:50:00', 32.00),
(3, 'Dolci tradizionali italiani da provare', 'Contenuto dell\'articolo sulla cucina...', '2024-12-01 14:25:00', 16.80),
(4, 'L\'importanza dell\'esercizio fisico', 'Contenuto dell\'articolo sullo sport...', '2024-12-15 08:40:00', 23.00),
(5, 'Esposizioni d\'arte da non perdere nel 2024', 'Contenuto dell\'articolo sull\'arte...', '2024-12-20 19:30:00', 37.50),
(6, 'Tecnologie emergenti nel 2025', 'Contenuto dell\'articolo sulla tecnologia...', '2024-12-25 10:00:00', 50.00),
(7, 'Benefici dello yoga quotidiano', 'Contenuto dell\'articolo sulla salute...', '2025-01-05 07:30:00', 18.25),
(8, 'Le destinazioni più economiche per viaggiare', 'Contenuto dell\'articolo sui viaggi...', '2025-01-20 13:15:00', 29.99),
(9, 'Ricette vegane per principianti', 'Contenuto dell\'articolo sulla cucina...', '2025-02-10 11:45:00', 20.50),
(10, 'Le Olimpiadi: storie di successo', 'Contenuto dell\'articolo sullo sport...', '2025-02-25 17:20:00', 27.75),
(11, 'Arte contemporanea e società', 'Contenuto dell\'articolo sull\'arte...', '2025-03-05 09:10:00', 34.40),
(12, 'Tecnologia blockchain spiegata semplice', 'Contenuto dell\'articolo sulla tecnologia...', '2025-03-20 15:55:00', 42.00),
(13, 'Come risparmiare per la pensione', 'Contenuto dell\'articolo sulla finanza...', '2025-04-10 12:30:00', 35.60),
(14, 'Moda sostenibile: il futuro dell\'abbigliamento', 'Contenuto dell\'articolo sulla moda...', '2025-04-25 16:45:00', 28.90),
(15, 'Strategie per ridurre l\'impatto ambientale', 'Contenuto dell\'articolo sull\'ambiente...', '2025-05-10 08:50:00', 31.25),
(16, 'Recensioni dei nuovi album musicali', 'Contenuto dell\'articolo sull\'intrattenimento...', '2025-05-25 20:30:00', 19.75),
(17, 'Nuove scoperte nella genetica', 'Contenuto dell\'articolo sulla scienza...', '2025-06-05 10:40:00', 45.00),
(18, 'Le auto ibride più efficienti', 'Contenuto dell\'articolo sull\'automotive...', '2025-06-20 14:10:00', 52.50),
(19, 'Stili di vita minimalisti', 'Contenuto dell\'articolo sul lifestyle...', '2025-07-01 09:30:00', 22.80),
(20, 'Idee creative per la decorazione della casa', 'Contenuto dell\'articolo sulla casa...', '2025-07-15 13:25:00', 38.60),
(1, 'Vini biodinamici: cosa sono e perché sceglierli', 'Contenuto dell\'articolo sulla gastronomia...', '2025-08-05 18:10:00', 55.00),
(2, 'Analisi del nuovo bestseller letterario', 'Contenuto dell\'articolo sulla letteratura...', '2025-08-20 12:50:00', 26.40),
(3, 'Le migliori periferie per giocare', 'Contenuto dell\'articolo sul gaming...', '2025-09-01 16:35:00', 30.00),
(4, 'Le sinfonie più influenti del secolo', 'Contenuto dell\'articolo sulla musica...', '2025-09-15 11:20:00', 24.95),
(5, 'Innovazioni nella realtà virtuale', 'Contenuto dell\'articolo sulla tecnologia...', '2025-10-01 10:00:00', 47.30),
(6, 'Benefici della meditazione per la mente', 'Contenuto dell\'articolo sulla salute...', '2025-10-15 09:15:00', 21.50),
(7, 'Viaggi sostenibili: come ridurre l\'impatto', 'Contenuto dell\'articolo sui viaggi...', '2025-11-05 14:40:00', 33.20),
(8, 'Pane fatto in casa: tecniche e segreti', 'Contenuto dell\'articolo sulla cucina...', '2025-11-20 12:30:00', 19.80),
(9, 'Prepararsi alle gare: consigli utili', 'Contenuto dell\'articolo sullo sport...', '2025-12-01 08:50:00', 25.60),
(10, 'Esposizioni virtuali di arte contemporanea', 'Contenuto dell\'articolo sull\'arte...', '2025-12-15 19:00:00', 36.75);

-- Inserimenti nella tabella Articoli_Categorie

INSERT INTO Articoli_Categorie (id_articolo, id_categoria) VALUES
(1, 1),
(1, 13),
(2, 2),
(3, 3),
(4, 4),
(5, 5),
(6, 6),
(7, 7),
(8, 8),
(9, 9),
(10, 10),
(11, 11),
(12, 12),
(13, 13),
(14, 14),
(15, 15),
(16, 16),
(17, 17),
(18, 18),
(19, 19),
(20, 1),
(20, 13),
(21, 2),
(22, 3),
(23, 4),
(24, 5),
(25, 6),
(26, 1),
(27, 2),
(28, 3),
(29, 4),
(30, 5),
(31, 6),
(32, 1),
(33, 8),
(34, 9),
(35, 10),
(36, 11),
(37, 13),
(38, 14),
(39, 15),
(40, 16),
(41, 17),
(42, 18),
(43, 19),
(44, 20),
(45, 1),
(46, 2),
(47, 3),
(48, 4),
(49, 5),
(50, 6);

```

# Query

### Livello 1: Interrogazioni di Base

1. Recupera tutti gli utenti registrati nel sistema.

```sql
SELECT *
FROM Utenti
```

2. Recupera il nome, cognome e email di tutti gli utenti iscritti dopo il 1° marzo 2024.

```sql
SELECT nome, cognome, email
FROM Utenti
WHERE data_iscrizione >= '2024-03-01'
```

3. Recupera tutti gli articoli insieme al nome e cognome dell'autore.

```sql
SELECT a.*, u.nome, u.cognome 
FROM Articoli a 
	JOIN Utenti u 
		ON a.id_utente = u.id_utente 
```

4. Recupera i titoli degli articoli pubblicati nel mese di maggio 2024.

```sql
-- VERSIONE 1
SELECT *
FROM Articoli a 
WHERE data_pubblicazione BETWEEN '2024-05-01' AND '2024-05-31'

-- VERSIONE 2
SELECT *
FROM Articoli a 
WHERE MONTH(data_pubblicazione) = 5 
	AND YEAR(data_pubblicazione) = 2024

-- VERSIONE 3
SELECT *
FROM Articoli a 
WHERE data_pubblicazione >= '2024-05-01' 
	AND data_pubblicazione < '2024-06-01'
```

5. Recupera le prime 5 categorie ordinate alfabeticamente per nome.

```sql
SELECT *
FROM Categorie c 
ORDER BY nome_categoria
LIMIT 5
```

6. Recupera gli articoli che appartengono alla categoria 'Tecnologia'.

```sql
SELECT a.*
FROM Categorie c 
	JOIN Articoli_Categorie ac 
		ON c.id_categoria = ac.id_categoria 
	JOIN Articoli a 
		ON ac.id_articolo = a.id_articolo 
WHERE nome_categoria LIKE 'Tecnologia'
```

7. Recupera le email degli utenti che hanno scritto almeno un articolo.

```sql
-- VERSIONE 1
SELECT u.email
FROM Utenti u 
	JOIN Articoli a 
		ON u.id_utente = a.id_utente 
GROUP BY u.email 

-- VERSIONE 2
SELECT DISTINCT u.email
FROM Utenti u 
	JOIN Articoli a 
		ON u.id_utente = a.id_utente 
```

8. Recupera tutti gli articoli pubblicati tra il 1° giugno 2024 e il 31 agosto 2024.

```sql
-- VERSIONE 1
SELECT *
FROM Articoli a 
WHERE data_pubblicazione BETWEEN '2024-06-01' AND '2024-08-31'

-- VERSIONE 2
SELECT *
FROM Articoli a 
WHERE data_pubblicazione >= '2024-06-01' 
	AND data_pubblicazione < '2024-08-31'
```

9. Recupera i dettagli delle categorie associate all'articolo con `id_articolo` = 10.

```sql
SELECT c.*
FROM Articoli_Categorie ac 
	JOIN Categorie c 
		ON ac.id_categoria = c.id_categoria 
WHERE ac.id_articolo = 10
```

10. Recupera i nomi degli utenti ordinati per data di iscrizione più recente.

```sql
SELECT *
FROM Utenti u 
ORDER BY data_iscrizione DESC
```

## Livello 2: Interrogazioni Intermedie

1. Conta il numero di articoli scritti da ogni utente.

```sql
SELECT u.id_utente, u.nome, u.cognome, u.email, COUNT(*) AS n_articoli
FROM Utenti u 
	JOIN Articoli a 
		ON u.id_utente = a.id_utente 
GROUP BY u.id_utente 
```

2. Trova la categoria con il maggior numero di articoli associati.

```sql
SELECT c.id_categoria, c.nome_categoria, COUNT(*) AS n_articoli
FROM Categorie c 
	JOIN Articoli_Categorie ac 
		ON c.id_categoria = ac.id_categoria 
GROUP BY c.id_categoria  
ORDER BY n_articoli DESC
LIMIT 1
```

3. Recupera gli utenti che hanno scritto più di 2 articoli.

```sql
SELECT c.id_categoria, c.nome_categoria, COUNT(*) AS n_articoli
FROM Categorie c 
	JOIN Articoli_Categorie ac 
		ON c.id_categoria = ac.id_categoria 
GROUP BY c.id_categoria  
HAVING n_articoli > 2
```

4. Calcola la data di pubblicazione più recente per ogni categoria.

```sql
SELECT c.id_categoria, c.nome_categoria, MAX(a.data_pubblicazione) AS ultima_pub
FROM Categorie c 
	JOIN Articoli_Categorie ac 
		ON c.id_categoria = ac.id_categoria 
	JOIN Articoli a 
		ON ac.id_articolo = a.id_articolo
GROUP BY c.id_categoria 
```

5. ~~Trova il numero medio di articoli per utente.~~
   > [!attention]- DA NON FARE
   > Sottoquery richiesta
   >
   > ```sql
   > SELECT avg(subQ.n_articoli) media_articoli
   > 	FROM (
   > 		SELECT u.id_utente, COUNT(*) n_articoli
   > 		FROM Utenti u
   > 			JOIN Articoli a
   > 				ON	u.id_utente = a.id_utente
   > 		GROUP BY u.id_utente
   > 	) subQ
   > ```
6. Recupera le categorie che hanno almeno 3 articoli associati.

```sql
SELECT c.id_categoria, c.nome_categoria, COUNT(*) AS n_articoli
FROM Categorie c 
	JOIN Articoli_Categorie ac 
		ON c.id_categoria = ac.id_categoria 
GROUP BY c.id_categoria 
HAVING n_articoli >= 3
```

7. Calcola il totale degli articoli pubblicati per ogni mese del 2024.

```sql
SELECT MONTH(data_pubblicazione), COUNT(*) n_articoli
FROM Articoli a 
WHERE YEAR(data_pubblicazione) = 2024
GROUP BY MONTH(data_pubblicazione)
```

8. Trova l'utente che ha la data di iscrizione più antica.

```sql
-- VERSIONE 1
SELECT *
FROM Utenti u 
ORDER BY data_iscrizione 
LIMIT 1

-- VERSIONE 2
SELECT nome, data_iscrizione 
FROM Utenti u 
WHERE data_iscrizione = (
	SELECT MIN(u2.data_iscrizione)
	FROM Utenti u2 
)
```

9. Recupera le categorie ordinate per numero articoli in maniera decrescente

```sql
SELECT c.id_categoria, c.nome_categoria, COUNT(*) AS n_articoli 
FROM Categorie c 
	JOIN Articoli_Categorie ac 
		ON c.id_categoria  = ac.id_categoria 
GROUP BY c.id_categoria 
ORDER BY n_articoli DESC
```

10. Calcola il numero totale di articoli pubblicati da utenti iscritti nel 2024.

```sql
SELECT count(*)
FROM Utenti u 
	JOIN Articoli a 
		ON u.id_utente = a.id_utente 
WHERE YEAR(data_iscrizione) = 2024
```

## Livello 3: Bonus

1. Recupera gli utenti che non hanno scritto nessun articolo.
   > [!note] Eseguire la seguente query per creare un utente senza articoli pubblicati
   >
   > ```sql
   > INSERT INTO Utenti (nome, cognome, email, data_iscrizione)
   > VALUES ("Gigi", "Bianchi", "gigi@gmail.com", '2020-01-01');
   > ```
```sql
SELECT u.*
FROM Utenti u 
	LEFT JOIN Articoli a 
		ON u.id_utente = a.id_utente 
WHERE a.id_articolo IS NULL
```
2. Trova le categorie che non hanno alcun articolo associato.
   > [!note] Eseguire la seguente query per creare una categoria senza articoli associati
   >
   > ```sql
   > INSERT INTO Categorie (nome_categoria, descrizione)
   > VALUES ("my cat", "empty desc")
   > ```

```sql
SELECT c.*
FROM Categorie c 
	LEFT JOIN Articoli_Categorie ac 
		ON c.id_categoria = ac.id_categoria 
WHERE ac.id_articolo IS NULL 
```
3. Trova le categorie che contengono articoli scritti da utenti iscritti prima del 2024.
```sql
SELECT DISTINCT c.*
FROM Utenti u
	JOIN Articoli a 
		ON u.id_utente = a.id_utente 
	JOIN Articoli_Categorie ac 
		ON a.id_articolo = ac.id_articolo 
	JOIN Categorie c 
		ON ac.id_categoria = c.id_categoria 
WHERE u.data_iscrizione < '2024-01-01'
```
5. Recupera le categorie che sono associate ad almeno 3 articoli pubblicati nel 2024.
```sql
SELECT c.id_categoria, c.nome_categoria, COUNT(*) n_articoli
FROM Categorie c 
	JOIN Articoli_Categorie ac 
		ON c.id_categoria = ac.id_categoria
	JOIN Articoli a 
		ON ac.id_articolo = a.id_articolo 
WHERE YEAR(a.data_pubblicazione) = 2024
GROUP BY c.id_categoria 
HAVING n_articoli >= 3
```