---
Materia: Basi di dati
tags:
  - SQL
  - PL-SQL
  - SQL_Dinamico
Link risorse:
Libro:
Imparato: true
Ordine: 90
aliases:
  - dizionario
  - catalogo
---
Il [[Definizioni|DBMS]] conserva un catalogo di tutti gli oggetti presenti nel sistema. Il data dictionary contiene il nome di: tabelle, colonne ed utenti.
## Viste
Solo il DBMS ha accesso a queste informazioni.
Agli utenti sono consentite le query solo tramite specifiche `VIEW`.
Le viste sono di 3 tipi, in base al **ruolo dell'utente**:
- `DBA_`: solo amministratore
- `ALL_`: utente con abilitazione
- `USER_`: solo proprietario

`ALL_TABLES`: tutti i nomi delle tabelle che esistono nel DBMS
- `ALL_ALL_TABLES`
- `USER_ALL_TABLES`
Sono viste di `ALL_TABLES` per gli utenti abilitati/proprietari. Le colonne sono:
- `OWNER`
- `TABLE_NAME`
- ...

`ALL_TAB_COLUMNS`: tutti i nomi di tutte le tabelle
-  `OWNER`
- `TABLE_NAME`
- `COLUMN_NAME`
- `DATA_TYPE`