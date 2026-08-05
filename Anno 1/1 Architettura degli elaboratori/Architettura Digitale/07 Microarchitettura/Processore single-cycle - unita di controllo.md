---
tags: [architettura, microarchitettura, single-cycle, controllo, cap7]
capitolo: 7
sezione: "7.3.2"
pagine_pdf: 413-418
---

# Processore single-cycle: l'unità di controllo

## Che cosa fa
L'**unità di controllo** calcola i segnali di controllo a partire dai campi
**`cond`**, **`op`** e **`funct`** dell'istruzione, più i flag di stato. Contiene
inoltre i **flag di stato correnti** e li **aggiorna** quando l'istruzione lo richiede.

## La partizione in due parti
L'unità di controllo si divide in due parti principali:

| Parte | Compito |
|---|---|
| **Decoder** | genera i segnali di controllo **in base al tipo di istruzione** (`op`, `funct`) |
| **Conditional Logic** | mantiene i **flag di stato** e **annulla** l'esecuzione se la condizione `cond` non è soddisfatta |

## Il Decoder
È a sua volta scomposto in tre blocchi:

### Main Decoder
Determina il **tipo di istruzione** dai bit `op` e da `funct`:
- Data-Processing con registro
- Data-Processing con immediato
- STR
- LDR
- B

E produce di conseguenza: `Branch`, `MemtoReg`, `MemW`, `ALUSrc`, `ImmSrc`, `RegW`,
`RegSrc`, `ALUOp`.

### ALU Decoder
Se `ALUOp = 1` (istruzione di elaborazione dati), traduce il campo **`cmd`** nel segnale
**`ALUControl`** e decide se i flag vanno aggiornati (`FlagW`), in base al bit **`S`**.
Se `ALUOp = 0` (LDR/STR/B), forza `ALUControl` all'**addizione**.

### PC Logic
Determina se il PC deve essere aggiornato con un indirizzo di branch: vale per
l'istruzione **`B`**, ma **anche** per qualunque istruzione che scriva in **R15**
(`Rd = 15`), poiché in ARM scrivere nel PC provoca un salto.

$$PCS = \big((Rd = 15)\ \text{AND}\ RegW\big)\ \text{OR}\ Branch$$

## La Conditional Logic
Realizza la caratteristica distintiva di ARM: **l'esecuzione condizionale**.

1. Confronta i **4 bit `cond`** dell'istruzione con i **flag di stato** correnti
   (N, Z, C, V) e produce `CondEx` (condizione soddisfatta / non soddisfatta).
2. Se `CondEx = 0`, **azzera** i segnali che producono effetti visibili:
   `PCSrc`, `RegWrite`, `MemWrite` diventano 0. L'istruzione si comporta come una **NOP**.
3. Se l'istruzione deve aggiornare i flag (`FlagW`) **e** la condizione è soddisfatta,
   i flag vengono scritti con `ALUFlags`.

> [!important] Il meccanismo chiave
> L'esecuzione condizionale **non** è realizzata con salti nascosti: è realizzata
> **inibendo i segnali di scrittura**. L'istruzione attraversa comunque il datapath, ma
> non modifica lo stato. Questo spiega perché costa **un ciclo** anche quando non fa nulla.

## Struttura complessiva dei segnali
```
Instr[31:28] cond ──> Conditional Logic ──> PCSrc, RegWrite, MemWrite
Instr[27:26] op   ──> Main Decoder      ──> ALUSrc, ImmSrc, MemtoReg, RegSrc, ALUOp
Instr[25:20] funct──> ALU Decoder       ──> ALUControl, FlagW
Instr[15:12] Rd   ──> PC Logic          ──> PCS
ALUFlags          ──> Conditional Logic (registro dei flag)
```

## Tabella di verità (schema del Main Decoder)
| Istruzione | op | funct | RegW | MemW | MemtoReg | ALUSrc | ImmSrc | Branch |
|---|---|---|---|---|---|---|---|---|
| DP reg | 00 | I=0 | 1 | 0 | 0 | 0 | – | 0 |
| DP imm | 00 | I=1 | 1 | 0 | 0 | 1 | 8-bit | 0 |
| STR | 01 | L=0 | 0 | **1** | – | 1 | 12-bit | 0 |
| LDR | 01 | L=1 | 1 | 0 | **1** | 1 | 12-bit | 0 |
| B | 10 | – | 0 | 0 | – | 1 | 24-bit | **1** |

(La tabella completa del libro include anche `RegSrc` e `ALUOp`; questa è la struttura
essenziale da ricostruire.)

## Da ricordare
- Controllo = **Decoder** (Main + ALU + PC Logic) + **Conditional Logic**.
- La condizionalità si realizza **azzerando RegWrite, MemWrite, PCSrc**.
- $PCS = (Rd{=}15 \cdot RegW) + Branch$: scrivere in R15 **è** un salto.
- `ALUOp = 0` → l'ALU somma (serve per LDR/STR/B).

## Domande flash
1. Cosa fa la Conditional Logic quando `cond` non è soddisfatta?
2. Perché `PCS` dipende anche da `Rd`?
3. Quale segnale distingue LDR da STR nel Main Decoder?
