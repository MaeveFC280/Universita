---
Materia: Architettura degli elaboratori
tags:
  - ARM
  - assembly
  - memoria
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 6.2.3'
Imparato: true
Ordine: 604
aliases:
  - LDR
  - STR
  - load store
---
## LDR — Load Register
Legge una parola dalla memoria e la porta in un registro.

```
LDR R1, [R5, #4]     ; R1 = Mem[R5 + 4]
```

L'indirizzo è specificato con:
- un **registro base** (qui `R5`), che contiene l'indirizzo di partenza;
- un **offset** (qui `#4`), che si somma al base.

Nel calcolo dell'indirizzo l'offset è espresso in **byte**: `#4` significa "una parola più avanti".

## STR — Store Register
Scrive il contenuto di un registro in memoria.

```
STR R9, [R5, #8]     ; Mem[R5 + 8] = R9
```

> [!warning] Attenzione all'ordine degli operandi
> In `STR Rd, [Rn, #off]` il registro `Rd` è la **sorgente** (il dato da scrivere), non la destinazione. È l'unica famiglia di istruzioni ARM in cui il primo operando non è la destinazione.

## Le tre modalità di indirizzamento
Oltre allo scalamento dell'indice, ARM offre tre modalità:

| Modalità | Sintassi | Indirizzo usato | Aggiorna il base? |
|---|---|---|---|
| **offset** | `LDR R1,[R2,#4]` | $R2 + 4$ | **no** |
| **pre-indexed** | `LDR R1,[R2,#4]!` | $R2 + 4$ | **sì**, $R2 = R2+4$ **prima** |
| **post-indexed** | `LDR R1,[R2],#4` | $R2$ | **sì**, $R2 = R2+4$ **dopo** |

> [!tip] A cosa serve pre/post-indexed
> A **scorrere array** senza istruzioni aggiuntive: `LDR R1, [R2], #4` legge l'elemento corrente e avanza il puntatore in **una sola istruzione**.

L'offset può essere un **immediato** oppure un **registro** (opzionalmente [[Istruzioni logiche e di shift|shiftato]]).

## Varianti per byte e half-word
| Istruzione | Effetto |
|---|---|
| `LDRB` | carica un **byte** e riempie i bit restanti del registro con **zeri** |
| `LDRSB` | carica un byte e lo estende con il **segno** |
| `LDRH` / `LDRSH` | come sopra, per **half-word** (16 bit) |
| `STRB` | scrive il **byte meno significativo** del registro in memoria |
| `STRH` | scrive i 16 bit meno significativi |

*Esempio completo:*
```c
// C: a[2] = a[0] + a[1];  con base dell'array in R0
```
```
LDR  R1, [R0, #0]    ; R1 = a[0]
LDR  R2, [R0, #4]    ; R2 = a[1]
ADD  R3, R1, R2      ; R3 = a[0] + a[1]
STR  R3, [R0, #8]    ; a[2] = R3
```
