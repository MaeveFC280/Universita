---
tags: [architettura, combinatoria, blocchi, cap2]
capitolo: 2
sezione: "2.8.2"
pagine_pdf: 102-104
---

# Decoder

## Funzione
Un **decoder** ha $N$ ingressi e $2^N$ uscite. Attiva **esattamente una** uscita, quella
il cui indice corrisponde al valore binario presente sugli ingressi.

Esempio, decoder 2:4 con ingressi $A_{1:0}$:
| $A_1 A_0$ | $Y_3 Y_2 Y_1 Y_0$ |
|---|---|
| 00 | 0001 |
| 01 | 0010 |
| 10 | 0100 |
| 11 | 1000 |

## Codifica one-hot
Le uscite si dicono **one-hot** perché esattamente una è HIGH ("calda") in ogni
istante. → [[Codifica degli stati - binaria e one-hot]]

## Decoder + OR = logica combinatoria
Ogni uscita di un decoder corrisponde a un **mintermine**. Quindi:

> Qualunque funzione booleana si realizza con un decoder seguito da porte OR che
> raccolgono i mintermini in cui la funzione vale 1.

Per questo, quando si costruisce logica con i decoder, conviene esprimere la funzione
in forma **somma di mintermini** (SOP canonica).

Esempio: $Y = \overline{A}B + A\overline{B}$ (XOR) = OR delle uscite $Y_1$ e $Y_2$ di un decoder 2:4.

## Usi tipici
- **Selezione di riga** nelle memorie: l'indirizzo entra nel decoder, l'uscita attiva
  la *wordline* corrispondente (→ [[Array di memoria - organizzazione]]).
- Decodifica delle istruzioni nell'unità di controllo.
- Abilitazione di uno tra molti dispositivi.

## Da ricordare
- $N$ ingressi → $2^N$ uscite one-hot.
- Ogni uscita = un mintermine.
- Decoder + OR realizza qualunque funzione, in forma SOP canonica.

## Domande flash
1. Quante uscite ha un decoder 4:16?
2. Realizza un NAND a 2 ingressi con un decoder 2:4 e una porta OR.
