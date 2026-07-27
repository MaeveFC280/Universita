---
Materia: Basi di dati
tags:
  - PL-SQL
  - SQL
Imparato: true
Ordine: 7
---
Un cursore SQL è un oggetto che permette di **attraversare un set di risultati riga per riga**. Mentre le query SQL tradizionali operano su insiemi di dati, i cursori consentono **operazioni basate su righe singole**. 
Il cursore va dichiarato insieme alla variabili
````plsql
DECLARE
	CURSOR mio_cursore IS SELECT * FROM <tabella> WHERE <condizione>;
	mia_riga tabella%ROWTYPE;
BEGIN
	OPEN mio_cursore;
	LOOP
		FETCH mio_cursore INTO mia_riga;
		EXIT WHEN mio_cursore%NOTFOUND;
		DBMS_OUTPUT.put_line(mia_riga.attributo);
	END LOOP
	CLOSE mio_cursore;
END
````

- `DECLARE`: Stabilisce la `SELECT` da eseguire, senza eseguirla ancora.
- `OPEN`: Consente di eseguire la `SELECT`, imposta e riempie in buffer con i dati posizionando il cursore immediatamente prima della prima riga.
- `CLOSE`: Rilascia la memoria, permettendo di riutilizzare il cursore solo dopo aver riaperto.
- `FETCH`: Consente di trasferire le informazioni dalla riga corrente alla struttura dati definita. Va inserito all'interno di un [[Strutture di iterazione|costrutto iterativo]] per scorrere tutte le righe presenti.
- `LOOP`: Scorre il buffer, permettendo di accedere a tutte le righe.

Bisogna sempre usare una `INTO` quando si usano istruzioni di `SELECT` all'interno di corpi procedurali [[Fondamenti di PL-SQL|PL/SQL]].

È obbligatorio usare un cursore se non si ha certezza di un risultato di una singola riga.

Un buon strumento è `%NOTFOUND`, un attributo del cursore che restituisce `TRUE` quando le righe sono finite.
[[Fondamenti di PL-SQL|Così come con le tabelle normali,]] è possibile usare `%ROWTYPE` anche con i cursori.