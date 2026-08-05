---
tags: [architettura, microarchitettura, multiciclo, cap7]
capitolo: 7
sezione: "7.4.1"
pagine_pdf: 422-429
---

# Processore multiciclo: il datapath

## L'idea
Il processore **multiciclo** spezza ogni istruzione in **più passi**, ciascuno eseguito
in un ciclo di clock **breve**. Vantaggi:
- il tempo di ciclo è dettato dal passo più lento, non dall'istruzione più lunga;
- **l'hardware si riusa** in cicli diversi: **una sola memoria** e **un solo sommatore**
  (l'ALU) bastano;
- le istruzioni brevi impiegano **meno cicli**.

Il prezzo: servono **registri non architetturali** per conservare i risultati intermedi
tra un ciclo e il successivo, più un'unità di controllo a **FSM**.

## I registri non architetturali aggiunti
| Registro | Contenuto |
|---|---|
| **Instr** | l'istruzione prelevata dalla memoria (l'*instruction register*) |
| **Data** | il dato letto dalla memoria (per `LDR`) |
| **ALUOut** | il risultato dell'ALU del ciclo precedente |

## La costruzione, passo per passo (LDR)

### Ciclo 1 — Fetch
Il PC contiene l'indirizzo dell'istruzione. Si legge la memoria e **l'istruzione viene
memorizzata nel registro `Instr`**. Questo è indispensabile: la memoria serve anche per
i dati nei cicli successivi, quindi l'istruzione va conservata.
Contemporaneamente si calcola PC + 4.

### Ciclo 2 — Decode
Si **legge il register file** per ottenere il registro base, e si **estende
l'immediato**. Il blocco Extend è **combinatorio** in funzione di `Instr`: poiché `Instr`
è ora in un registro e non cambia, **`ExtImm` resta stabile** per tutta la durata
dell'istruzione, e non serve un registro per memorizzarlo.

### Ciclo 3 — MemAdr (calcolo dell'indirizzo)
L'ALU somma base e offset, con `ALUControl = 00` (addizione). **`ALUResult` viene
memorizzato in `ALUOut`**.

### Ciclo 4 — MemRead
`ALUOut` fornisce l'indirizzo alla memoria. Il dato letto viene **memorizzato nel
registro `Data`**.

### Ciclo 5 — MemWB (write-back)
Il registro `Data` è collegato direttamente alla porta di scrittura `WD3` del register
file. Il segnale **`RegWrite = 1`** indica che il register file va aggiornato, e il dato
viene scritto in `Rd`.

Nello stesso ciclo si scrive il nuovo PC (già calcolato al ciclo 1).

## Le altre istruzioni
| Istruzione | Cicli | Passi |
|---|---|---|
| **LDR** | **5** | Fetch, Decode, MemAdr, MemRead, MemWB |
| **STR** | **4** | Fetch, Decode, MemAdr, MemWrite |
| **Data-processing** | **4** | Fetch, Decode, Execute, ALUWB |
| **B** | **3** | Fetch, Decode, Branch |

### STR
Come `LDR` legge il base ed estende l'offset. **La novità**: deve leggere un **secondo
registro** dal register file (il dato da scrivere, campo `Rd`), quindi serve il
multiplexer `RegSrc` sull'indirizzo della seconda porta di lettura.

### Data-processing con immediato
Legge il primo operando dal register file, il secondo da `ExtImm` (mux `ALUSrc`).
`ALUControl` è determinato dal campo `cmd`. Il risultato passa da `ALUOut` al register
file.

### Data-processing con registro
Identica, ma il secondo operando viene selezionato dal **register file** invece che da
`ExtImm`.

### Branch
Legge **PC + 8** e l'immediato a 24 bit, li somma nell'ALU e **scrive il risultato nel
PC**.

## Il riuso dell'ALU per il PC
> [!important] L'economia del multiciclo
> Nel single-cycle servivano **tre sommatori**. Nel multiciclo ne serve **uno solo**:
> l'ALU calcola PC + 4 nel ciclo di fetch (quando non serve per altro), e calcola gli
> indirizzi di memoria o le operazioni aritmetiche nei cicli successivi.
>
> Per farlo si inseriscono **multiplexer sulle sorgenti dell'ALU**, per poter scegliere
> il **PC** e la **costante 4** come operandi.

## Il PC e R15
Anche qui vale la regola ARM: **leggere R15 restituisce PC + 8** e **scrivere R15
aggiorna il PC**. Nel multiciclo questo si realizza con multiplexer che instradano il
PC verso il register file e viceversa.

## Riepilogo: single-cycle vs multiciclo
| | single-cycle | multiciclo |
|---|---|---|
| memorie | **2** (istruzioni + dati) | **1** condivisa |
| sommatori | 3 (ALU + 2) | **1** (solo ALU) |
| registri non architetturali | nessuno | Instr, ALUOut, Data |
| CPI | 1 | 3–5 |
| $T_c$ | lungo | **breve** |
| unità di controllo | combinatoria | **FSM** |

## Da ricordare
- Registri non architetturali: **Instr, ALUOut, Data**.
- Cicli: **LDR 5, STR 4, data-processing 4, B 3**.
- Una **sola** memoria e un **solo** sommatore, riusati in cicli diversi.
- `ExtImm` non ha bisogno di registro perché è funzione combinatoria di `Instr`.

## Domande flash
1. Perché l'istruzione va memorizzata in `Instr`?
2. Perché `ExtImm` non richiede un registro dedicato?
3. Quanti cicli richiede `STR` e quali sono?

Collegato a: [[Processore multiciclo - controllo a FSM]]
