---
tags: [architettura, arm, assembly, memoria, cap6]
capitolo: 6
sezione: "6.2.3"
pagine_pdf: 317-319
---

# Istruzioni di memoria: LDR e STR

## LDR — Load Register
Legge una parola dalla memoria e la porta in un registro.

```
LDR R1, [R5, #4]     ; R1 = Mem[R5 + 4]
```

L'indirizzo è specificato con:
- un **registro base** (qui `R5`), che contiene l'indirizzo di partenza;
- un **offset** (qui `#4`), che si somma al base.

Nel calcolo dell'indirizzo l'offset è espresso in **byte**: `#4` significa "una parola
più avanti".

## STR — Store Register
Scrive il contenuto di un registro in memoria.

```
STR R9, [R5, #8]     ; Mem[R5 + 8] = R9
```

> [!warning] Attenzione all'ordine degli operandi
> In `STR Rd, [Rn, #off]` il registro `Rd` è la **sorgente** (il dato da scrivere), non
> la destinazione. È l'unica famiglia di istruzioni ARM in cui il primo operando non è
> la destinazione — errore classico d'esame.

## Le tre modalità di indirizzamento
Oltre allo scalamento dell'indice, ARM offre tre modalità:

| Modalità | Sintassi | Indirizzo usato | Aggiorna il base? |
|---|---|---|---|
| **offset** | `LDR R1,[R2,#4]` | $R2 + 4$ | **no** |
| **pre-indexed** | `LDR R1,[R2,#4]!` | $R2 + 4$ | **sì**, $R2 = R2+4$ **prima** |
| **post-indexed** | `LDR R1,[R2],#4` | $R2$ | **sì**, $R2 = R2+4$ **dopo** |

- **Offset addressing**: calcola l'indirizzo come registro base **±** offset. Il base
  non cambia.
- **Pre-indexed**: aggiorna il base **e** usa il nuovo valore come indirizzo.
- **Post-indexed**: usa il base **così com'è** come indirizzo, poi lo aggiorna.

> [!tip] A cosa serve pre/post-indexed
> A **scorrere array** senza istruzioni aggiuntive: `LDR R1, [R2], #4` legge l'elemento
> corrente e avanza il puntatore in **una sola istruzione**.

L'offset può essere un **immediato** oppure un **registro** (opzionalmente shiftato).

## Varianti per byte e half-word
| Istruzione | Effetto |
|---|---|
| `LDRB` | carica un **byte** e riempie i bit restanti del registro con **zeri** |
| `LDRSB` | carica un byte e lo estende con il **segno** |
| `LDRH` / `LDRSH` | come sopra, per **half-word** (16 bit) |
| `STRB` | scrive il **byte meno significativo** del registro in memoria |
| `STRH` | scrive i 16 bit meno significativi |

→ [[Byte caratteri ASCII e stringhe]]

## Esempio completo
```c
// C: a[2] = a[0] + a[1];  con base dell'array in R0
```
```
LDR  R1, [R0, #0]    ; R1 = a[0]
LDR  R2, [R0, #4]    ; R2 = a[1]
ADD  R3, R1, R2      ; R3 = a[0] + a[1]
STR  R3, [R0, #8]    ; a[2] = R3
```

## Da ricordare
- `LDR Rd, [Rn, #off]` → legge; `STR Rs, [Rn, #off]` → scrive (Rs è **sorgente**).
- Offset in **byte**: per l'elemento $i$ di un array di word l'offset è $4i$.
- Tre modalità: offset, pre-indexed (`!`), post-indexed (offset fuori parentesi).
- `LDRB` estende con zeri, `LDRSB` con il segno.

## Domande flash
1. Che differenza c'è tra `LDR R1,[R2,#4]!` e `LDR R1,[R2],#4`?
2. Scrivi il codice per `x = a[3];` con base in R5 e `x` in R1.
