---
Materia: Basi di dati
tags:
  - SQL
  - PL-SQL
Imparato: true
Ordine: 6
---
I triggers sono lanciati automaticamente dal [[Definizioni|DBMS]] al verificarsi di una certa condizione. Gli eventi possibili sono:
- `DELETE`
- `UPDATE`
- `INSERT`
Un trigger ha una serie di parametri:
- Quale evento scatena la reazione?`INSERT/UPDATE/DELETE`
- Quando si scatena l'azione? `BEFORE/AFTER/INSTEAD OF`
- Quali condizioni? `WHEN` (opzionale)
- Reazione globale o per riga? `FOR EACH ROW` (opzionale)
- Un trigger può essere sostituito da un nuovo trigger con `REPLACE`
- È possibile eliminare un trigger con `DROP` o disabilitarlo con `ALTER <nome_trigger> SET ENABLD/DISABLED`
````PLSQL
CREATE OR REPLACE TRIGGER <nome_trigger> 
[AFTER/ BEFORE/ INSTEAD OF] <operazione> 
[FOR EACH ROW] (nel caso di reazione per riga)
WHEN <condizione>
BEGIN
	<corpo della procedura>
END
----------------------------------------------------------------------
Dove operazione:
- INSERT ON <nome_tabella> 
- DELETE ON <nome_tabella> 
- UPDATE ON <nome_tabella> [OF <nome_attributo>]
````
Quando si lavora riga per riga `[FOR EACH ROW]` il [[Definizioni|DBMS]] mette a disposizione due strutture dati speciali:
- `OLD`: contiene i valori della riga prima dell'avvio del trigger
- `NEW`: contiene i nuovi valori di riga
Si accede agli attributi usando la dot notation: `OLD.<nome>`,  `NEW.<nome>`

Ciò che è contenuto tra `BEGIN` e `END` è definito **transazione**, ovvero viene compiuta nella sua interezza o la base di dati viene riportata allo stato precedente.

È anche possibile precedere `BEGIN` da un `DECLARE` per dichiarare delle [[Fondamenti di PL-SQL|variabili]] in caso di necessita.