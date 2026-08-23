---
Materia: Architettura degli elaboratori
tags:
  - microarchitettura
  - FSM
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 7.4.2'
Imparato: false
Ordine: 707
aliases:
  - controllo multiciclo
  - FSM di controllo
---
## Struttura
Come nel single-cycle, l'unità di controllo calcola i segnali a partire da `cond`, `op`,
`funct` e `Rd`, ed è partizionata in **Decoder** e **Conditional Logic**.

**La differenza fondamentale**: nel multiciclo il Decoder contiene una **macchina a
stati finiti** — la **Main FSM** — perché i segnali di controllo dipendono non solo
dall'istruzione ma anche **dal ciclo corrente** dell'esecuzione.

La Main FSM produce i segnali di **selezione dei multiplexer**, di **abilitazione dei
registri** e di **scrittura in memoria**, ciclo per ciclo.

## Gli stati della Main FSM

### Fetch (comune a tutte)
> Il **primo passo per qualunque istruzione** è prelevare l'istruzione dalla memoria.

Nello stato **Fetch**:
- l'indirizzo per la memoria è il **PC** (`AdrSrc = 0`);
- l'istruzione letta è scritta in `Instr` (`IRWrite = 1`);
- in parallelo l'ALU calcola **PC + 4** e il risultato viene scritto nel PC.

### Decode (comune a tutte)
> Il **secondo passo** è **leggere il register file e/o l'immediato e decodificare
> l'istruzione**.

Nello stato **Decode** non si compie nessuna azione irreversibile: si leggono i registri
(letture combinatorie, senza effetti collaterali) e si decide **dove andare**. Da qui la
FSM procede verso uno di **diversi stati possibili**, in base a **`op`** e **`Funct`**.

### La diramazione
| Se l'istruzione è… | Stato successivo |
|---|---|
| `LDR`/`STR` (op=01) | **MemAdr** |
| Data-processing (op=00) | **ExecuteR** o **ExecuteI** |
| `B` (op=10) | **Branch** |

### Il ramo memoria
- **MemAdr**: l'ALU calcola base + offset; il risultato va in `ALUOut`.
- Se l'istruzione è **`LDR`** (`Funct0 = 1`, cioè bit L = 1) → **MemRead**: si legge la
  memoria all'indirizzo `ALUOut` e il dato va nel registro `Data`.
  → **MemWB**: il dato viene scritto nel register file.
- Se l'istruzione è **`STR`** (L = 0) → **MemWrite**: si scrive in memoria il dato letto
  dal register file (`MemWrite = 1`). L'istruzione termina qui, in 4 cicli.

### Il ramo elaborazione dati
- **ExecuteR** (secondo operando da registro) oppure **ExecuteI** (secondo operando da
  immediato): l'ALU esegue l'operazione indicata da `cmd`; il risultato va in `ALUOut`.
- **ALUWB**: `ALUOut` viene scritto nel register file.

### Il ramo branch
- **Branch**: l'ALU somma PC+8 e l'immediato esteso; il risultato viene scritto nel
  **PC**. L'istruzione termina in 3 cicli.

## Diagramma sintetico
```
              ┌──────────┐
              │  Fetch   │  (PC -> Instr; PC = PC+4)
              └────┬─────┘
                   v
              ┌──────────┐
              │  Decode  │  (legge RF, estende imm)
              └──┬───┬───┴──────────┐
      op=01      │   │ op=00        │ op=10
                 v   v              v
           ┌─────────┐  ┌──────────────┐  ┌────────┐
           │ MemAdr  │  │ExecuteR / I  │  │ Branch │
           └──┬───┬──┘  └──────┬───────┘  └────────┘
       L=1    │   │ L=0        v
              v   v      ┌──────────┐
      ┌────────┐ ┌──────────┐  │  ALUWB   │
      │MemRead │ │MemWrite │  └──────────┘
      └───┬────┘ └─────────┘
          v
      ┌────────┐
      │ MemWB  │
      └────────┘
```
Da ogni stato terminale (MemWB, MemWrite, ALUWB, Branch) la FSM **torna a Fetch**.

## Conditional Logic
Identica in principio al single-cycle: confronta `cond` con i flag e, se la condizione
non è soddisfatta, **inibisce** `RegWrite`, `MemWrite` e la scrittura del PC. Nel
multiciclo l'inibizione va applicata **nel ciclo giusto** (quello in cui si compie la
scrittura).

## Da ricordare
- Il controllo del multiciclo è una **FSM**, non logica puramente combinatoria.
- **Fetch e Decode sono comuni a tutte** le istruzioni (i primi 2 cicli).
- La diramazione avviene dopo Decode, in base a `op` (e a `Funct` per LDR/STR).
- Ogni stato terminale ritorna a **Fetch**.

## Domande flash
1. Quali due stati sono comuni a tutte le istruzioni?
2. Quale bit distingue il percorso di `LDR` da quello di `STR` dopo MemAdr?
3. Perché nello stato Decode non si compiono azioni irreversibili?
