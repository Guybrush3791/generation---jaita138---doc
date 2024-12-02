# Scanner in Java
Si ricordi che nella lettura di stringe seguite da intero tramite java `Scanner` presenta problemi di caratteri terminatori. Nei casi in cui si voglia leggere una stringa dopo un valore numerico, procedere come segue
```java
Scanner sc = new Scanner(System.in);

System.out.println("Dammi un valore intero:");
int userValue = sc.nextInt();
sc.nextLine(); // <-- AGGIUNGERE QUESTA ISTRUZIONE

System.out.println("Hai inserito: " + userValue);

System.out.println("Dammi un colore:");
String colore = sc.nextLine();

System.out.println("Hai inserito: " + colore);

System.out.println("Dammi una canzone:");
String canzone = sc.nextLine();

System.out.println("Hai inserito: " + canzone);

sc.close();
```