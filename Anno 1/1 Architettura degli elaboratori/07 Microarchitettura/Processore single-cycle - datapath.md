---
Materia: Architettura degli elaboratori
tags:
  - microarchitettura
  - datapath
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 7.3.1'
Imparato: true
Ordine: 703
aliases:
  - single-cycle
  - ciclo singolo
---
Il [datapath](Datapath%20e%20unita%20di%20controllo) è l'insieme dei componenti e dei collegamenti attraverso cui passano i dati durante l'esecuzione di un'istruzione.

Nel processore **single-cycle**, ogni istruzione viene completata in **un solo ciclo di clock**. `LDR`, `STR`, le istruzioni di elaborazione dati e `B` sono istruzioni diverse che utilizzano **percorsi diversi dello stesso datapath**.

Tutte iniziano con il **fetch** dell'istruzione; successivamente, il percorso dipende dal tipo di istruzione.
## Fetch dell'istruzione
### Fetch
Il **program counter** contiene l'indirizzo dell'istruzione da eseguire. Il PC alimenta la memoria istruzioni, che restituisce l'istruzione corrente, la memoria restituisce i 32 bit dell'istruzione:`Instr`.

```
PC --> [Memoria Istruzioni] --> Instr
```
> [!important] Contenuto di un'istruzione
Un'istruzione ARM  occupa 32 bit=4 byte quindi si possono avere istruzioni tipo:
`0x1000    SUB R0,R1,R2`
`0x1004    ADD R3,R4,R5`
`0x1008    ...`
### Incremento del PC
Il PC deve avanzare all'istruzione successiva: serve un [[Half adder e full adder|sommatore]] che calcoli **PC + 4**.

> [!important] Il secondo sommatore: PC + 8
> Poiché **leggere R15 deve restituire PC + 8**, serve un **ulteriore sommatore** che calcoli PC + 8, il cui risultato è instradato verso il register file quando l'istruzione legge [[Registri ARM|R15]].

![[Processore single-cycle - datapath-1787749081759.webp|163]]![[Processore single-cycle - datapath-1787749128341.webp]]

## LDR

### Lettura del registro base
Per l'istruzione `LDR` il passo successivo è **leggere il registro sorgente** che contiene l'indirizzo base. Il campo `Rn` (bit 19:16) di `Instr` alimenta l'indirizzo della **porta 1** del [[Register file ROM e logic array|register file]], che produce il valore su `RD1`.

### Offset
`LDR` richiede anche un **offset**, memorizzato nel campo immediato dell'istruzione (bit 11:0). Poiché l'offset è a 12 bit senza segno e i dati sono a 32 bit, un blocco **Extend** lo estende a 32 bit producendo `ExtImm`.

Il blocco Extend deve gestire **più formati** (immediato a 12 bit di LDR/STR, immediato a 8 bit con rotazione dei data-processing, immediato a 24 bit dei branch): è quindi comandato dal segnale **`ImmSrc`**.

### Calcolo dell'indirizzo
L'**[[Sottrattori comparatori e ALU|ALU]]** somma base e offset e produce `ALUResult` a 32 bit. Per `LDR`, `ALUControl` vale il codice dell'**addizione** (00).
### Accesso alla memoria dati
`ALUResult` è l'indirizzo per la memoria dati. Il dato letto compare sul bus `ReadData`.

### Write-back
Il dato letto viene **scritto nel register file** all'indirizzo `Rd` (bit 15:12), sulla porta di scrittura, abilitata da `RegWrite`.


## STR
Come `LDR`, `STR` legge l'indirizzo base dalla porta 1 del register file ed estende l'offset. **La novità**: deve leggere anche il **dato da scrivere**, che sta nel campo `Rd`. Si aggiunge quindi un [[Multiplexer|multiplexer]] sull'indirizzo della **porta 2** di lettura (segnale **`RegSrc`**), per poter leggere `Rd` anziché `Rm`.

Il dato letto va all'ingresso `WriteData` della memoria dati, abilitata da `MemWrite`.

## Istruzioni di elaborazione dati
Come `LDR`, leggono il primo operando dalla porta 1. La differenza è il **secondo operando**:
- con **[[Operandi|indirizzamento]] immediato**: usano un immediato a **8 bit**, quindi il blocco Extend ha una modalità in più;
- con **indirizzamento a registro**: il secondo operando viene dal register file (campo `Rm`, bit 3:0).

Serve quindi un multiplexer comandato da **`ALUSrc`** che scelga tra `ExtImm` e il secondo registro letto.

Inoltre le istruzioni di elaborazione dati scrivono **`ALUResult`** nel register file (non `ReadData`): serve un multiplexer sul dato di [[Blocchi politiche di sostituzione e scrittura|write-back]], comandato da **`MemtoReg`**.

## Branch (B)
Il branch:
- legge **PC + 8** e un **immediato a 24 bit**;
- li somma (l'immediato scalato di 4 e **esteso con segno**) per ottenere l'indirizzo di destinazione;
- scrive il risultato nel **PC**.

Il blocco Extend necessita quindi di un'**ulteriore modalità** per l'immediato a 24 bit esteso con segno e moltiplicato per 4. E serve un multiplexer sull'ingresso del PC, comandato da **`PCSrc`**, per scegliere tra PC+4 e l'indirizzo di destinazione.
## Segnali

| Segnale          | Valore | Significato                                       |
| ---------------- | -----: | ------------------------------------------------- |
| **`RegSrc[1]`**  |    `0` | seconda porta legge `Rm`                          |
|                  |    `1` | seconda porta legge `Rd`                          |
| **`RegSrc[0]`**  |    `0` | prima porta legge `Rn`                            |
|                  |    `1` | prima porta legge `R15`                           |
| **`ImmSrc`**     |   `00` | immediato **8 bit + rotazione** → Data Processing |
|                  |   `01` | immediato **12 bit** → `LDR`/`STR`                |
|                  |   `10` | immediato **24 bit × 4, sign-extended** → `B`     |
| **`ALUSrc`**     |    `0` | secondo operando ALU = `RD2` (registro)           |
|                  |    `1` | secondo operando ALU = `ExtImm` (immediato)       |
| **`ALUControl`** |   `00` | ADD                                               |
|                  |   `01` | SUB                                               |
|                  |   `10` | AND                                               |
|                  |   `11` | ORR                                               |
| **`MemWrite`**   |    `0` | non scrivere nella memoria                        |
|                  |    `1` | scrivi nella memoria                              |
| **`MemtoReg`**   |    `0` | nel registro scrivi `ALUResult`                   |
|                  |    `1` | nel registro scrivi `ReadData` dalla memoria      |
| **`RegWrite`**   |    `0` | non scrivere nel Register File                    |
|                  |    `1` | scrivi nel Register File                          |
| **`PCSrc`**      |    `0` | prossimo PC = `PC+4`                              |
|                  |    `1` | PC riceve il risultato destinato al PC            |
![[Datapath e unita di controllo-1787502063076.webp]]