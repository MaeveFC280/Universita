---
Materia: Architettura degli elaboratori
tags:
  - ARM
  - assembly
  - funzioni
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 6.3.7'
Imparato: true
Ordine: 612
aliases:
  - funzioni
  - calling convention
  - BL
  - LR
---
I linguaggi di alto livello supportano le **funzioni** (o procedure) per riusare codice frequentemente usato e per rendere il programma leggibile e modulare.

Terminologia:
- il **caller** (chiamante) invoca la funzione, e le passa gli **argomenti**;
- il **callee** (chiamata) esegue il lavoro e restituisce un **valore di ritorno**.

> [!important] Il contratto tra caller e callee
> 1. Una funzione deve **calcolare il valore di ritorno** e **non produrre altri effetti collaterali indesiderati**.
> 2. **Il callee non deve interferire con il comportamento del caller**: deve cioè restituire il controllo al punto giusto e **non alterare** i registri e la memoria su cui il caller conta.

## Convenzioni ARM (AAPCS)
| Elemento | Registro |
|---|---|
| **argomenti** (fino a 4) | R0, R1, R2, R3 |
| **valore di ritorno** | **R0** |
| indirizzo di ritorno | **LR** (R14) |
| puntatore allo stack | **SP** (R13) |

- Il **caller** mette gli **argomenti** in **R0–R3** prima di chiamare.
- Il **callee** mette il **valore di ritorno** in **R0** prima di terminare.
- Per convenzione ARM, una funzione **`void`** non restituisce nulla e non usa R0 come ritorno.
- Quando una funzione ha **più di quattro argomenti**, gli argomenti in eccesso si
  passano sullo [[Lo stack|stack]].

## Istruzioni essenziali
**`BL`** (*branch and link*) e **`MOV PC, LR`** sono le due istruzioni necessarie per chiamare una funzione e tornare al chiamante.

### Chiamata
[[Branch ed esecuzione condizionale|BL etichetta]] esegue due cose:
1. salva nel **link register (LR)** l'indirizzo dell'istruzione successiva alla chiamata (**l'indirizzo di ritorno**);
2. salta all'istruzione di destinazione.

### Ritorno

```armasm
MOV PC, LR      ; copia l'indirizzo di ritorno nel PC
```
Un metodo alternativo nelle versioni moderne e usare `BX LR`
```armasm
BX LR
```

*Esempio:*
```armasm
    MOV  R0, #5           ; RO=5
    MOV  R1, #7           ; R1=7
    BL   somma            ; chiamata funzione e mette l'indirizzo del ritorno in LR
    ; ora R0 contiene il risultato di somma

somma
    ADD  R0, R0, R1       ; calcola
    MOV  PC, LR           ; ritorna copiando il valore LR in PC
```

## Funzioni annidate
Se la funzione chiamata **chiama a sua volta** un'altra funzione, la seconda `BL` **sovrascrive LR**, distruggendo l'indirizzo di ritorno della prima. Analogamente, se il callee usa i registri R4–R11, distrugge i valori del caller.
**La soluzione è lo** **[[Lo stack|stack]]**.

## Riepilogo dei registri preservati
| [[Registri ARM\|Preserved]] (**callee-saved**) | [[Registri ARM\|Nonpreserved]] (**caller-saved**) |
| ---------------------------------------------- | ------------------------------------------------- |
| R4–R11                                         | R0–R3                                             |
| R13 (SP)                                       | R12 (IP)                                          |
| R14 (LR)                                       | CPSR (flag)                                       |
| la memoria sopra lo stack pointer              | la memoria sotto lo stack pointer                 |

Interpretazione operativa:
- Se sei il **callee** e vuoi usare R4–R11, **devi salvarli e ripristinarli**.
- Se sei il **caller** e ti serve un valore in R0–R3 dopo la chiamata, **salvalo prima tu**

