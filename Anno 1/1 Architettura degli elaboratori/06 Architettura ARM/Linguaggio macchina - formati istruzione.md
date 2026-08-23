---
Materia: Architettura degli elaboratori
tags:
  - ARM
  - Binario
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 6.4'
Imparato: false
Ordine: 614
aliases:
  - linguaggio macchina
  - machine language
  - formato istruzione
  - encoding
---
## Il passaggio dall'assembly al binario
L'assembly è comodo per gli esseri umani, ma i circuiti digitali comprendono solo
**1 e 0**. Il programma è quindi codificato come una sequenza di numeri binari: il
**linguaggio macchina**.

Applicando il principio "**la regolarità favorisce la semplicità**", la scelta più
regolare è **codificare tutte le istruzioni con la stessa lunghezza**: in ARM ogni
istruzione è di **32 bit** esatti.

Ma la regolarità pura sarebbe troppo rigida per accogliere ogni tipo di istruzione:
qui entra in gioco il quarto principio, **un buon progetto richiede buoni compromessi**.
ARM definisce quindi **tre formati principali** di istruzione.

## I tre formati

### 1. Data-processing (elaborazione dati)
Il formato **più comune**. Ha tre operandi: due sorgenti e una destinazione.

| Campo | Bit | Contenuto |
|---|---|---|
| `cond` | 31:28 | condizione di esecuzione |
| `op` | 27:26 | **00** (identifica il tipo di formato) |
| `funct` | 25:20 | `I` (1 bit), `cmd` (4 bit), `S` (1 bit) |
| `Rn` | 19:16 | primo registro sorgente |
| `Rd` | 15:12 | registro di destinazione |
| `Src2` | 11:0 | secondo operando |

Gli operandi sono codificati nei tre campi `Rn`, `Rd` e `Src2`:
- **`Rn`** è la **prima sorgente**, sempre un registro;
- **`Rd`** è la **destinazione**;
- **`Src2`** è la **seconda sorgente**: un registro **oppure** un immediato.

Il campo `funct` ha tre sottocampi:
- **`I`** (*immediate*): vale **1 quando `Src2` è un immediato**, 0 quando è un registro;
- **`cmd`** (4 bit): specifica **quale** operazione (ADD, SUB, AND, ORR, MOV, CMP…);
- **`S`** (*set flags*): vale **1 se l'istruzione aggiorna i flag** di condizione
  (suffisso `S`, oppure istruzioni come `CMP` che li aggiornano sempre).

#### Le due forme di Src2
- **`I = 1` (immediato)**: `Src2` = `rot` (4 bit) + `imm8` (8 bit); il valore effettivo è
  `imm8` ruotato a destra di $2 \times rot$.
- **`I = 0` (registro)**: `Src2` = `shamt5` + `sh` + `Rm`, dove `Rm` è il registro
  sorgente e i campi di shift permettono lo **shift gratuito** del secondo operando
  (→ [[Istruzioni logiche e di shift]]).

### 2. Memory (istruzioni di memoria)
Le istruzioni di memoria usano un formato **simile** a quello data-processing e hanno
**tre operandi**: un **registro base**, un **offset** (immediato o registro), e un
registro **sorgente o destinazione** del dato.

| Campo | Bit | Contenuto |
|---|---|---|
| `cond` | 31:28 | condizione |
| `op` | 27:26 | **01** |
| `funct` | 25:20 | 6 bit di controllo: `I, P, U, B, W, L` |
| `Rn` | 19:16 | registro **base** |
| `Rd` | 15:12 | registro dato (destinazione per LDR, sorgente per STR) |
| `Src2` | 11:0 | offset |

I sei bit di controllo:
| Bit | Nome | Significato |
|---|---|---|
| **I** | *immediate* | 1 = offset immediato, 0 = offset in registro |
| **P** | *pre-index* | 1 = pre-indexed / offset, 0 = post-indexed |
| **U** | *up* | 1 = offset **sommato**, 0 = offset **sottratto** |
| **B** | *byte* | 1 = accesso a **byte** (LDRB/STRB), 0 = word |
| **W** | *writeback* | 1 = **aggiorna** il registro base |
| **L** | *load* | **1 = LDR** (load), **0 = STR** (store) |

> [!tip] Come ricordare P e W
> - offset addressing: P=1, W=0 (usa base+off, non aggiorna)
> - pre-indexed: P=1, W=1 (usa base+off, aggiorna)
> - post-indexed: P=0, W=1 (usa base, aggiorna)

### 3. Branch
| Campo | Bit | Contenuto |
|---|---|---|
| `cond` | 31:28 | condizione |
| `op` | 27:26 | **10** |
| `funct` | 25:24 | `1L` — **L=1 per BL**, L=0 per B |
| `imm24` | 23:0 | offset in **parole**, con segno |

L'indirizzo di destinazione è
$$BTA = (PC + 8) + 4 \times imm24_{\text{sign-extended}}$$

## Il campo cond: condizionalità universale
> [!important] Perché `cond` sta in tutti i formati
> **Ogni** istruzione ARM contiene i 4 bit di condizione nei bit 31:28. È per questo che
> **qualunque** istruzione può essere resa condizionale
> (→ [[Branch ed esecuzione condizionale]]). Il valore `1110` (AL, *always*) significa
> esecuzione incondizionata, ed è il default.

## Riepilogo dei codici op
| `op` | Formato |
|---|---|
| 00 | data-processing |
| 01 | memoria |
| 10 | branch |
| 11 | coprocessore / altre |

## Interpretare il codice macchina
Procedura per decodificare un'istruzione a 32 bit:
1. leggi `op` (bit 27:26) → identifica il **formato**;
2. leggi `cond` (31:28) → la condizione;
3. secondo il formato, leggi `funct` per l'operazione specifica;
4. leggi i campi registro e l'immediato.

## Da ricordare
- Tutte le istruzioni sono di **32 bit**.
- Tre formati: **data-processing (op=00)**, **memoria (op=01)**, **branch (op=10)**.
- `cond` nei bit **31:28** di **tutte** le istruzioni.
- Data-processing: `I` = immediato, `cmd` = operazione, `S` = aggiorna i flag.
- Memoria: `I,P,U,B,W,L`; **L=1 per LDR**, L=0 per STR.

## Domande flash
1. Quali bit identificano il formato dell'istruzione?
2. Cosa significa `B=1` in un'istruzione di memoria?
3. In che formato è codificata `ADDS R0, R1, #4`, e quali bit di `funct` valgono 1?

Collegato a: [[Processore single-cycle - unita di controllo]]
