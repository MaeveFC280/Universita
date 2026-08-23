---
Materia: Architettura degli elaboratori
tags:
  - aritmetica
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 5.2.1'
Imparato: false
Ordine: 501
aliases:
  - half adder
  - full adder
  - sommatore
---
I **circuiti aritmetici** sono i blocchi centrali dei calcolatori. Si parte dal sommatore a 1 bit.

## Half adder (semisommatore)
Due ingressi $A$, $B$; due uscite $S$ (*sum*) e $C_{out}$ (*carry out*).

$$S = A \oplus B \qquad C_{out} = AB$$

| $A$ | $B$ | $C_{out}$ | $S$ |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 0 |

$S$ è il bit di somma, $C_{out}$ il [[Addizione binaria e overflow|riporto]] verso la colonna successiva.

> [!warning] Il limite dell'half adder
> **Manca l'ingresso $C_{in}$**: non può accettare il riporto proveniente dalla colonna precedente, quindi non si può usare per costruire sommatori a più bit (tranne per la colonna meno significativa).

## Full adder (sommatore completo)
Aggiunge l'ingresso di riporto $C_{in}$: tre ingressi $A$, $B$, $C_{in}$; due uscite $S$, $C_{out}$.

$$S = A \oplus B \oplus C_{in}$$
$$C_{out} = AB + A C_{in} + B C_{in}$$

| $C_{in}$ | $A$ | $B$ | $C_{out}$ | $S$ |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 1 |
| 0 | 1 | 0 | 0 | 1 |
| 0 | 1 | 1 | 1 | 0 |
| 1 | 0 | 0 | 0 | 1 |
| 1 | 0 | 1 | 1 | 0 |
| 1 | 1 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 | 1 |

Letture utili:
- $S$ è la **parità** dei tre ingressi (1 se il numero di 1 è dispari);
- $C_{out}$ è la **maggioranza** dei tre ingressi (1 se almeno due sono 1).

## Da ricordare
- $S = A \oplus B \oplus C_{in}$ (parità), $C_{out} = AB + AC_{in} + BC_{in}$ (maggioranza).
- Half adder = senza $C_{in}$; full adder = con $C_{in}$.
