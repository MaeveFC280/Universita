---
Materia: Architettura degli elaboratori
tags:
  - virgola_mobile
  - Binario
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 5.3.2'
Imparato: false
Ordine: 507
aliases:
  - IEEE 754
  - floating point
  - mantissa
  - esponente
---
## Analogia
I numeri in **virgola mobile** sono analoghi alla **notazione scientifica**: come $4{,}1 \times 10^3$, hanno un segno, una **mantissa** ($M$), una **base** ($B$) e un **esponente** ($E$):

$$\pm M \times B^E$$

Nel formato IEEE 754 la base è **2** e la mantissa è **binaria**. Il vantaggio: si può coprire un range dinamico enormemente più ampio, a parità di bit.

## Formato a precisione singola (32 bit)
| Campo | Bit | Larghezza |
|---|---|---|
| **segno** | 31 | 1 bit |
| **esponente** | 30:23 | 8 bit |
| **frazione** | 22:0 | 23 bit |

## Le due convenzioni chiave

### 1. Il leading one implicito
In virgola mobile binaria, il **primo bit della mantissa** (quello a sinistra del punto binario) è **sempre 1** per un numero normalizzato. Essendo sempre 1, **non viene memorizzato**: si guadagna un bit di precisione gratis.

Quindi la mantissa vale $1.\text{frazione}$, e nei 23 bit si memorizza solo la parte **frazionaria**. La precisione effettiva è di 24 bit.

### 2. L'esponente polarizzato (biased)
L'esponente non è memorizzato in [[Segno, modulo e complemento a due|complemento a due]], ma con un **bias**:

$$E_{memorizzato} = E_{reale} + 127$$

Il bias per la precisione singola è **127** ($2^{8-1}-1$). Vantaggio: gli esponenti così codificati si possono confrontare come **interi senza segno**, il che semplifica enormemente il confronto tra numeri in virgola mobile.

## Valore rappresentato
$$V = (-1)^{S} \times 1.F \times 2^{(E - 127)}$$

### Esempio: convertire $228_{10}$
1. In binario: $11100100_2$
2. Normalizzato: $1{,}1100100 \times 2^7$
3. Segno: 0 (positivo)
4. Esponente memorizzato: $7 + 127 = 134 = 10000110_2$
5. Frazione (i 23 bit dopo il punto): $1100100\,0000\dots$
6. Risultato: `0 10000110 11001000000000000000000`

## Casi speciali
Lo standard IEEE riserva alcune combinazioni di esponente per valori che non esistono come numeri normali:

| Numero | Segno | Esponente | Frazione |
|---|---|---|---|
| **0** | x | 00000000 | 0 |
| **$\pm\infty$** | 0 / 1 | 11111111 | 0 |
| **NaN** | x | 11111111 | ≠ 0 |
| **denormalizzati** | x | 00000000 | ≠ 0 |

- $\pm\infty$: risultato di overflow o di divisione per zero.
- **NaN** (*Not a Number*): usato per **numeri che non esistono**, come $\sqrt{-1}$ o $\infty - \infty$.
- **Denormalizzati**: numeri molto piccoli, con leading one **implicitamente 0** anziché 1; riempiono il "buco" tra zero e il più piccolo numero normalizzato.

## Precisione doppia (64 bit)
| Campo | Larghezza | Bias |
|---|---|---|
| segno | 1 | — |
| esponente | 11 | **1023** |
| frazione | 52 | — |

## Arrotondamento
Le operazioni possono produrre risultati non rappresentabili. Lo standard prevede quattro modalità: verso zero, verso $+\infty$, verso $-\infty$, e **al più vicino** (*round to nearest even*, il default).

## Addizione in virgola mobile
**Non** è semplice come in complemento a due, perché gli esponenti vanno allineati. Procedura:
1. **Estrai** i bit di esponente e di frazione.
2. **Aggiungi il leading 1** per formare la mantissa completa.
3. **Confronta gli esponenti** e **shifta a destra** la mantissa più piccola per allineare i punti binari.
4. **Somma** le mantisse.
5. **Normalizza** il risultato (shifta la mantissa e aggiusta l'esponente).
6. **Arrotonda**.
7. **Riassembla** esponente e frazione nel formato finale.

> [!warning] Conseguenze pratiche
> L'addizione in virgola mobile **non è associativa**: $(a+b)+c \ne a+(b+c)$ in generale, per effetto degli arrotondamenti. È il motivo per cui i risultati numerici dipendono dall'ordine delle operazioni.

## Da ricordare
- Singola precisione: 1 + 8 + 23; bias **127**. Doppia: 1 + 11 + 52; bias **1023**.
- $V = (-1)^S \times 1.F \times 2^{E-127}$.
- Leading one **implicito** (non memorizzato) e esponente **polarizzato** (confronto come interi).
- Esponente tutto 1 → $\infty$ (frazione 0) o NaN (frazione ≠ 0).
- Addizione: allinea gli esponenti, somma, normalizza, arrotonda.
