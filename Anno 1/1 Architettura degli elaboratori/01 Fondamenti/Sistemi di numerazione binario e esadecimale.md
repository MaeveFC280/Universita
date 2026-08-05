---
tags: [architettura, fondamenti, numerazione, cap1]
capitolo: 1
sezione: "1.4"
pagine_pdf: 26-30
---

# Sistemi di numerazione: binario ed esadecimale

## Notazione posizionale e base
In un sistema posizionale ogni cifra è moltiplicata per il **peso** della propria
colonna. La base si indica con un pedice per evitare ambiguità: $1101_2$, $27_{10}$, $1B_{16}$.

- **Decimale (base 10)**: pesi $10^0, 10^1, 10^2, \dots$
  Un numero decimale a $N$ cifre rappresenta uno di $10^N$ valori: da $0$ a $10^N - 1$.
  Questo intervallo si chiama **range**.
- **Binario (base 2)**: ogni colonna ha peso doppio della precedente ($1, 2, 4, 8, 16, \dots$).
  Un numero binario a $N$ bit rappresenta uno di $2^N$ valori: da $0$ a $2^N - 1$.
- **Esadecimale (base 16)**: cifre `0-9` più `A-F` (A=10 … F=15).

## Perché l'esadecimale
Un gruppo di 4 bit rappresenta uno di $2^4 = 16$ valori: quindi **una cifra
esadecimale corrisponde esattamente a 4 bit**. Scrivere numeri binari lunghi è
scomodo e soggetto a errori; in esadecimale la scrittura è 4 volte più compatta e la
conversione è meccanica.

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
$10110_2 = 16 + 4 + 2 = 22_{10}$

### Decimale → binario (metodo dei resti)
Si divide ripetutamente per 2 partendo da destra; **il resto va nella colonna**.
Esempio: $84_{10}$
```
84 / 2 = 42  resto 0   -> bit 0 (lsb)
42 / 2 = 21  resto 0
21 / 2 = 10  resto 1
10 / 2 =  5  resto 0
 5 / 2 =  2  resto 1
 2 / 2 =  1  resto 0
 1 / 2 =  0  resto 1   -> msb
```
Leggendo dall'ultimo al primo: $1010100_2$.

### Metodo alternativo (per sottrazione dei pesi)
Si parte dalla potenza di 2 più grande contenuta nel numero e si sottrae.
$84 = 64 + 16 + 4 \Rightarrow 1010100_2$.

### Esadecimale ↔ binario
Sostituzione diretta di ogni cifra con i suoi 4 bit (e viceversa, raggruppando a 4
**partendo da destra**).
$2ED_{16} = 0010\ 1110\ 1101_2$

### Esadecimale → decimale
$2ED_{16} = 2 \cdot 256 + 14 \cdot 16 + 13 = 749_{10}$

## Da ricordare
- $N$ bit → $2^N$ combinazioni, range $[0, 2^N-1]$.
- 1 cifra hex = 4 bit, sempre.
- Decimale→binario: divisioni successive per 2, i resti sono i bit da lsb a msb.

## Domande flash
1. Quanti bit servono per rappresentare 1000 valori distinti?
2. Converti $C3_{16}$ in decimale e in binario.

Collegato a: [[Byte nibble word e prefissi binari]] · [[Addizione binaria e overflow]]
