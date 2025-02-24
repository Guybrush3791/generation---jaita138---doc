
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

> [!note] Attenzione
> Il **front-end** non e' abilitato ad accedere ai servizi del **back-end** in mancanza della direttiva `@CrossOrigin` di `Java` a livello di classe del `Controller`

