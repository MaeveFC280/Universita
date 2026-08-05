---
tags: [architettura, arm, assembly, cap6]
capitolo: 6
sezione: "6.3.1"
pagine_pdf: 319-322
---

# Istruzioni logiche, di shift e di moltiplicazione

## Operazioni logiche
Le operazioni logiche ARM sono: **AND**, **ORR** (OR), **EOR** (XOR) e **BIC** (bit
clear). Operano **bit a bit** su due operandi a 32 bit.

Formato: la prima sorgente è **sempre un registro**, la seconda può essere un
**registro** o un **immediato**; il risultato va in un registro di destinazione.

```
AND R0, R1, R2      ; R0 = R1 AND R2
ORR R0, R1, #0xFF   ; R0 = R1 OR 0xFF
EOR R0, R1, R2      ; R0 = R1 XOR R2
BIC R0, R1, R2      ; R0 = R1 AND (NOT R2)
MVN R0, R1          ; R0 = NOT R1
```

## Gli usi tipici (importanti)
> [!important] I due idiomi da conoscere
> - **BIC** serve a **mascherare** (azzerare) i bit indesiderati: ogni 1 nella maschera
>   **azzera** il bit corrispondente. `BIC R0, R1, #0xFF` azzera il byte basso di R1.
> - **AND** serve a **isolare** un campo di bit: ogni 0 nella maschera azzera il bit
>   corrispondente. `AND R0, R1, #0xFF` mantiene **solo** il byte basso.
> - **ORR** serve a **combinare campi di bit** provenienti da due registri (dopo averli
>   allineati con degli shift).
> - **EOR** con tutti 1 equivale a complementare; EOR con se stesso azzera.

Sequenza tipica per estrarre e ricomporre bitfield:
```
AND  R2, R1, #0xFF00   ; isola il campo
LSR  R2, R2, #8        ; allinealo a destra
ORR  R3, R3, R2        ; inseriscilo nel risultato
```

## Istruzioni di shift
Le istruzioni di shift spostano il valore di un registro a destra o a sinistra,
**scartando** i bit che escono.

| Istruzione | Nome | Riempimento |
|---|---|---|
| `LSL` | logical shift left | zeri a destra |
| `LSR` | logical shift right | zeri a sinistra |
| `ASR` | arithmetic shift right | copie del **bit di segno** |
| `ROR` | rotate right | i bit che escono rientrano dall'altro lato |

```
LSL R0, R1, #3      ; R0 = R1 << 3   (= R1 * 8)
ASR R0, R1, #2      ; R0 = R1 >> 2   (con segno)
ROR R0, R1, R2      ; rotazione di una quantità variabile
```

La quantità di shift può essere un **immediato** (0–31) o un **registro**.

→ [[Shifter e rotatori]]

## Lo shift "gratuito" del secondo operando
> [!tip] Una caratteristica distintiva di ARM
> Il **secondo operando** di qualunque istruzione di elaborazione dati può essere
> shiftato **nella stessa istruzione**, senza costo aggiuntivo in cicli:
>
> ```
> ADD R0, R1, R2, LSL #3    ; R0 = R1 + (R2 << 3)  = R1 + 8*R2
> ```
>
> Questo è possibile perché il datapath contiene uno shifter **in serie** al percorso
> del secondo operando, prima dell'ALU. È estremamente utile per l'accesso agli array
> (→ [[Array e modalita di indirizzamento]]).

## Moltiplicazione
| Istruzione | Effetto |
|---|---|
| `MUL R0,R1,R2` | moltiplica due numeri a 32 bit, produce un risultato a **32 bit** (i 32 bit **bassi** del prodotto) |
| `MLA R0,R1,R2,R3` | *multiply-accumulate*: $R0 = R1 \cdot R2 + R3$ |
| `UMULL`/`SMULL` | prodotto **lungo**: risultato a 64 bit su due registri, senza/con segno |

Nota: `MUL` **scarta** i 32 bit alti del prodotto. Se servono, si usa `UMULL`/`SMULL`.

Non esiste un'istruzione di **divisione** nell'ARM classico: si realizza in software
(o con istruzioni dedicate nelle versioni più recenti dell'architettura).

## Da ricordare
- AND / ORR / EOR / BIC + MVN. **BIC = AND con il complemento**.
- AND per **isolare**, BIC per **azzerare**, ORR per **combinare**.
- LSL/LSR zeri, ASR segno, ROR circolare.
- Il **secondo operando può essere shiftato gratis** nella stessa istruzione.
- `MUL` dà solo i 32 bit bassi; `UMULL`/`SMULL` danno 64 bit.

## Domande flash
1. Come si azzerano i bit 4–7 di R1 lasciando gli altri invariati?
2. Che cosa fa `ADD R0, R1, R1, LSL #2`?
3. Perché non esiste un'istruzione di divisione?
