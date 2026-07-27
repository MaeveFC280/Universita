---
Materia: Basi di dati
tags:
  - progettazione_concettuale
  - modello_logico
Libro: '"Sistemi di basi di dati. Fondamenti e complementi"'
Imparato: true
Ordine: 1
aliases:
  - schema logico
  - modello logico
---
Il modello relazionale **permette di trattare i dati ad un livello logico senza preoccuparsi del livello fisico ovvero di come i dati sono effettivamente elaborati e memorizzati**.
È definito in termini di **tuple, relazioni, domini e attributi**.

![[Screenshot 2026-06-11 alle 09.34.32.png]]
## Dominio
- Insieme di valori atomici 
- Deve essere definito da un tipo di dati
- Ad ogni dominio deve essere assegnato un nome 
## Attributi
L'attributo specifica il ruolo de dominio
## Schema di relazione
Definisco schema di relazione l'insieme di:
- Nome della relazione seguita dai suoi attributi, ognuno definito dal proprio dominio. $R(A_{1}\dots A_{n})$ 
- Per ogni $A_{i}$ indico $dom(A_{i})$
- La relazione è descritta completamente dallo schema
## Relazione
Fissato la schema di relazione definisce relazione $r$ su $R(A_{1}\dots A_{n})$ un sottoinsieme del prodotto cartesiano: $r\underline{\subset}\text{dom}(A_{1})\times\dots \text{dom} (A_{i})\times\dots \times \text{dom}(A_{n})$  $r$ è un insieme
## Ordinamento
Ogni tupla è un insieme **ordinato** di elementi. L'ordine degli elementi di per se non è importante, ma tutte le tuple devono avere lo stesso ordinamento.
## Valori nulli
Per indicare un valore nullo si utilizza `NULL`
## Database relazionale 
Un insieme di schemi di relazione è detto **database**: $\text{DB}=\{r_{1\dots r_{n}}\}$
## Superchiave
Sia $S(A_{1}\dots A_{n})$uno schema di relazione:
- Si definisce [[Chiavi|superchiave]] un sottoinsieme di $(A_{1}\dots A_{n})$ che consente di individuare una istanza in modo **univoco** 
- Se due istanze hanno la stessa superchiave allora sono identiche
L'insieme delle superchiavi sono le **chiavi candidate**, e tra di esse viene scelta la **[[Chiavi|primary key]]** 
All'interno delle tabelle del modello relazionale la chiave principale va **sottolineata**, mentre le [[Chiavi|chiavi esterne]] vanno scritte in italico.![[Screenshot 2026-06-11 alle 10.00.50.png]]