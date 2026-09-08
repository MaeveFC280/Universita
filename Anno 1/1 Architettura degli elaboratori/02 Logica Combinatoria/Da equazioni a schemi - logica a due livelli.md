---
Materia: Architettura degli elaboratori
tags:
  - logica_combinatoria
  - Logica
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 2.4-2.5'
Imparato: true
Ordine: 206
aliases:
  - logica a due livelli
  - logica multilivello
  - schematico
---
## Lo schematico
Uno **schematico** (*schematic*) è il diagramma di un circuito digitale che mostra gli elementi e i fili che li collegano.
![[schematic t=abc...]]
### Convenzioni di disegno
- Gli **ingressi** stanno a sinistra (o in alto).
- Le **uscite** stanno a destra (o in basso).
- Quando possibile le porte scorrono **da sinistra a destra**.
- Meglio fili **rettilinei** che con molte piegature.
- I fili si connettono sempre a **T**.
- Un **pallino** dove i fili si incrociano indica connessione; fili che si incrociano **senza** pallino **non** sono connessi.

Disegnare in modo consistente rende gli schemi leggibili e gli errori evidenti.

## Logica a due livelli
Qualunque equazione in[[Forme canoniche SOP e POS| forma SOP]] si può disegnare direttamente come schema:
- **primo livello**: un banco di porte AND (una per [[Terminologia booleana - letterali mintermini maxtermini|implicante]]), con gli inversori necessari sugli ingressi;
- **secondo livello**: una porta OR che raccoglie le uscite degli AND.

Si chiama **logica a due livelli** perché consiste in due livelli di porte (a parte gli inverter di ingresso).

> [!info] Conseguenza teorica
> Ogni funzione booleana è realizzabile con logica a due livelli. Ciò garantisce l'esistenza di una soluzione, ma non che sia la più economica.

## Logica multilivello
Usare **più di due livelli** di porte spesso riduce il costo in hardware, anche se aumenta il numero di livelli attraversati (e quindi, in genere, il [[Timing combinatorio - ritardo di propagazione e cammino critico|ritardo di propagazione]]).

*Esempio classico: la **parità a $N$ ingressi**. In due livelli servirebbero $2^{N-1}$* *porte AND; con un albero di XOR bastano $N-1$ porte, disposte su più livelli.*

Il progetto multilivello è un compromesso tra:
- **area/costo** (numero di porte e di ingressi per porta),
- **ritardo** (numero di livelli sul cammino critico),
- **potenza**.
