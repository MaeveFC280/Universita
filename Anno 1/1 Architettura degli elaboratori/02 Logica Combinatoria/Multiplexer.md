---
Materia: Architettura degli elaboratori
tags:
  - logica_combinatoria
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 2.8.1'
Imparato: true
Ordine: 209
aliases:
  - mux
  - lookup table
---
Un **multiplexer** (mux) sceglie una tra più uscite possibili in base a un segnale di **selezione**. È uno dei blocchi combinatori più usati.
![[Multiplexer-1786796041455.webp]]

## Mux 2:1
Due ingressi dati $I_0, I_1$, un ingresso di selezione $S$, un'uscita $Y$:
$$Y = \overline{S}I_0 + S I_1$$
- $S = 0 \Rightarrow Y = I_0$
- $S = 1 \Rightarrow Y = I_1$
![[Multiplexer-1786796112833.webp]]
Realizzazioni possibili: [[Da equazioni a schemi - logica a due livelli|logica multilivello]] ([[Forme canoniche SOP e POS|SOP]]), oppure con **buffer three-state** (uno abilitato da $S$, l'altro da $\overline{S}$: mai contemporaneamente attivi).
![[Multiplexer-1786796073484.webp|228]]
## Mux più grandi
Un mux **N:1** ha $N$ ingressi dati e richiede $\log_2 N$ linee di selezione.
- mux 4:1 → 2 linee di selezione
- mux 8:1 → 3 linee di selezione

Si costruisce sia in [[Da equazioni a schemi - logica a due livelli|logica multilivello]], sia come **albero** di mux 2:1 (gerarchia e [[Astrazione e gestione della complessita|modularità]]: soluzione più regolare e più economica).

## Mux come tabella di consultazione (*lookup table*)
Un mux con $2^N$ ingressi può realizzare **qualunque** funzione logica di $N$ variabili:
1. collega le $N$ variabili alle linee di selezione;
2. collega ogni ingresso dati a **0 o 1** secondo la riga corrispondente della [[Porte logiche|tabella di verità]].

Questa è l'idea che sta dietro alle [[Register file ROM e logic array|LUT delle FPGA]]

### Trucco per dimezzare le dimensioni
Con un po' di astuzia si può implementare una funzione di $N$ variabili con un mux a $2^{N-1}$ ingressi: si usano $N-1$ variabili come selezione e si collegano gli ingressi dati alla $N$-esima variabile, al suo complemento, a 0 o a 1.
