---
Materia: Architettura degli elaboratori
tags:
  - algebra_booleana
  - logica_combinatoria
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 2.7'
Imparato: false
Ordine: 208
aliases:
  - K-map
  - mappa di Karnaugh
  - minimizzazione
---

# Mappe di Karnaugh (K-map)

## Cosa sono
Un metodo **grafico** per semplificare equazioni booleane, inventato da Maurice
Karnaugh nel 1953. Sfruttano la capacità visiva umana di riconoscere schemi al posto
della manipolazione algebrica.

Il principio sottostante è il **teorema di combinazione (T10)**:
$$P\overline{A} + PA = P$$
due termini che differiscono per un solo letterale si fondono, eliminando quel letterale.
La K-map rende **immediatamente visibili** i termini combinabili, mettendoli
fisicamente vicini.

## Struttura
- Ogni **casella** rappresenta un **mintermine**.
- Ogni casella differisce da quelle **adiacenti** per il cambio di **una sola variabile**.
- Le etichette di riga/colonna seguono l'**ordine di Gray**: `00, 01, 11, 10` — non
  l'ordine binario naturale. Serve esattamente a garantire l'adiacenza a un bit.
- Le caselle all'estremo destro sono **adiacenti** a quelle all'estremo sinistro (la
  mappa si "avvolge", come su un toro); lo stesso vale per sopra/sotto.

Leggere i mintermini dalla K-map è equivalente a leggerli dalla tabella di verità: è
la stessa informazione, disposta diversamente.

## Come si minimizza
Si **cerchiano** i gruppi di 1 e si scrive un implicante per ogni cerchio.
- Ogni cerchio è un **implicante**; il cerchio più grande possibile è un
  **implicante primo** (*prime implicant*).
- Le variabili che nel cerchio compaiono **sia in forma diretta sia complementata**
  vengono **eliminate**; restano solo quelle costanti dentro il cerchio.

### Regole (da applicare in ordine)
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
Gli X (don't care) permettono una minimizzazione **ancora più spinta**: possono essere
cerchiati **oppure ignorati**, a scelta, in base a ciò che rende i cerchi più grandi e
meno numerosi.
Regola pratica: **cerchia un X solo se ti serve per ingrandire un cerchio**; mai fare
un cerchio composto di soli X.

## Limiti
Le K-map funzionano bene fino a **4 variabili** (mappa 4×4), a stento con 5-6
(mappe sovrapposte). Oltre, si usano algoritmi (Quine-McCluskey) e strumenti CAD.

## Da ricordare
- Ordine di Gray `00, 01, 11, 10`: fondamentale, e fonte di errori d'esame.
- La mappa si avvolge sui bordi (anche i **4 angoli** sono un gruppo valido!).
- Cerchi il più grandi possibile, il meno numerosi possibile.
- $2^k$ caselle ⇒ $k$ letterali in meno.

## Domande flash
1. Perché l'ordine delle colonne è 00, 01, 11, 10 e non 00, 01, 10, 11?
2. I quattro angoli di una mappa a 4 variabili possono formare un unico implicante?
3. Un cerchio di 3 caselle è ammesso?

Collegato a: [[Forme canoniche SOP e POS]] · [[Assiomi e teoremi dell algebra di Boole]] · [[Glitch]]
