## Schema E-R
![[Pasted image 20241216154447.png]]

## Query Creazione + Inserimento
```sql
-- Drop tables if they exist (to ensure a clean start)
DROP TABLE IF EXISTS EsameStudente;
DROP TABLE IF EXISTS StudenteDettagli;
DROP TABLE IF EXISTS Studente;
DROP TABLE IF EXISTS Esame;
DROP TABLE IF EXISTS CorsoStudi;

-- Create table: CorsoStudi
CREATE TABLE CorsoStudi (
    id INT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    dataInizio DATE,
    dataFine DATE
);

-- Insert 10 rows into CorsoStudi
INSERT INTO CorsoStudi (id, nome, dataInizio, dataFine) VALUES 
(1, 'Laurea in Ingegneria Informatica', '2010-10-01', '2013-07-15'),
(2, 'Laurea in Matematica', '2011-09-15', '2014-06-30'),
(3, 'Laurea in Fisica', '2012-03-01', '2015-09-20'),
(4, 'Laurea in Chimica', '2013-11-10', '2016-10-01'),
(5, 'Laurea in Biologia', '2010-01-20', '2013-12-10'),
(6, 'Laurea in Lettere', '2014-02-01', '2017-07-10'),
(7, 'Laurea in Storia', '2015-04-15', '2018-09-15'),
(8, 'Laurea in Economia', '2011-07-01', '2014-11-25'),
(9, 'Laurea in Giurisprudenza', '2013-01-10', '2016-05-30'),
(10, 'Laurea in Ingegneria Elettronica', '2009-09-05', '2012-06-20');


-- Create table: Studente
CREATE TABLE Studente (
    id INT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    cognome VARCHAR(100) NOT NULL,
    dataNascita DATE,
    corsoStudiId INT,
    FOREIGN KEY (corsoStudiId) REFERENCES CorsoStudi(id)
);

-- Insert 10 rows into Studente
INSERT INTO Studente (id, nome, cognome, dataNascita, corsoStudiId) VALUES
(1, 'Mario', 'Rossi', '1990-05-10', 1),
(2, 'Luigi', 'Bianchi', '1991-06-20', 2),
(3, 'Giulia', 'Ferrari', '1992-07-15', 3),
(4, 'Anna', 'Verdi', '1990-09-25', 1),
(5, 'Marco', 'Esposito', '1993-12-01', 4),
(6, 'Carla', 'Neri', '1989-03-30', 5),
(7, 'Luca', 'Moretti', '1994-11-11', 2),
(8, 'Sara', 'Giordano', '1991-01-22', 10),
(9, 'Francesca', 'Ricci', '1995-04-04', 9),
(10, 'Giorgio', 'Marini', '1990-08-08', 8);


-- Create table: StudenteDettagli
CREATE TABLE StudenteDettagli (
    id INT PRIMARY KEY,
    residenza VARCHAR(100),
    tipoDocumento VARCHAR(50),
    idDocumento VARCHAR(50),
    FOREIGN KEY (id) REFERENCES Studente(id)
);

-- Insert 10 rows into StudenteDettagli
INSERT INTO StudenteDettagli (id, residenza, tipoDocumento, idDocumento) VALUES
(1, 'Milano', 'CartaID', 'AB12345'),
(2, 'Roma', 'Passaporto', 'PZ99876'),
(3, 'Torino', 'CartaID', 'CD34567'),
(4, 'Firenze', 'CartaID', 'EF78901'),
(5, 'Napoli', 'Patente', 'NPL45678'),
(6, 'Genova', 'CartaID', 'GH23456'),
(7, 'Bari', 'Patente', 'BR99881'),
(8, 'Palermo', 'CartaID', 'PM11223'),
(9, 'Bologna', 'Passaporto', 'BL65432'),
(10, 'Cagliari', 'CartaID', 'CG88776');


-- Create table: Esame
CREATE TABLE Esame (
    id INT PRIMARY KEY,
    tipologia VARCHAR(50),
    materia VARCHAR(100),
    inizio DATETIME,
    location VARCHAR(100),
    cfu INT
);

-- Insert 10 rows into Esame
INSERT INTO Esame (id, tipologia, materia, inizio, location, cfu) VALUES
(1, 'Scritto', 'Analisi Matematica', '2024-01-10 09:00:00', 'Aula 1', 6),
(2, 'Orale', 'Programmazione', '2024-02-15 14:00:00', 'Aula 3', 9),
(3, 'Scritto', 'Fisica I', '2024-03-20 08:30:00', 'Aula 2', 6),
(4, 'Orale', 'Chimica Generale', '2024-04-25 10:00:00', 'Aula 5', 6),
(5, 'Scritto', 'Biologia Molecolare', '2024-05-05 11:00:00', 'Aula 1', 6),
(6, 'Scritto', 'Letteratura Italiana', '2024-06-10 15:00:00', 'Aula 7', 3),
(7, 'Orale', 'Storia Contemporanea', '2024-07-12 09:30:00', 'Aula 4', 6),
(8, 'Orale', 'Economia Politica', '2024-08-02 16:00:00', 'Aula Magna', 9),
(9, 'Scritto', 'Diritto Privato', '2024-09-23 08:00:00', 'Aula 2', 6),
(10, 'Scritto', 'Elettronica Digitale', '2024-10-05 13:30:00', 'Aula 6', 9);


-- Create table: EsameStudente
CREATE TABLE EsameStudente (
    id INT PRIMARY KEY,
    votoEsame INT,
    esameId INT,
    studenteId INT,
    FOREIGN KEY (esameId) REFERENCES Esame(id),
    FOREIGN KEY (studenteId) REFERENCES Studente(id)
);

-- Insert 10 rows into EsameStudente
-- Assume random association and random grades
INSERT INTO EsameStudente (id, votoEsame, esameId, studenteId) VALUES
(1, 28, 1, 1),
(2, 30, 2, 2),
(3, 25, 3, 3),
(4, 18, 4, 4),
(5, 27, 5, 5),
(6, 30, 6, 6),
(7, 22, 7, 7),
(8, 26, 8, 8),
(9, 19, 9, 9),
(10, 29, 10, 10);

```
## Query Interrogative
### Studente <--> Corso di Studi
- **tipo relazione**: 1aN
- per ogni studente esiste un solo corso di studi
- per ogni corso di studi esistono tanti studenti

#### Domande
1. Seleziona tutti i nomi degli studenti e i nomi dei corsi di studio a cui sono iscritti.

2. Trova i cognomi degli studenti e i nomi dei corsi che hanno iniziato prima del 2015.

3. Ottieni una lista di studenti nati dopo il 1990 e i rispettivi nomi dei corsi di studio.

4. Elenco di studenti e corsi di studio, ordinati per data di nascita dello studente e data di inizio del corso.

5. Conta quanti studenti sono iscritti a ogni corso di studio.
