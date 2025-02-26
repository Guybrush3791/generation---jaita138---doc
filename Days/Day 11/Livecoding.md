
## Codebase
Come progetto back-end, utilizzeremo la continuazione dell'[[Springboot + Hibernate + CommandLineRunner|Esercizio Day 10]] a cui andremo ad aggiungere la parte **web** (`controller`, `api`, ecc)
## Repos
### Back-end
[Springboot project GitHub Repository](https://github.com/Guybrush3791/gen-jaita138-springboot-controller-1)
> [!note] In particolare
> Vedi file 
> - `org.generation.jaita138.demo11.controller.BookController`
### Front-end
[Vue.JS + axios project Repository](https://github.com/Guybrush3791/gen-jaita138-vuejs-1)
> [!note] In particolare
> Vedi file 
> - `@/views/HomeView.vue` 
> - `@/components/BookListComponent.vue`
## Day 1
### Back-end
Recuperando il proprio progetto sviluppato in gruppo (vedi [[Springboot + Hibernate + CommandLineRunner|Esercizio Day 10]]) aggiungere un semplice `Controller` per la gestione dei libri da parte del progetto `Vue.JS`.

All'interno del controller sviluppare una rotta in `GET` che ritorna la lista di libri presenti in DB (creare e popolare il db all'occorrenza).

Testare la rotta attraverso `PostMan` (o programma equivalente).

### Front-end
Al progetto precedente sviluppato in `Vue.JS` aggiungere un `Component` che scarichi la lista di libri presenti in `DB` attraverso il `back-end` in `Spring-Boot` e stampi la lista in pagina (front-end non rilevante).

> [!attention] Attenzione
> Il **front-end** non e' abilitato ad accedere ai servizi del **back-end** in mancanza della direttiva `@CrossOrigin` di `Java` a livello di classe del `Controller`

> [!attention] Attenzione
> Per accedere alla libereria `axios` è necessario installarla attraverso `yarn`
> ```sh
> yarn add axios
> ```
> Una volta installata la libreria è necessario riavviare il comando per avviare l'esecuzione
> ```sh
> yarn dev
> ```

## Day 2
### Back-end
Al progetto del giorno precedente aggiungere due semplici `controller` per le entità `Author` e `Genre` con una semplice rotta ciascuno per la lettura di tutta la tabella (senza relazioni).
### Front-end
#### Index
Attraverso un bottone per ogni libro visualizzato, dare la possibilià all'utente di visualizzare i dettagli del libro selezionato, facendo comparire un `blocco HTML` adeguatamente compilato con i dettagli del libro. Dare la possibilità all'utente di chiudere la visualizzazione dei dettagli.
#### Create
Aggiungere un ulteriore bottone che permetta di far scomparire la visualizzazione, in favore di un `form` che permetta di definire i dettagli del nuovo libro che si vuole creare. Fornire all'utente `input` specifici per ogni tipo di inserimento (vedi relazioni `1aN` e `NaM` tra `book` e `author`/`genre`), verificando che il model risultate dal form compilato dall'utente, rispetti la struttura richiesta in ingresso dal **`Back-end`**. 

### Bonus
Tentare di inviare effettivamente il JSON risultate attraverso un `axios.post(...)` al `back-end` e testare il corretto funzionamento della comunicazione loggando i risultato o salvando effettivamente i dati in tabella (**very hard**).
