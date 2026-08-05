---
Materia: Architettura degli elaboratori
tags:
  - Binario
  - aritmetica
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 1.4.6'
Imparato: false
Ordine: 105
aliases:
  - somma binaria
  - riporto
  - overflow
---

# Addizione binaria e overflow

## Meccanica
L'addizione binaria funziona come quella decimale: si sommano le colonne da destra a
sinistra propagando il **riporto** (*carry*) quando la somma di colonna supera il
valore massimo della base.

Le quattro regole di colonna, da sapere a memoria:

| Colonna | Risultato | Riporto |
|---|---|---|
| $0 + 0$ | 0 | 0 |
| $0 + 1$ | 1 | 0 |
| $1 + 1$ | 0 | **1** |
| $1 + 1 + 1$ | 1 | **1** |

Cioè: $1+1 = 10_2$ e $1+1+1 = 11_2$.

```
   1 1 1     <- carry
   0 1 1 1   (7)
 + 0 1 0 1   (5)
 ---------
   1 1 0 0   (12)
```

Lo stesso conto in decimale e in binario, per convincersi che è la stessa operazione
($35 + 7 = 42$, cioè $100011_2 + 000111_2 = 101010_2$):

![[Sistemi di numerazione-1785676210811.webp]]

> [!warning] Errore da non ripetere
> La vecchia nota riportava «$1+0=0$ e $0+0=0$». La prima è sbagliata: $1+0 = 1$.

> [!info] Perché serve
> È esattamente questa meccanica che viene realizzata in hardware dai sommatori
> (→ [[Half adder e full adder]], [[Ripple carry adder]]).

## Overflow
I sistemi digitali operano su un **numero fisso di cifre**. Si dice che l'addizione va
in **overflow** se il risultato è troppo grande per stare nelle cifre disponibili.

Esempio su 4 bit: $1101_2 + 0101_2 = 10010_2$ richiede 5 bit → overflow (il risultato
troncato a 4 bit, $0010$, è sbagliato).

> [!tip] Come si gestisce
> Si può estendere il numero di bit disponibili (es. sommare due numeri a 4 bit su un
> risultato a 5 bit), oppure segnalare la condizione con un flag
> (→ [[Flag di condizione e istruzione CMP]]).

## Da ricordare
- Overflow = il risultato non entra nel formato fisso.
- Per numeri **senza segno**, overflow ⇔ carry out dal msb.
- Per il complemento a due la regola è diversa
  (→ [[Numeri con segno - segno-modulo e complemento a due]]).

## Domande flash
1. $1111_2 + 0001_2$ su 4 bit: risultato e overflow?
2. Quanti bit serve al massimo il risultato della somma di due numeri a $N$ bit?
