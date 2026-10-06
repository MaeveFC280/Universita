---
Materia: Architettura degli elaboratori
tags:
  - logica_combinatoria
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 2.8.2'
Imparato: true
Ordine: 210
aliases:
  - decodificatore
  - one-hot
---
Un **decoder** ha $N$ ingressi e $2^N$ uscite. Attiva **esattamente una** uscita, quella il cui indice corrisponde al valore binario presente sugli ingressi.

*Esempio: decoder 2:4 con ingressi $A_{1:0}$:*

| $A_1 A_0$ | $Y_3 Y_2 Y_1 Y_0$ |
| --------- | ----------------- |
| 00        | 0001              |
| 01        | 0010              |
| 10        | 0100              |
| 11        | 1000              |

![[Decoder-1786801160458.webp]]
## Codifica one-hot
Le uscite si dicono **[[Codifica degli stati - binaria e one-hot|one-hot]]** perché esattamente una è HIGH ("calda") in ogni istante.

## Decoder + OR = logica combinatoria
Ogni uscita di un decoder corrisponde a un **[[Terminologia booleana - letterali mintermini maxtermini|mintermine]]**. Quindi:

> Qualunque funzione booleana si realizza con un decoder seguito da porte OR che raccolgono i mintermini in cui la funzione vale 1.

Per questo, quando si costruisce logica con i decoder, conviene esprimere la funzione in forma **somma di mintermini** (SOP canonica).

*Esempio: $Y = \overline{A}B + A\overline{B}$ (XOR) = OR delle uscite $Y_1$ e $Y_2$ di un decoder 2:4.*

## Usi tipici
- **Selezione di riga** nelle memorie: [[Array di memoria - organizzazione|l'indirizzo entra nel decoder, l'uscita attiva la wordline corrispondente]].
- Decodifica delle istruzioni nell'[[Datapath e unita di controllo|unità di controllo]].
- Abilitazione di uno tra molti dispositivi.
