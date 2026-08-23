---
Materia: Architettura degli elaboratori
tags:
  - microarchitettura
  - datapath
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 7.3.1'
Imparato: false
Ordine: 703
aliases:
  - single-cycle
  - ciclo singolo
---
Il [[Datapath e unita di controllo|datapath]] si costruisce **incrementalmente**, aggiungendo un'istruzione alla volta. Questo è il modo giusto di studiarlo (e di ricostruirlo in esame).

## Passo 0 — Fetch dell'istruzione
Il **program counter** contiene l'indirizzo dell'istruzione da eseguire. Il PC alimenta la memoria istruzioni, che restituisce l'istruzione corrente, `Instr`.

```
PC --> [Memoria Istruzioni] --> Instr
```

## Passo 1 — LDR: lettura del registro base
Per l'istruzione `LDR` il passo successivo è **leggere il registro sorgente** che contiene l'indirizzo base. Il campo `Rn` (bit 19:16) di `Instr` alimenta l'indirizzo della **porta 1** del [[Register file ROM e logic array|register file]], che produce il valore su `RD1`.

## Passo 2 — LDR: l'offset
`LDR` richiede anche un **offset**, memorizzato nel campo immediato dell'istruzione (bit 11:0). Poiché l'offset è a 12 bit senza segno e i dati sono a 32 bit, un blocco **Extend** lo estende a 32 bit producendo `ExtImm`.

Il blocco Extend deve gestire **più formati** (immediato a 12 bit di LDR/STR, immediato a 8 bit con rotazione dei data-processing, immediato a 24 bit dei branch): è quindi comandato dal segnale **`ImmSrc`**.

## Passo 3 — LDR: calcolo dell'indirizzo
L'**ALU** somma base e offset e produce `ALUResult` a 32 bit. Per `LDR`, `ALUControl` vale il codice dell'**addizione** (00).

## Passo 4 — LDR: accesso alla memoria dati
`ALUResult` è l'indirizzo per la memoria dati. Il dato letto compare sul bus `ReadData`.

## Passo 5 — LDR: write-back
Il dato letto viene **scritto nel register file** all'indirizzo `Rd` (bit 15:12), sulla porta di scrittura, abilitata da `RegWrite`.

## Passo 6 — Incremento del PC
Il PC deve avanzare all'istruzione successiva: serve un [[Half adder e full adder|sommatore]] che calcoli **PC + 4**.

> [!important] Il secondo sommatore: PC + 8
> Poiché **leggere R15 deve restituire PC + 8**, serve un **ulteriore sommatore** che calcoli PC + 8, il cui risultato è instradato verso il register file quando l'istruzione legge [[Registri ARM|R15]].

## Passo 7 — STR
Come `LDR`, `STR` legge l'indirizzo base dalla porta 1 del register file ed estende l'offset. **La novità**: deve leggere anche il **dato da scrivere**, che sta nel campo `Rd`. Si aggiunge quindi un [[Multiplexer|multiplexer]] sull'indirizzo della **porta 2** di lettura (segnale **`RegSrc`**), per poter leggere `Rd` anziché `Rm`.

Il dato letto va all'ingresso `WriteData` della memoria dati, abilitata da `MemWrite`.

## Passo 8 — Istruzioni di elaborazione dati
Come `LDR`, leggono il primo operando dalla porta 1. La differenza è il **secondo operando**:
- con **[[Operandi|indirizzamento]] immediato**: usano un immediato a **8 bit** (non 12), quindi il blocco Extend ha una modalità in più;
- con **indirizzamento a registro**: il secondo operando viene dal register file (campo `Rm`, bit 3:0).

Serve quindi un multiplexer comandato da **`ALUSrc`** che scelga tra `ExtImm` e il secondo registro letto.

Inoltre le istruzioni di elaborazione dati scrivono **`ALUResult`** nel register file (non `ReadData`): serve un multiplexer sul dato di [[Blocchi politiche di sostituzione e scrittura|write-back]], comandato da **`MemtoReg`**.

## Passo 9 — Branch (B)
Il branch:
- legge **PC + 8** e un **immediato a 24 bit**;
- li somma (l'immediato scalato di 4 e **esteso con segno**) per ottenere l'indirizzo di destinazione;
- scrive il risultato nel **PC**.

Il blocco Extend necessita quindi di un'**ulteriore modalità** per l'immediato a 24 bit esteso con segno e moltiplicato per 4. E serve un multiplexer sull'ingresso del PC, comandato da **`PCSrc`**, per scegliere tra PC+4 e l'indirizzo di destinazione.

## Riepilogo dei multiplexer e dei loro segnali
| Segnale | Sceglie |
|---|---|
| `RegSrc` | quale registro leggere sulle porte del register file (Rm vs Rd vs R15) |
| `ImmSrc` | come estendere l'immediato (12 bit / 8 bit+rot / 24 bit×4) |
| `ALUSrc` | secondo operando dell'ALU: registro o `ExtImm` |
| `ALUControl` | quale operazione esegue l'ALU |
| `MemWrite` | abilita la scrittura in memoria dati |
| `MemtoReg` | dato di write-back: `ReadData` o `ALUResult` |
| `RegWrite` | abilita la scrittura nel register file |
| `PCSrc` | prossimo PC: PC+4 o indirizzo di branch |

## Da ricordare
- Si costruisce **istruzione per istruzione**: fetch → decode/lettura registri → esecuzione ALU → memoria → write-back → aggiornamento PC.
- Ogni istruzione nuova aggiunge tipicamente **un multiplexer** e **un segnale di controllo**.
- Servono **due sommatori** oltre all'ALU: PC+4 e PC+8.
- L'unico blocco davvero "nuovo" rispetto al capitolo 5 è **Extend**.
