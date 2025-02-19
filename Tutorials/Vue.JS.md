# Create Project
## VSCode
Aprire cartella vuota in VSCode, e aprire terminale:
- aprire terminale (per Windows `git bash`) e dare seguente comando
```sh
yarn dlx create-vue@latest
yarn create vue@latest # se il primo non dovesse funzionare
yarn create vue # se i primi due non dovessero funzionare
```
- rispondere alle domande come segue
```sh
yarn create vue                                                                  

yarn create v1.22.22
[1/4] Resolving packages...
[2/4] Fetching packages...
[3/4] Linking dependencies...
[4/4] Building fresh packages...
success Installed "create-vue@3.14.2" with binaries:
      - create-vue

Vue.js - The Progressive JavaScript Framework

✔ Project name: … [nome-progetto]
✔ Add TypeScript? … No 
✔ Add JSX Support? … No 
✔ Add Vue Router for Single Page Application development? … Yes
✔ Add Pinia for state management? … No 
✔ Add Vitest for Unit Testing? … No 
✔ Add an End-to-End Testing Solution? › No
✔ Add ESLint for code quality? › Yes
✔ Add Prettier for code formatting? … Yes
```
> [!note] YES alle seguenti
> - `Add Vue Router ...`
> - `Add ESLint ...`
> - `Add Prettier ...`
- aprire VSCode nella cartella effettiva del progetto
- aprire terminale ed esegure i seguenti comandi
```sh
yarn install # solo la prima volta
yarn dev # ad ogni esecuzione
```
Se tutto e' andato a buon fine il terminale loggera la pagina a cui e' possibile connettersi per renderizzare il progetto:
```sh
VITE v6.1.1  ready in 380 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  Vue DevTools: Open http://localhost:5173/__devtools__/ as a separate window
  ➜  Vue DevTools: Press Alt(⌥)+Shift(⇧)+D in App to toggle the Vue DevTools
  ➜  press h + enter to show help
```
Aprire nel browser preferito l'indirizzo riportato alla riga `Local:`
![[Pasted image 20250219171420.png]]