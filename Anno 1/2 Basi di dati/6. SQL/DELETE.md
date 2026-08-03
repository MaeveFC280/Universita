---
Materia: Basi di dati
tags:
  - SQL
  - DML
  - incompleto
Imparato: true
Ordine: 8
---
The `DELETE` statement is used to delete existing records in a table.
````mysql
DELETE FROM table_name WHERE condition;
````
It is possible to delete all records in a table, without deleting the table. This means that the table structure, attributes, and indexes will be intact.
````mysql
DELETE FROM table_name;
````
## `CASCADE`
In SQL, the `ON DELETE CASCADE` constraint instructs the database to **automatically delete all child rows referencing the deleted parent row**. It triggers the operation recursively through [[Chiavi|foreign key]] chains, deleting dependent data in one [[Database|atomic transaction]].

Quando esegui un comando `DELETE` su una riga principale, il database mette in pausa l'esecuzione finale per controllare le sue regole della chiave esterna nel seguente ordine:
- **Identificazione**: il motore guarda l'indice della chiave esterna per trovare tutte le righe nelle tabelle figlio che corrispondono all'ID eliminato.
- **Esecuzione**: prima (o durante) la rimozione della riga principale, il motore elimina le righe figlio identificate.
- **Convalida**: il database garantisce che non rimangano righe orfane. Se tutte le eliminazioni vanno a buon fine, la transazione è finalizzata.
Dovresti notare che il processo di cui sopra avverrà solo se hai definito il vincolo ON DELETE CASCADE, come vedremo più avanti nell'articolo.