---
Materia: Architettura degli elaboratori
tags:
  - logica_combinatoria
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 2.8.1'
Imparato: false
Ordine: 209
aliases:
  - mux
  - lookup table
---

# Multiplexer

## Funzione
Un **multiplexer** (mux) sceglie una tra più uscite possibili in base a un segnale di
**selezione**. È uno dei blocchi combinatori più usati.

## Mux 2:1
Due ingressi dati $D_0, D_1$, un ingresso di selezione $S$, un'uscita $Y$:
$$Y = \overline{S}D_0 + S D_1$$
- $S = 0 \Rightarrow Y = D_0$
- $S = 1 \Rightarrow Y = D_1$

Realizzazioni possibili: logica a due livelli (SOP), oppure con **buffer three-state**
(uno abilitato da $S$, l'altro da $\overline{S}$: mai contemporaneamente attivi).

## Mux più grandi
Un mux **N:1** ha $N$ ingressi dati e richiede $\log_2 N$ linee di selezione.
- mux 4:1 → 2 linee di selezione
- mux 8:1 → 3 linee di selezione

Si costruisce sia in logica a due livelli, sia come **albero** di mux 2:1 (gerarchia e
modularità: soluzione più regolare e più economica).

## Mux come tabella di consultazione (*lookup table*)
Un mux con $2^N$ ingressi può realizzare **qualunque** funzione logica di $N$ variabili:
1. collega le $N$ variabili alle linee di selezione;
2. collega ogni ingresso dati a **0 o 1** secondo la riga corrispondente della tabella
   di verità.

Questa è l'idea che sta dietro alle **LUT** delle FPGA (→ [[Register file ROM e logic array]]).

### Trucco per dimezzare le dimensioni
Con un po' di astuzia si può implementare una funzione di $N$ variabili con un mux a
$2^{N-1}$ ingressi: si usano $N-1$ variabili come selezione e si collegano gli ingressi
dati alla $N$-esima variabile, al suo complemento, a 0 o a 1.

## Da ricordare
- Mux N:1 ⇒ $\log_2 N$ segnali di selezione.
- Mux a $2^N$ ingressi = LUT per qualunque funzione di $N$ variabili.
- Nei processori il mux è **onnipresente**: seleziona quale valore entra nell'ALU,
  cosa si scrive nei registri, da dove viene il prossimo PC.

## Domande flash
1. Quante linee di selezione ha un mux 16:1?
2. Implementa $Y = AB + \overline{A}\,\overline{B}$ con un solo mux 4:1.

Collegato a: [[Decoder]] · [[Processore single-cycle - datapath]]
