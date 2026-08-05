---
Materia: Architettura degli elaboratori
tags:
  - ARM
  - assembly
  - flusso_di_controllo
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 6.3.2-6.3.3'
Imparato: false
Ordine: 607
aliases:
  - branch
  - esecuzione condizionale
  - salto
---

# Branch ed esecuzione condizionale

## Due modi di prendere decisioni
ARM offre due meccanismi distinti:
1. l'**esecuzione condizionale** di singole istruzioni;
2. i **branch** (salti), che modificano il flusso del programma.

## 1. Esecuzione condizionale
Un modo per prendere decisioni è **ignorare** certe istruzioni: **quasi tutte** le
istruzioni ARM possono portare un **suffisso di condizione** che ne determina
l'esecuzione in base ai flag.

```
CMP    R1, R2
ADDEQ  R3, R4, R5      ; eseguita SOLO se R1 == R2
SUBNE  R3, R4, R5      ; eseguita SOLO se R1 != R2
MOVGT  R0, #1          ; eseguita SOLO se R1 > R2 (con segno)
```

Se la condizione è falsa, l'istruzione **si comporta come una NOP**: non ha alcun
effetto.

> [!tip] Perché è utile
> Per blocchi `if` **molto corti** l'esecuzione condizionale è **più veloce** di un
> branch, perché evita di svuotare la pipeline. È una caratteristica distintiva di ARM
> (poche altre architetture la offrono in modo così generale).

## 2. Istruzioni di branch
Le istruzioni di **branch** modificano il **program counter**. In altre architetture si
chiamano anche *jump* (salti). ARM ha due tipi di branch:

| Istruzione | Nome | Effetto |
|---|---|---|
| `B etichetta` | *branch* | salta all'etichetta |
| `BL etichetta` | *branch and link* | salta **e salva** l'indirizzo di ritorno in **LR** (per le chiamate a funzione → [[Funzioni e convenzioni di chiamata]]) |

## Etichette (labels)
Un'**etichetta** indica la posizione di un'istruzione nel programma.

> [!warning] Regola sintattica
> **Le etichette non devono essere indentate**, mentre **le istruzioni devono essere
> precedute da spazi bianchi**. È così che l'assemblatore le distingue.

```
        MOV  R0, #0
loop
        ADD  R0, R0, #1
        CMP  R0, #10
        BNE  loop        ; salta a 'loop' finché R0 != 10
        B    fine
fine
```

## Branch condizionati
I branch possono eseguirsi condizionalmente usando gli stessi **mnemonici di
condizione** delle altre istruzioni:

```
BEQ etichetta     ; salta se uguale       (Z=1)
BNE etichetta     ; salta se diverso      (Z=0)
BLT etichetta     ; salta se minore       (con segno)
BGE etichetta     ; salta se maggiore o uguale
BLO etichetta     ; salta se minore       (senza segno)
```

## Come si calcola l'indirizzo di destinazione
L'istruzione di branch contiene un **immediato a 24 bit** che è l'offset **in parole**
rispetto al PC. L'indirizzo effettivo è:

$$BTA = (PC + 8) + 4 \times imm24_{\text{esteso con segno}}$$

dove il termine **+8** viene dalla regola "leggere il PC dà PC+8"
(→ [[Registri ARM]]). L'assemblatore calcola l'offset automaticamente a partire
dall'etichetta.

Il range di salto è quindi di circa $\pm 32$ MB, sufficiente per la quasi totalità dei
casi.

## Da ricordare
- Quasi **ogni** istruzione ARM può essere condizionale (suffisso di condizione).
- `B` salta, `BL` salta e salva il ritorno in **LR**.
- Etichette **non indentate**, istruzioni **indentate**.
- $BTA = (PC+8) + 4 \times imm24$.

## Domande flash
1. Quando conviene l'esecuzione condizionale invece di un branch?
2. Che differenza c'è tra `B` e `BL`?
3. Perché nel calcolo del target compare il +8?
