---
tags: [architettura, arm, assembly, cap6]
capitolo: 6
sezione: "6.2.2 - 6.2.3"
pagine_pdf: 314-319
---

# Operandi: registri, immediati e memoria

Un'istruzione opera su **operandi**. In ARM esistono tre tipi di operandi.

## 1. Operandi in registro
Il caso normale: gli operandi sono in R0–R15.
```
ADD R0, R1, R2      ; R0 = R1 + R2
```
> **In ARM le istruzioni operano esclusivamente sui registri**: i dati in memoria vanno
> prima **caricati** in un registro, elaborati, e poi eventualmente **riscritti** in
> memoria. Questa è la caratteristica di un'architettura **load/store**.

## 2. Operandi immediati (costanti)
Le istruzioni ARM possono usare **costanti** o **immediati** codificate direttamente
nell'istruzione. In assembly l'immediato è precedute dal simbolo **`#`** e si può
scrivere in decimale o in esadecimale (con prefisso `0x`).

```
ADD R0, R1, #42     ; R0 = R1 + 42
SUB R0, R1, #0x1F   ; R0 = R1 - 31
```

### L'istruzione MOV
L'istruzione **`MOV`** (move) è il modo tipico di **inizializzare** il valore di un
registro:
```
MOV R0, #17         ; R0 = 17
MOV R2, R3          ; R2 = R3
MVN R0, #0          ; R0 = NOT 0 = 0xFFFFFFFF
```

### Il vincolo sugli immediati a 12 bit
Il campo immediato nelle istruzioni di elaborazione dati è di **12 bit**, ma non
codifica un numero da 0 a 4095: è diviso in
- **8 bit di valore** (`imm8`) e
- **4 bit di rotazione** (`rot`),

e il valore effettivo è `imm8` **ruotato a destra** di $2 \times rot$ posizioni. Questo
permette di rappresentare costanti grandi ma "sparse" (come `0xFF000000`), mentre altre
costanti apparentemente semplici **non** sono rappresentabili in un solo immediato e
richiedono più istruzioni o un caricamento da memoria.

## 3. Operandi in memoria
Servono per i dati che non entrano nei registri (array, strutture, variabili globali).
Sono accessibili **solo** tramite le istruzioni `LDR` e `STR`
(→ [[Istruzioni LDR e STR]]).

## Il modello di memoria ARM
- Indirizzi a **32 bit** e parole di dati a **32 bit**.
- La memoria è **indirizzata al byte** (*byte-addressable*): ogni byte ha il suo
  indirizzo.
- Di conseguenza **gli indirizzi delle parole sono multipli di 4**: la parola 0 sta
  all'indirizzo 0, la parola 1 all'indirizzo 4, la parola 2 all'indirizzo 8, e così via.

```
indirizzo   contenuto (parola)
0x00000000  ...   <- word 0
0x00000004  ...   <- word 1
0x00000008  ...   <- word 2
```

## Da ricordare
- ARM è **load/store**: le istruzioni ALU lavorano solo su registri.
- Gli immediati sono precedute da `#`; il campo è 8 bit di valore + 4 di rotazione.
- Memoria **indirizzata al byte**, parole allineate a multipli di **4**.
- `MOV` per inizializzare, `MVN` per il complemento.

## Domande flash
1. Qual è l'indirizzo della quinta parola in memoria (partendo dalla parola 0)?
2. Perché `0xFF000000` è rappresentabile come immediato e `0x12345678` no?
