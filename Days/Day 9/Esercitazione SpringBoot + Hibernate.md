# Repo
`gen-jaita138-springboot-hibernate-1`

# Todo
## Fase 1
Sulla falsa riga dell'[ultimo esercizio visto a lezione](https://github.com/Guybrush3791/gen-jaita138-springboot-5) generare la tripletta `Entity`, `Repo` e `Service` per la seguente entità:
### Utente
- nome : String : VARCHAR(64)
- cognome : String : VARCHAR(64)
- username : String : VARCHAR(128)
- password : String : VARCHAR(64)
- credito : Int : Int (il valore deve essere espresso in centesimi di euro)

#### Entità
L'entità dovra' fornite tutti i campi privati, proprietà `getter`/`setter` e implementazione sensata del metodo `toString`

#### Repo
Definire `query` custom **solo se necessario**

#### Service
Definire almeno i 4 metodi principali:
- `findAll`: trova tutti gli utenti presenti in tabella
- `save`: crea/aggiorna utenti
- `delete`: elimina utenti
- `findById`: recupera utente a partire dall'`id`

## Fase 2
Dopo aver creato e verificato la presenza di dati in tabella eseguire i seguenti inserimenti attraverso `DBEaver`:
```sql
-- TODO
```

Definire poi la classe `CliManager` con le seguenti caratteristiche
### CliManager
#### Costruttore
Costruttore che acquisisce tutti i `service` necessari al suo funzionamento e che lancia il menu a terminale
#### Metodo: `printOptions`
Metodo che presenta le possibili scelte all'utente, e le esegue quando richieste. Questo metodo termina la sua esecuzione solo a richiesta esplicita dell'utente (*loop infinito*).

##### Opzioni disponibili nel menu
- stampa tutti gli utenti presenti in tabella
- inserisci un nuovo utente (richiedento tutti i dati necessari)
- modificare i dettagli di un utente
- eliminare un utente a partire dall'`id`

## [BONUS] Fase 3
Aggiungere al menu le seguenti funzioni:
- trovare tutti gli utenti con nome che inizia per `a`
- trovare tutti gli utenti con credito superiore ai 10 euro *(attenzione alle conversioni)*
- trovare tutti gli utenti con nome `NULL` o cognome `NULL`
- trovare tutti gli utenti con credito positivo ma inferiore ai 10 euro *(attenzione alle conversioni)*

