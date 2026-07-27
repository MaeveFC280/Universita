---
Materia: Basi di dati
tags:
  - progettazione_concettuale
  - modello_logico
Link risorse:
Libro:
Imparato: true
Ordine: 2
aliases:
---
## Vincoli del modello relazionale
Un modello relazionale deve rispettare dei [[Vincoli]]:
1. Vincoli intrinseci o **impliciti**
	- **No tuple duplicate**
	- **No attributi multipli**
	- **No atributi composti**
	- **No gerarchie**
	- È a questo scopo necessario il **[[Ristrutturazione|mapping]]**
2. Vincoli **di schema**: 
	- Definiti dal [[Astrazione e modelli|DDL]]
	- [[CREATE|Struttura del DB]]
3. Vincoli di **integrità semantica**
	- Non sempre esprimibili nel DB con DDL
	- Hanno bisogno di [[triggers]] o [[Vincoli|assertions]]
## Fasi mapping
Il mapping verso uno schema logico parte dallo schema concettuale [[Ristrutturazione|ristrutturato]].
Il mapping prevede più fasi:
1. Traduco le entità/classi in schemi di relazione
	- Per ogni classe $\text{C}$ creo uno schema di relazione: $\text{C}(A_{1},\dots A_{n})\rightarrow \text{dom}(A_{i}=\text{tipo nella classe})$ 
2. Individuo le [[Chiavi|primary key]]
3. Traduco le associazioni/relazioni
	- È fondamentale disegnare bene il diagramma concettuale con le giuste molteplicità
		- ###### Molti a molti (N:N):
			- Viene creata una tabella ponte con le [[Chiavi|FK]] per rappresentare la relazione 
		- ###### Molti a molti (N:N) di associazione:
			- Mapping delle associazioni normale. La classi di associazione contiene le FK.
		- ###### Uno a molti (1:N):
			- Individuo la classe "debole", quella con molteplicità `*`, e migro la PK della classe forte in essa.
		- ###### Uno a uno (1:1)**:
			- Scelgo una classe da considerare debole e seguo il procedimento 1:N.
			- Altrimenti unisco le due classi in una sola
