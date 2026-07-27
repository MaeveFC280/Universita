---
Materia: Basi di dati
tags:
  - progettazione_concettuale
Link risorse:
Imparato: true
Ordine: 3
aliases:
---
## Ciclo di vita
La progettazione del database è parte del processo di sviluppo dei sistemi informativi.
- **Sistema informativo:** È una **componente** di una **organizzazione** che gestisce le **informazioni** di interesse
![[Screenshot 2026-06-10 alle 20.27.16.png]]
Un progetto prevede fasi indipendenti l’una dall’altra, i cui prodotti, ovvero **schemi concettuali**, logici e fisici, sono descritti dal **modello dati**.
## Analisi e progettazione
![[Screenshot 2026-06-10 alle 20.27.58.png]]
- definizione matematica basata sul concetto di insieme
- Algebra relazionale
## Modelli
Modelli concettuali:
- indipendenti dal DBMS
Modelli logici:
- Descrivono le relazioni logiche tra elementi della base dati
- Successivo alla scelta del DBMS
Modelli Fisici:
- Dipende fortemente dalla DBMS
Modello concettuale rende più comprensibile il progetto, ignorando i dettagli implementativi, rafforzando l’astrazione concentrandosi sugli aspetti fondamentali e producendo documentazioni grafiche.
## Aspetti informativi rilevanti:
- **Entità**: Elementi informativi di base, concetti fondamentali del minimondo, distinte
- **Associazioni**: Come sono interrelati gli elementi
- **Vincoli**: Le regole che i dati dovrebbero soddisfare
- **Interrogazioni**: Le più importanti forme d’accesso/manipolazione dei dati degli utenti 
- **Frequenza**: Quanto spesso avvengono le interrogazioni
- **Numero di utenti**: Quanti utenti possono interagire simultaneamente
## Documentazione
1. **Schema concettuale** basato sul modello dei **CLASS DIAGRAM [[UML]]**
2. **Dizionari**
	1. Entità e associazioni
	2. Vincoli
	3. Interrogazioni e indicazione della loro frequenza
3. **Schema concettuale** basato sul modello **[[ER|ENTITÀ-RELAZIONI (ER)]]**
## Definizione matematica
- A: Attributo
- E: Entità
- V: Insieme di valori per A
- 
$A:E->P(V)$ L’attributo è una funzione che associa ad una entità l’insieme potenza dei sui valori
$A(E)=\{ \}$ (A è nullo) $A(E)=\{v1\}$(Single value) $A(E)=\{v1…vn\}(multivalore)$
Se A è un attributo composto V=P(v1)x…P(vn)
$P(V)=\{\{\},\{bianco\},\{rosso\},\{blu\},\{bianco rosso\},\{bianco blu\},\{rosso blu\},\{bianco rosso blu\}\}$
$$A:E->P(V)\ \ \ \ A(colore)->\{bianco\ blu\}\ \ \ \ A(colore)->\{\{ \}\}\ \ \ \ A(colore)->\{rosso\}$$
## Istanza di relazione
Definisco un insieme di istanze di relazione(R)
- **R** è una funzione che **lega** n  **entità** ( $E_{1}\dots E_{n}$) e **definisce** un **insieme** con lo **stesso nome** della relazione
$$
r_{i}\in R\ \ r_{i}=(e_{1}\dots e_{n})=istanza\ relazione\
$$
$$
R(e_{1}\dots e_{n})=istanze\ tipi
$$

