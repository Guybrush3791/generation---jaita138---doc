# Repo
`gen-jaita138-springboot-hibernate-1`

# Todo
## Day 1
### Fase 1
Sulla falsa riga dell'[ultimo esercizio visto a lezione](https://github.com/Guybrush3791/gen-jaita138-springboot-5) generare la tripletta `Entity`, `Repo` e `Service` per la seguente entità:
#### Utente
- nome : String : VARCHAR(64)
- cognome : String : VARCHAR(64)
- username : String : VARCHAR(128)
- password : String : VARCHAR(64)
- credito : Int : Int (il valore deve essere espresso in centesimi di euro)

##### Entità
L'entità dovra' fornite tutti i campi privati, proprietà `getter`/`setter` e implementazione sensata del metodo `toString`

##### Repo
Definire `query` custom **solo se necessario**

##### Service
Definire almeno i 4 metodi principali:
- `findAll`: trova tutti gli utenti presenti in tabella
- `save`: crea/aggiorna utenti
- `delete`: elimina utenti
- `findById`: recupera utente a partire dall'`id`

### Fase 2
Dopo aver creato e verificato la presenza di dati in tabella eseguire i seguenti inserimenti attraverso `DBEaver`:
```sql
INSERT INTO Utente (nome, cognome, username, password, credito) VALUES
('Marco', 'Rossi', 'marco.rossi', 'password1', 4500),
('Marco', 'Russo', 'marco.russo', 'password2', -1200),
('Luca', 'Ferrari', 'luca.ferrari', 'password3', 7800),
('Luca', 'Esposito', 'luca.esposito', 'password4', -500),
('Alessandro', 'Bianchi', 'alessandro.bianchi', 'password5', 9200),
('Alessandro', 'Romano', 'alessandro.romano', 'password6', -3000),
('Matteo', 'Colombo', 'matteo.colombo', 'password7', 1500),
('Matteo', 'Ricci', 'matteo.ricci', 'password8', -7500),
('Giuseppe', 'Marino', 'giuseppe.marino', 'password9', 6300),
('Giuseppe', 'Greco', 'giuseppe.greco', 'password10', 420),
('Giovanni', 'Bruno', 'giovanni.bruno', 'password11', -200),
('Giovanni', 'Gallo', 'giovanni.gallo', 'password12', 8900),
('Andrea', 'Conti', 'andrea.conti', 'password13', -9100),
('Andrea', 'DeLuca', 'andrea.deluca', 'password14', 3400),
('Stefano', 'Mancini', 'stefano.mancini', 'password15', 5600),
('Stefano', 'Costa', 'stefano.costa', 'password16', -4300),
('Francesco', 'Giordano', 'francesco.giordano', 'password17', 2200),
('Francesco', 'Rizzo', 'francesco.rizzo', 'password18', -6700),
('Gabriele', 'Lombardi', 'gabriele.lombardi', 'password19', 1100),
('Gabriele', 'Moretti', 'gabriele.moretti', 'password20', 9900),
('Antonio', 'Barbieri', 'antonio.barbieri', 'password21', -8400),
('Antonio', 'Fontana', 'antonio.fontana', 'password22', 500),
('Simone', 'Santoro', 'simone.santoro', 'password23', 3200),
('Simone', 'Mariani', 'simone.mariani', 'password24', -150),
('Davide', 'Caruso', 'davide.caruso', 'password25', 7600),
('Davide', 'Ferrara', 'davide.ferrara', 'password26', -9200),
('Lorenzo', 'Gatti', 'lorenzo.gatti', 'password27', 4300),
('Lorenzo', 'Pellegrini', 'lorenzo.pellegrini', 'password28', -2600),
('Paolo', 'Villa', 'paolo.villa', 'password29', 5800),
('Paolo', 'Marchetti', 'paolo.marchetti', 'password30', 100),
('Riccardo', 'D''Angelo', 'riccardo.dangelo', 'password31', -3300),
('Riccardo', 'Bernardi', 'riccardo.bernardi', 'password32', 6700),
('Roberto', 'Martini', 'roberto.martini', 'password33', -9900),
('Roberto', 'Serafini', 'roberto.serafini', 'password34', 2500),
('Edoardo', 'Rinaldi', 'edoardo.rinaldi', 'password35', 800),
('Edoardo', 'Leone', 'edoardo.leone', 'password36', -4100),
('Filippo', 'Vitale', 'filippo.vitale', 'password37', 6900),
('Filippo', 'Coppola', 'filippo.coppola', 'password38', -1200),
('Salvatore', 'De Santis', 'salvatore.desantis', 'password39', 3500),
('Salvatore', 'Palumbo', 'salvatore.palumbo', 'password40', -700),
('Carlo', 'Sanna', 'carlo.sanna', 'password41', 4400),
('Carlo', 'Farina', 'carlo.farina', 'password42', -8800),
('Enzo', 'Riva', 'enzo.riva', 'password43', 2300),
('Enzo', 'Donati', 'enzo.donati', 'password44', 100),
('Fabio', 'Piras', 'fabio.piras', 'password45', -5500),
('Fabio', 'Sala', 'fabio.sala', 'password46', 6600),
('Dario', 'Parisi', 'dario.parisi', 'password47', 200),
('Dario', 'Conte', 'dario.conte', 'password48', -3000),
('Claudio', 'Messina', 'claudio.messina', 'password49', 7700),
('Claudio', 'Rossetti', 'claudio.rossetti', 'password50', -100),
('Elena', 'Rossi', 'elena.rossi', 'password51', 4500),
('Elena', 'Russo', 'elena.russo', 'password52', -1200),
('Maria', 'Ferrari', 'maria.ferrari', 'password53', 7800),
('Maria', 'Esposito', 'maria.esposito', 'password54', -500),
('Sofia', 'Bianchi', 'sofia.bianchi', 'password55', 9200),
('Sofia', 'Romano', 'sofia.romano', 'password56', -3000),
('Giulia', 'Colombo', 'giulia.colombo', 'password57', 1500),
('Giulia', 'Ricci', 'giulia.ricci', 'password58', -7500),
('Anna', 'Marino', 'anna.marino', 'password59', 6300),
('Anna', 'Greco', 'anna.greco', 'password60', 420),
('Chiara', 'Bruno', 'chiara.bruno', 'password61', -200),
('Chiara', 'Gallo', 'chiara.gallo', 'password62', 8900),
('Francesca', 'Conti', 'francesca.conti', 'password63', -9100),
('Francesca', 'DeLuca', 'francesca.deluca', 'password64', 3400),
('Laura', 'Mancini', 'laura.mancini', 'password65', 5600),
('Laura', 'Costa', 'laura.costa', 'password66', -4300),
('Valentina', 'Giordano', 'valentina.giordano', 'password67', 2200),
('Valentina', 'Rizzo', 'valentina.rizzo', 'password68', -6700),
('Roberta', 'Lombardi', 'roberta.lombardi', 'password69', 1100),
('Roberta', 'Moretti', 'roberta.moretti', 'password70', 9900),
('Angela', 'Barbieri', 'angela.barbieri', 'password71', -8400),
('Angela', 'Fontana', 'angela.fontana', 'password72', 500),
('Barbara', 'Santoro', 'barbara.santoro', 'password73', 3200),
('Barbara', 'Mariani', 'barbara.mariani', 'password74', -150),
('Martina', 'Caruso', 'martina.caruso', 'password75', 7600),
('Martina', 'Ferrara', 'martina.ferrara', 'password76', -9200),
('Sara', 'Gatti', 'sara.gatti', 'password77', 4300),
('Sara', 'Pellegrini', 'sara.pellegrini', 'password78', -2600),
('Alessia', 'Villa', 'alessia.villa', 'password79', 5800),
('Alessia', 'Marchetti', 'alessia.marchetti', 'password80', 100),
('Elisa', 'D''Angelo', 'elisa.dangelo', 'password81', -3300),
('Elisa', 'Bernardi', 'elisa.bernardi', 'password82', 6700),
('Giorgia', 'Martini', 'giorgia.martini', 'password83', -9900),
('Giorgia', 'Serafini', 'giorgia.serafini', 'password84', 2500),
('Federica', 'Rinaldi', 'federica.rinaldi', 'password85', 800),
('Federica', 'Leone', 'federica.leone', 'password86', -4100),
('Lucia', 'Vitale', 'lucia.vitale', 'password87', 6900),
('Lucia', 'Coppola', 'lucia.coppola', 'password88', -1200),
('Veronica', 'De Santis', 'veronica.desantis', 'password89', 3500),
('Veronica', 'Palumbo', 'veronica.palumbo', 'password90', -700),
('Silvia', 'Sanna', 'silvia.sanna', 'password91', 4400),
('Silvia', 'Farina', 'silvia.farina', 'password92', -8800),
('Daniela', 'Riva', 'daniela.riva', 'password93', 2300),
('Daniela', 'Donati', 'daniela.donati', 'password94', 100),
('Monica', 'Piras', 'monica.piras', 'password95', -5500),
('Monica', 'Sala', 'monica.sala', 'password96', 6600),
('Serena', 'Parisi', 'serena.parisi', 'password97', 200),
('Serena', 'Conte', 'serena.conte', 'password98', -3000),
('Alice', 'Messina', 'alice.messina', 'password99', 7700),
('Alice', 'Rossetti', 'alice.rossetti', 'password100', -100);
```

Definire poi la classe `CliManager` con le seguenti caratteristiche
#### CliManager
##### Costruttore
Costruttore che acquisisce tutti i `service` necessari al suo funzionamento e che lancia il menu a terminale
##### Metodo: `printOptions`
Metodo che presenta le possibili scelte all'utente, e le esegue quando richieste. Questo metodo termina la sua esecuzione solo a richiesta esplicita dell'utente (*loop infinito*).

###### Opzioni disponibili nel menu
- stampa tutti gli utenti presenti in tabella
- inserisci un nuovo utente (richiedento tutti i dati necessari)
- modificare i dettagli di un utente
- eliminare un utente a partire dall'`id`

### [BONUS] Fase 3
Aggiungere al menu le seguenti funzioni:
- trovare tutti gli utenti con nome che inizia per `a`
- trovare tutti gli utenti con credito superiore ai 10 euro *(attenzione alle conversioni)*
- trovare tutti gli utenti con nome `NULL` o cognome `NULL`
- trovare tutti gli utenti con credito positivo ma inferiore ai 10 euro *(attenzione alle conversioni)*
## Day 2
### Fase 1
Introdurre la seguente entità all'interno dello stesso progetto l'entita' **Role** che descrive il ruolo dell'utente all'interno del sw (es: utente normale, amministratore, god, ecc)

#### Role
- nome : String : VARCHAR
- descrizione : String : VARCHAR

##### Entità
L'entità dovra' fornite tutti i campi privati, proprietà `getter`/`setter` e implementazione sensata del metodo `toString`

##### Repo
Definire `query` custom **solo se necessario**

##### Service
Definire almeno i 4 metodi principali:
- `findAll`: trova tutti gli utenti presenti in tabella
- `save`: crea/aggiorna utenti
- `findById`: recupera utente a partire dall'`id`

### Fase 2
Aggiungere relazione all'interno delle entità (`@OneToMany` e `@ManyToOne`) con tipi di dato coerenti alla direzione della relazione

> [!note] per ogni utente c'e' un solo ruolo ; per ogni ruolo ci sono tanti utenti

> [!attention] RIGENERARE IL DB SE LA RELAZIONE NON VIENE CREATA AUTOMATICAMENTE

Inserire dati nella nuova tabella
```sql
-- TODO!
```

Aggiungere la stampa del ruolo all'interno del `toString` dello `User` e permettere di scegliere il ruolo in fase di creazione di un nuovo utente.

### [BONUS] Fase 3
Dare la possibilità di modificare il ruolo di un utente