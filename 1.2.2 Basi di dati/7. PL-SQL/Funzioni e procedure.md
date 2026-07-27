---
Materia: Basi di dati
tags:
  - PL-SQL
  - SQL
  - funzioni
aliases:
  - funzione
  - procedura
Imparato: true
Ordine: 5
---
È possibile dare nomi a blocchi [[Fondamenti di PL-SQL|PL/SQL]] tramite procedure o funzioni.
- `CREATE OR REPLACE PROCEDURE <nome_procedura>`: Crea una **procedura**. Essa non ha  valore di ritorno, ma ha come parametri:
	- `IN`: solo di input
	- `OUT`: solo di output
	- `IN/OUT`: sia di input sia si output
````PLSQL
CREATE OR REPLACE PROCEDURE hello_world
IS
l_message VARCHAR2(100) := 'Hello World!';
BEGIN
DBMS_OUTPUT.put_line(l_message);
END hello_world;
````
- `CREATE OR REPLACE FUNCTION <nome_funzione>`: Crea una **funzione**. Essa deve avere un valore di ritorno e ha solo parametri di input. Sono estensioni di SQL e possono essere usati solo all'interno delle `SELECT`
````PLSQL
CREATE OR REPLACE FUNCTION hello_place (place_in IN VARCHAR2)
	RETURN VARCHAR2
IS
BEGIN
 RETURN 'Hello' || place_in;
END hello_place;
````
I parametri non sono obbligatori.
Sono necessari i [[Cursore|cursori]] se si vogliono gestire risultati su più righe.