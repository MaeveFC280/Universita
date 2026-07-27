---
Materia: Basi di dati
tags:
  - PL-SQL
  - SQL
  - SQL_Dinamico
Imparato: true
Ordine: 9
---
Consente di creare in maniera dinamica istruzione [[Introduzione SQL|SQL]] nel corpo procedurale [[Fondamenti di PL-SQL|PL/SQL]]
La parte definita all'interno di [[Fondamenti di PL-SQL|DECLARE]] è detta **SQL Statico**.
**Il comando SQL viene costruito a RUNTIME come insieme di parti fisse e variabili conservate in una stringa. A tempo di esecuzione la stringa viene eseguita come comando.**
## Comandi come stringhe
I comandi vengono costruiti tramite variabili di tipo `VARCHAR`. Si compone l'istruzione e viene salvata in una variabile, dopodiché si chiede al compilatore di controllare che sia ben scritto.
- `EXECUTE IMMEDIATELY`: controlla ed esegue alla stesso momento
- `PREPARE + EXECUTE`(SQL standard): separa controllo ed esecuzione
Per poter manipolare le stringhe è possibile usare funzioni apposite.
## `EXECUTE` con parametri
È possibile specificare il passaggio di parametri al comando che si va ad eseguire
````plsql
EXECUTE <nome_comando> USING (lista_variabili)
````
### Esempio
Considerando questa consegna:
*Si scriva una funzione [[Introduzione SQL|SQL]] che riceve in ingesso una lista di codici di partite separate dal carattere speciale @ e utilizzando SQL DINAMICO si restituiscano i pezzi eliminati da certe partite*
````PLSQL
SELECT DISTINCT pezzo
FROM ELIMINATO
WHERE 1
	AND pezzo IN(
		SELECT pezzo
		FROM ELIMINATO
		WHERE codP=<codicePartita1>)
	AND pezzo IN (
		SELECT pezzo
		FROM ELIMINATO
		WHERE codP=<codicePartita2>)
````
- **`WHERE 1` serve a rendere identici i blocchi successivi, venendo entrambi preceduti da `AND`**
- Il `<codice_partita>` è la **parte variabile** del codice
Risalgo con un `LOOP` alle sottostringhe di *`CodPIn1@CodPIn2@CodPIn3...`*
````PLSQL
LOOP
	POS=INSTR(listaIn,'@', DA)
	-- ritorna la posizione della sottostringa, con possibile offset
	codiceIn=SUBSTR(listaIn, DA, POS-1)
	-- separa e tira fuori la stringa da a certe posizioni
	DA=POS+1;
````
Quindi in forma completa il codice è:
````PLSQL
CREATE OR REPLACE FUNCTION pezzi_eliminati (listaPartiteIn VARCHAR)
	RETURN VARCHAR2
IS
DECLARE
	res VARCHAR2(1000):='';
	estrai_pezzi SYS_REF.CURSOR RETURN Pezzi.Pezzo%TYPE;
	POS INTEGER :=0;
	codPartita TAB.CodP%TYPE;
	comando1 VARCHAR(1000):= 'SELECT DISTINCT pezzo FROM ELIMINATO  
		WHERE 1'
	comando2 VARCHAR(1000):= ' AND pezzo IN(
		SELECT pezzo FROM ELIMINATO WHERE codP= '
	comando3 VARCHAR(2):= ') '
	comandoTOT VARCHAR(2000) = comando;
	pezzoOut Pezzi.Pezzo&TYPE;
BEGIN
	LOOP
		POS=INSTR(listaIn,'@', DA)
		EXIT WHEN POS=0;
		codicePartita=SUBSTR(listaPartiteIn, DA, POS-1)
		DA=POS+1;
		comandoTOT := comandoTOT || comando2 || codPartita || comando3;
	ENDLOOP
	
	OPEN estraiPezzi FOR comandoTOT
	LOOP
		FETCH estraiPezzi
		EXIT WHEN estraiPezzi%NOT_FOUND
			res = res || pezzoOut || ';'
	ENDLOOP
	res = RTRIM(res,';');
END
````

