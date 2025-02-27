
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
## Day 3
### Back-end
Al progetto `SpringBoot`, aggiungere la rotta con metodo `Post` per il salvataggio di un nuovo libro.
#### Bonus: Validation
Aggiungere la dipendenza nel `pom.xml`
```xml
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-validation</artifactId>
</dependency>
```
> [!attention] È NECESSARIO RIAVVIARE IL PROGETTO

Aggiungere delle regole di validazione alla classe `Book`
```java
@Entity
public class Book {

   // ...

    @NotNull(message = "Title is required")
    @NotBlank(message = "Title is required")
    @Column(length = 64)
    private String title;

	// ...
}
```
Annotare il `@RequestBody Book` come `@Valid`
```java
@RestController
@CrossOrigin("http://localhost:5173/")
@RequestMapping("/api/v1/book")
public class BookController {

    // ...

    @PostMapping
    public ResponseEntity<Book> createBook(
            @Valid @RequestBody Book book) {

	// ...
}
```
Testare la funzionalita' tramite `PostMan` tramite un oggetto che viole una o più delle regole di validazione (ad esempio il titolo vuoto)
```json
{
  "genres": [
    {"id": 1}
  ],
  "title": "",
  "isbn": "12345",
  "year_pub": "2025",
  "author": {"id": 1}
}
```
Il risultato atteso e' un errore in `PostMan`
```json
{
    "timestamp": "2025-02-27T15:59:45.786+00:00",
    "status": 400,
    "error": "Bad Request",
    "path": "/api/v1/book"
}
```
Ed un `log` nel terminale di `SpringBoot` riportante la regola violata
```sh
Validation failed for argument [0] in public org.springframework.http.ResponseEntity<org.generation.jaita138.demo11.db.entity.Book> org.generation.jaita138.demo11.controller.BookController.createBook(org.generation.jaita138.demo11.db.entity.Book): [Field error in object 'book' on field 'title': rejected value []; codes [NotBlank.book.title,NotBlank.title,NotBlank.java.lang.String,NotBlank]; arguments [org.springframework.context.support.DefaultMessageSourceResolvable: codes [book.title,title]; arguments []; default message [title]]; default message [Title is required]] ]
```
### Front-end
Al progetto `VueJS`, dopo aver aggiunto il `form`, aggiungere la chiamata in `axios` per l'invio dei dati del nuovo `Book` al back-end e scaricando e mostrando i dati di tutti i libri aggiornati.