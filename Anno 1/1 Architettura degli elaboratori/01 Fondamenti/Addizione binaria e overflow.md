---
Materia: Architettura degli elaboratori
tags:
  - Binario
  - aritmetica
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 1.4.6'
Imparato: true
Ordine: 105
aliases:
  - somma binaria
  - riporto
  - overflow
---
## Meccanica
L'addizione binaria funziona come quella decimale: si sommano le colonne da destra a sinistra propagando il **riporto** (*carry*) quando la somma di colonna supera il valore massimo della base.

| Colonna | Risultato | Riporto |
|---|---|---|
| $0 + 0$ | 0 | 0 |
| $0 + 1$ | 1 | 0 |
| $1 + 1$ | 0 | **1** |
| $1 + 1 + 1$ | 1 | **1** |

![[Sistemi di numerazione-1785676210811.webp]]

> [!info] Perché serve
> È esattamente questa meccanica che viene realizzata in hardware dai [[Half adder e full adder|sommatori]], collegati in cascata nel [[Ripple carry adder|ripple carry adder]].

## Overflow
I sistemi digitali operano su un **numero fisso di cifre**. Si dice che l'addizione va in **overflow** se il risultato è troppo grande per stare nelle cifre disponibili.

*Esempio su 4 bit: $1101_2 + 0101_2 = 10010_2$ richiede 5 bit → overflow (il risultato troncato a 4 bit, $0010$, è sbagliato).

> [!tip] Come si gestisce
> Si può estendere il numero di bit disponibili (es. sommare due numeri a 4 bit su un risultato a 5 bit), oppure segnalare la condizione con un [[Flag di condizione e istruzione CMP|flag]].

## Da ricordare
- Overflow = il risultato non entra nel formato fisso.
- Per numeri **senza segno**, overflow ⇔ carry out dal msb.
- Per il [[Segno, modulo e complemento a due|complemento a due]] la regola è diversa.
