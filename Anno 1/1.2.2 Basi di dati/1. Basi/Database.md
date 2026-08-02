---
Materia: Basi di dati
tags:
  - DB
Link risorse:
Imparato: true
aliases:
Ordine: 0
---
## Tipi di database
- Applicazioni **Tradizionali** (Assicurazioni, anagrafiche, prenotazioni…) (Gerarchico, relazionali, SQL)
- Applicazioni**Moderne** (Shopping online, multimediale, real-time, geolocalizzazione…) (NoSQL)
## Caratteristiche di una BDD (base di dati)
- Non deve avere ridondanze (opzionale)
- [[Definizioni|Dati]] facilmente accessibili 
- **Descrizione del dato**
- **Organizzazione** 
- **Permanenza** 
## Funzionalità
- **Definire** tipi, strutture e vincoli
- **Costruire e caricare** il contenuto iniziale su un mezzo di memorizzazione secondario
- **Manipolare** il database: recuperare e modificare le informazioni e accedere al database 
- **Elaborare** i [[Definizioni|dati]] e **condividerli** tra gli utenti **con** **consistenza**
- **Fornire protezione** per prevenire accessi non autorizzati
- **Elaborazione attiva** dei [[Definizioni|dati]]
- Tool di **presentazione** e **visualizzazione** [[Definizioni|dati]]
- Strumenti per la **manutenzione**
## Operazioni sul DB
1. **Definizione alla struttura**
	- Nomi di file e campi
	- Tipo dei [[Definizioni|dati]]
	- Relazioni fra i record
2. **Costruzione database**
	- Caricamento dei [[Definizioni|dati]]
3. **Manipolazione del database**
	- Interrogazione query
	- Aggiornamento dei [[Definizioni|dati]]
## Proprietà di un DB
1. **Abilitazione di viste multiple**
2. **Condivisione di dati/transazioni multiutente**
3. **Controllo della concorrenza**
## Proprietà _ACID_ delle transazioni:
- **Atomicità** (Ricoveri subsystem): Indivisibile, le operazioni avvengono in blocchi (**commit** o **rollback**)
- **Consistenza** (Programmatori):
- **Isolamento** (Sistema di controllo della concorrenza): Meccanismo di controllo acceso ai dati, aspettando fine transazione prima di operare
- **Durabilità** (Sistema di gestione dell’affidabilità): Deve garantire la permanenza dei dati
