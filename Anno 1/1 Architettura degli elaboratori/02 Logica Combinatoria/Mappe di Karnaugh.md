---
Materia: Architettura degli elaboratori
tags:
  - algebra_booleana
  - logica_combinatoria
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 2.7'
Imparato: true
Ordine: 208
aliases:
  - K-map
  - mappa di Karnaugh
  - minimizzazione
---
Un metodo **grafico** per semplificare [[Porte logiche|logica booleana]]. Sfruttano la capacità visiva umana di riconoscere schemi al posto della manipolazione algebrica.
Il principio sottostante è il **[[Assiomi e teoremi dell algebra di Boole|teoremi booleani]]**:
$$P\overline{A} + PA = P$$
due termini che differiscono per un solo letterale si fondono, eliminando quel letterale.
La K-map rende **immediatamente visibili** i termini combinabili, mettendoli fisicamente vicini.
## Struttura
- Ogni **casella** rappresenta un **[[Terminologia booleana - letterali mintermini maxtermini|mintermine]]**.
- Ogni casella differisce da quelle **adiacenti** per il cambio di **una sola variabile**.
- Le etichette di riga/colonna seguono l'**ordine di Gray**: `00, 01, 11, 10` — non l'ordine binario naturale. Serve esattamente a garantire l'adiacenza a un bit.
- Le caselle all'estremo destro sono **adiacenti** a quelle all'estremo sinistro (la mappa si "avvolge", come su un toro); lo stesso vale per sopra/sotto.

Leggere i mintermini dalla K-map è equivalente a leggerli dalla tabella di verità: è la stessa informazione, disposta diversamente.
![[Mappe di Karnaugh-1786800841780.webp]]
## Come si minimizza
Si **cerchiano** i gruppi di 1 e si scrive un implicante per ogni cerchio.
- Ogni cerchio è un **implicante**; il cerchio più grande possibile è un
  **implicante primo** (*prime implicant*).
- Le variabili che nel cerchio compaiono **sia in forma diretta sia complementata**
  vengono **eliminate**; restano solo quelle costanti dentro il cerchio.
![[Mappe di Karnaugh-1786800913242.webp]]
### Regole (in ordine)
1. Usa il **minor numero di cerchi** necessario a coprire tutti gli 1.
2. Tutte le caselle di ogni cerchio devono contenere 1.
3. Ogni cerchio deve coprire un blocco **rettangolare** con lati potenza di 2
   (1, 2, 4, 8…).
4. Ogni cerchio deve essere il **più grande possibile**.
5. Un cerchio **può avvolgersi** oltre i bordi della mappa.
6. Un 1 **può essere cerchiato più volte**, se questo permette di ingrandire i cerchi.

### Relazione dimensione ↔ letterali
In una mappa a $N$ variabili, un cerchio di $2^k$ caselle produce un implicante con
$N-k$ letterali. Più grande il cerchio, più semplice il termine.

| Caselle cerchiate | Letterali eliminati |
|---|---|
| 1 | 0 |
| 2 | 1 |
| 4 | 2 |
| 8 | 3 |

## Don't care nelle K-map
Gli X ([[X e Z - don t care contention e nodi flottanti|don't care]]) permettono una minimizzazione **ancora più spinta**: possono essere cerchiati **oppure ignorati**, a scelta, in base a ciò che rende i cerchi più grandi e meno numerosi.
Regola pratica: **cerchia un X solo se ti serve per ingrandire un cerchio**; mai fare un cerchio composto di soli X.
## Limiti
Le K-map funzionano bene fino a **4 variabili** (mappa 4×4), a stento con 5-6 (mappe sovrapposte). Oltre, si usano algoritmi (Quine-McCluskey) e strumenti CAD.

