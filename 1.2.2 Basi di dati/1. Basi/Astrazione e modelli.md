---
Materia: Basi di dati
tags:
  - DB
Libro: '"Sistemi di basi di dati. Fondamenti e complementi" Capitolo 2'
Link risorse:
Imparato: true
Ordine: 1
aliases:
  - architettura di una base di dati
  - architettura e linguaggio
  - astrazione e modelli
---
## Astrazione e modello dei dati
- **Modello di dati**: Insieme di concetti usati per descrivere:
	- La **struttura** base dei dati (Tabelle, Attributi, JSON, NoSQL)
	- Le **operazioni** per manipolare le strutture (Inserimento, Cancellazione, Modifica, Query)
	- I **[[Vincoli | vincoli]]** che la [[Definizioni|base di dati]] deve rispettare (Trigger, Assertion)
Il modello dati permette di rappresentare una certa realtà, fornendo un insieme di simboli per descriverla.
$$
Modello+Minimondo=Rappresentazione
$$
- **Astrazione**: I dettagli di implementazione sono nascosti agli utenti. Bisogna trovare ciò che unisce gli elementi del [[Definizioni|minimondo]].

I modelli possono essere:
- **Concettuali**/High Level/Entity Based: Più vicino alla descrizione (UML, ER)
	- _Entità_: I concetti dominanti del [[Definizioni|minimondo]]
	- _Attributi_: Aspetti importanti delle entità
	- _Relazioni_: Interazioni tra entità
- Di basso livello: Modelli fisici
- Implementabili/Rappresentabili: Metà tra concettuale e fisico, regole di traduzione
- Autodescrittivi: Combinazione tra astratto e noti
## Schemi istanze e stati
Ogni oggetto nello schema è detto **costrutto di schema**.
- Quando il database non contiene nulla è detto in uno **stato vuoto**
- Quando il database contiene un solo elemento è detto in uno **stato iniziale**
- Si definisce **snapshot** (stato) del database **l’insieme di istanze presenti nel database in un determinato momento**
- Ogni volta che la db viene aggiornato **cambia stato**
- In ogni istante la db ha uno **stato corrente** 
- Ogni stato della db dovrebbe essere uno **stato valido**
## Architettura a tre livelli
 Gli schemi sono solo descrizioni dei dati, mentre i dati esistono a livello fisico
La trasformazione di richieste e dati fra i livelli è detta **mapping.**
Lo schema a 3 livelli rinforza la **indipendenza:**
- **Indipendenza logica**: Cambiare lo schema logico non cambia lo schema esterno
- **Indipendenza fisica**: Cambiare lo schema fisico non influenza lo schema logico 
Aumenta anche la **sicurezza** e **flessibilità**.
È però più **complessa**, **latente** e **costosa**.
## Linguaggi del DBMS
Ad ogni livello è associato un linguaggio: VDL, DDL, SDL
Un DBMS deve fornire ad ogni categoria i utenti delle **interfacce** e dei **linguaggi** adeguati.
Completata la **progettazione** della base di dati e scelto un DBMS per implementarla, bisogna  specificare gli schemi concettuale e fisico e il mapping fra i due.
$$
SQL=(DDL+VDL)
$$
![[Pasted image 20260610201924.png]]
Ma non esiste uno specifico linguaggio SDL
**SQL= Structured Query Language.**
È un linguaggio **dichiarativo**: specifico cosa voglio ottenere e non come
Linguaggio specifico per manipolare i dati: **DML**
Esistono:
- DML di **basso livello** o procedurale:
	- Deve essere incapsulato (embedded) in un linguaggio general-purpose
	- È detto **record-at-a-time**, perché recupera un solo record alla volta: necessita le strutture di iterazione del linguaggio in cui è immerso
- DML di **alto livello** o non-procedurale:
	- Possono essere specificati **interattivamente** da terminale.
	- Possono essere inglobati (embedded) in un linguaggio di programmazione
	- general-purpose (precompilazione).
	- Sono detti **set-at-a-time** o set-oriented perché possono specificare e recuperare molti record con un singolo statement DML
	- Sono detti dichiarativi perché una query di un DML high-level spesso specifica quale dato deve essere ritrovato piuttosto che come ritrovarlo.
## Architetture
![[Screenshot 2026-06-10 alle 20.23.14.png|697]]![[Screenshot 2026-06-10 alle 20.23.44.png]]
![[Screenshot 2026-06-10 alle 20.24.33.png]]![[Screenshot 2026-06-10 alle 20.24.53.png]]