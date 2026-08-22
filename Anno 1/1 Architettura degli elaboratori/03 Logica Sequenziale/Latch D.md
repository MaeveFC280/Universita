---
Materia: Architettura degli elaboratori
tags:
  - logica_sequenziale
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 3.2.3'
Imparato: true
Ordine: 303
aliases:
  - D latch
  - latch trasparente
---
## La separazione dei ruoli
Il **latch D** risolve i due problemi del [[Latch SR|latch SR]] separando **cosa** memorizzare da **quando** memorizzarlo. Ha due ingressi:
- **$D$** (*data*): controlla **quale** debba essere lo stato successivo;
- **$CLK$** (*clock*): controlla **quando** lo stato deve cambiare.
## Comportamento
| $CLK$ | $D$ | $Q$ | $\overline{Q}$ | Stato |
|---|---|---|---|---|
| 0 | X | $Q_{prev}$ | $\overline{Q_{prev}}$ | **opaco** |
| 1 | 0 | 0 | 1 | **trasparente** |
| 1 | 1 | 1 | 0 | **trasparente** |

- **$CLK = 1$**: il latch è **trasparente** (*transparent*). Il dato su $D$ fluisce attraverso l'uscita $Q$ come se il latch fosse un semplice buffer.
- **$CLK = 0$**: il latch è **opaco** (*opaque*). Blocca il nuovo dato e $Q$ mantiene il valore precedente. Si dice anche che il latch è **chiuso**.

In sintesi: **il clock controlla quando il dato scorre attraverso il latch**.

Il latch D è anche detto **latch trasparente** o **latch sensibile al livello** (*level-sensitive*), perché è il **livello** del clock (non il fronte) a determinare la trasparenza.
## Realizzazione
Un latch D si può costruire con:
- un [[Latch SR| latch SR]] preceduto da logica che genera $S$ e $R$ da $D$ e $CLK$ (evitando così
  la combinazione illegale);
- oppure, più economicamente, con un [[Multiplexer|mux 2:1]] retroazionato e un [[Porte logiche|inverter]]: quando
  $CLK=1$ il mux seleziona $D$, quando $CLK=0$ seleziona l'uscita corrente $Q$.
![[Latch D-1787400290396.webp|394x192]]![[Latch D-1787400336473.webp|215x192]]

## Il limite del latch
Finché il clock è alto, il latch è **trasparente**: se $D$ cambia più volte durante il livello alto, anche $Q$ cambia più volte. Questo rende difficile ragionare sul sistema, perché il dato può "scivolare" attraverso più stadi nello stesso ciclo di clock. Da qui il [[Flip-flop D e registri|flip-flop]].
