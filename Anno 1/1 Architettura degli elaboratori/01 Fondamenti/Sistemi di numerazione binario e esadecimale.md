---
Materia: Architettura degli elaboratori
tags:
  - Binario
Link risorse: https://youtu.be/QZwneRb-zqA?si=cP0ZyNW7ELlDQNCI&t=306
Libro: '"Digital Design and Computer Architecture" Capitolo 1.4'
Imparato: true
Ordine: 103
aliases:
  - Sistemi di numerazione
  - numerazione binaria
  - sistema binario
  - esadecimale
  - hex
  - conversione di base
---
## Notazione posizionale e base
In un sistema posizionale ogni cifra è moltiplicata per il **peso** della propria colonna. La base si indica con un pedice per evitare ambiguità: $1101_2$, $27_{10}$, $1B_{16}$.

- **Decimale (base 10)**: pesi $10^0, 10^1, 10^2, \dots$
  Un numero decimale a $N$ cifre rappresenta uno di $10^N$ valori: da $0$ a $10^N - 1$.
  Questo intervallo si chiama **range**.
- **Binario (base 2)**: ogni colonna ha peso doppio della precedente ($1, 2, 4, 8, 16, \dots$).
  Un numero binario a $N$ bit rappresenta uno di $2^N$ valori: da $0$ a $2^N - 1$.
- **Esadecimale (base 16)**: cifre `0-9` più `A-F` (A=10 … F=15).

## Bit più e meno significativo
In un numero binario si distinguono:
- il **bit più significativo** (*most significant bit*, **msb**): quello più a sinistra, con il peso maggiore;
- il **bit meno significativo** (*least significant bit*, **lsb**): quello più a destra, con peso $2^0 = 1$.

![[Sistemi di numerazione-1785675970006.webp|700]]

## Perché l'esadecimale
Un gruppo di 4 bit rappresenta uno di $2^4 = 16$ valori: quindi **una cifra esadecimale corrisponde esattamente a 4 bit**. Scrivere numeri binari lunghi è scomodo e soggetto a errori; in esadecimale la scrittura è 4 volte più compatta e la conversione è meccanica.

| Hex | Bin | Dec |
|---|---|---|
| 0 | 0000 | 0 |
| 1 | 0001 | 1 |
| 2 | 0010 | 2 |
| 3 | 0011 | 3 |
| 4 | 0100 | 4 |
| 5 | 0101 | 5 |
| 6 | 0110 | 6 |
| 7 | 0111 | 7 |
| 8 | 1000 | 8 |
| 9 | 1001 | 9 |
| A | 1010 | 10 |
| B | 1011 | 11 |
| C | 1100 | 12 |
| D | 1101 | 13 |
| E | 1110 | 14 |
| F | 1111 | 15 |

## Conversioni
### Binario → decimale
Somma dei pesi delle colonne con bit a 1.
*Esempio:* $10110_2 = 16 + 4 + 2 = 22_{10}$

### Decimale → binario
#### Metodo dei resti
Si divide ripetutamente per 2 partendo da destra; **il resto va nella colonna**.

*Esempio: $84_{10}$*
```
84 / 2 = 42  resto 0   -> bit 0 (lsb)
42 / 2 = 21  resto 0
21 / 2 = 10  resto 1
10 / 2 =  5  resto 0
 5 / 2 =  2  resto 1
 2 / 2 =  1  resto 0
 1 / 2 =  0  resto 1   -> msb
```
 *Leggendo dall'ultimo al primo: $1010100_2$.*
#### Metodo per sottrazione dei pesi
Si parte dalla potenza di 2 più grande contenuta nel numero e si sottrae.
*Esempio: * $84 = 64 + 16 + 4 \Rightarrow 1010100_2$.

### Esadecimale ↔ binario
Sostituzione diretta di ogni cifra con i suoi 4 bit (e viceversa, raggruppando a 4
**partendo da destra**).
*Esempio:* $2ED_{16} = 0010\ 1110\ 1101_2$

### Esadecimale → decimale
*Esempio:* $2ED_{16} = 2 \cdot 256 + 14 \cdot 16 + 13 = 749_{10}$

## Operazioni

| Argomento | Nota |
|---|---|
| somme | [[Addizione binaria e overflow]] |
| numeri negativi, sottrazioni | [[Segno, modulo e complemento a due]] |
| prodotti, divisioni per potenze di 2 | [[Shifter e rotatori]] |
| virgola | [[Notazione a virgola fissa]] · [[Virgola mobile IEEE 754]] |
| byte, word, prefissi K/M/G | [[Byte nibble word e prefissi binari]] |
