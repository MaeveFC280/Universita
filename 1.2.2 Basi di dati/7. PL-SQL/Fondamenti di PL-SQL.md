---
Materia: Basi di dati
tags:
  - PL-SQL
  - SQL
aliases:
  - basi di pl/sql
  - PL/SQL
Imparato: true
Ordine: 1
---

## Introduzione
PL/SQL sta per Procedural Language/Structured Query Language. PL/SQL offre una serie di comandi procedurali organizzati all'interno di blocchi che completano ed estendono la portata di SQL. PL/SQL è l'estensione di Oracle di [[Introduzione SQL|SQL]] progettata per gli sviluppatori che lavorano con il database Oracle. È anche possibile utilizzare PL/pgSQL in ambiente PostegreSQL.
- Aumenta le perfomance
	- meno comunicazione tra client e [[Definizioni|DBMS]] grazie ai blocchi
	- nessuna conversione di tipo di dato
- Possibile lavorare sui dati riga per riga grazie ai [[Cursore|cursori]]
## Struttura blocco
Un blocco PL/SQL è definito dalle parole chiave `DECLARE`, `BEGIN`, `EXCEPTION` e `END`, che suddividono il blocco in tre sezioni:
````PLSQL
[DECLARE
-- dichiarazione delle variabili
]
BEGIN
-- istruzioni
[EXCEPTION
-- gestione degli errori
]
END;
````
- **Dichiarazione**: istruzioni che dichiarano variabili, costanti e altri elementi di codice, che possono quindi essere utilizzati all'interno di quel blocco
- **Esecuzione**: istruzioni che vengono eseguite quando il blocco viene eseguito
- **[[Gestione degli errori|Gestione delle eccezioni]]**: una sezione appositamente strutturata che puoi utilizzare per "catturare" o intrappolare eventuali eccezioni sollevate quando la sezione eseguibile viene eseguita

L'unica parte obligatoria è `BEGIN`.

Un blocco stesso è un'istruzione eseguibile, quindi puoi annidare i blocchi all'interno di altri blocchi.
````PLSQL
DECLARE
  l_message VARCHAR2 (100) := 'Hello!';
  
BEGIN
	DECLARE
	  l_message2 VARCHAR2(100):= l_message || 'World!';
	BEGIN
		DBMS_OUTPUT.put_line (l_message2);
	END;
	
EXCEPTION
	WHEN OTHERS -- Cattura quasi tutti gli errori possibili
	THEN
	DBMS_OUTPUT.put_line(DBMS_UTILITY.format_error_stack);
END;
````

È possibile richiamare questi nomi quando vengono resi non anonimi da una [[Funzioni e procedure|procedura o funzione]].
## Variabili
È possibile copiare il tipo di un attributo con una notazione specifica: **`tabella.attributo%TYPE`**
Questa possibilità è utile quando si definiscono i [[Cursore|cursori]].
Altri tipi disponibili quando si definisce una variabile sono:
- `NUMBER(n)`: SQL data type
- `VARCHAR2(n)`: SQL data type
- `BOOLEAN`: PL/SQL only data type
- `NUMBER(x,y)`: SQL data type
- `VARCHAR(n)`: SQL data type
I nomi delle variabili non possono contenere: &,-,/,' '
È anche possibile usare **`tabella%ROWTYPE`** per creare una variabile che può contenere una tupla con gli stessi tipi della tabella scelta.
## Gestire i risultati della `SELECT`
Quando una `SELECT` restituisce un singolo valore esso va conservato con `INTO`
Se la `SELECT` non restituisce niente il programma va in errore, necessitando quindi della gestione con `EXCEPTION`.
````PLSQL
DECLARE
mia_riga tabella%ROWTYPE
BEGIN
	SELECT *
	INTO mia_riga
	FROM tabella
END
````
Se si vogliono ottenere più righe è necessario l'utilizzo di un [[Cursore|cursore]].