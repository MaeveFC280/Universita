---
Materia: Programmazione Object-Oriented
tags:
  - Java
Link risorse: https://youtu.be/adTDlH0lhaA?si=ucvjb-vGHYdh16lt
Libro:
Imparato: true
Ordine: 11
aliases:
---
## Tipi di errore 
Le accezioni permettono al programma di non bloccarsi. Gli errori sono divisi in `uncheked` (`Runtime exceptions`) che non obbligano un controllo  in quanto rappresentano tipicamente errori irrecuperabili o eccezioni impreviste/non pianificabili, e le `uncheked`, che richiedono un blocco `try-catch` in quanto errori comuni generalmente  gestibili o recuperabili.
## `try-catch`
Il blocco `try` rinchiude il codice a rischio mentre il `catch` gestisce l'errore.
````java
try{
	//codice
}
catch(Exception e){
	//codice
}
````
## `throw` e ` throws`
`thorw` viene usato per "lanciare" un'eccezione, ma è necessario prima indicarne la possibilità nella firma del metodo con `throws`
````java
returnType methodName() throws ExceptionName{
	throw new Exception("testo");
}
````
## Esempio
````java
Scanner scanner = new Scanner(System.in);

System.out.println("Inserisci un intero da dividere: ");
int x = scanner.nextInt();
System.out.println("Inserisci un intero come divisore: ");
int y = scanner.nextInt();

int z = x/y;
System.out.println("Risultato: " + z);
````
Se y=0 partirà l'exception: *"ArithmeticException: / by zero"* e il programma si interromperà
````java
try{
	Scanner scanner = new Scanner(System.in);

	System.out.println("Inserisci un intero da dividere: ");
	int x = scanner.nextInt();
	System.out.println("Inserisci un intero come divisore: ");
	int y = scanner.nextInt();

	int z = x/y;
	System.out.println("Risultato: " + z);
}
catch(ArithmeticException e){
	System.out.printl("Non puoi dividere per 0");
}
````
Se y=0 verrò mostrata a schermo la scritta *"Non puoi dividere per 0"*. Ma se viene inserita una stringa al posto di un intero il programma verrà interrotto dall'errore: *"InputMismatchException"*
````java
try{
	Scanner scanner = new Scanner(System.in);

	System.out.println("Inserisci un intero da dividere: ");
	int x = scanner.nextInt();
	System.out.println("Inserisci un intero come divisore: ");
	int y = scanner.nextInt();

	int z = x/y;
	System.out.println("Risultato: " + z);
}
catch(ArithmeticException e){
	System.out.printl("Non puoi dividere per 0");
}
catch(InputMismatchException e){
	System.out.printl("Inserisci un numero, altrimenti causerai l'errore "+ e);
}
````
Ora se viene inserita una stringa al posto di un intero apparirà la scritta *"Inserisci un numero, altrimenti causerai l'errore InputMismatchException"*.