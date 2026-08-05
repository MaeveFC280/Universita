---
Materia: Architettura degli elaboratori
tags:
  - aritmetica
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 5.2.5'
Imparato: false
Ordine: 505
aliases:
  - shifter
  - rotatore
  - LSL
  - ASR
---

# Shifter e rotatori

## Funzione
Gli **shifter** e i **rotatori** spostano i bit di una parola. Come suggerisce il nome,
gli shifter **moltiplicano o dividono per potenze di 2**.

## I tre tipi

### Logical shifter (shift logico)
Sposta il numero a sinistra (**LSL**) o a destra (**LSR**) e riempie le posizioni
liberate con **zeri**.
- `11001 LSR 2 = 00110`
- `11001 LSL 2 = 00100` (i bit che escono sono perduti)

### Arithmetic shifter (shift aritmetico)
Uguale allo shift logico, ma negli shift a **destra** (**ASR**) riempie le posizioni più
significative con copie del **bit di segno** originale (il msb).
- `11001 ASR 2 = 11110`

Serve per dividere correttamente i numeri **in complemento a due**: replicare il segno
è la stessa idea della *sign extension*.

### Rotator (rotatore)
Ruota il numero **in circolo**, in modo che le posizioni liberate siano riempite con i
bit che escono dall'altra estremità (**ROR** a destra, **ROL** a sinistra).
- `11001 ROR 2 = 01110`

## Relazione con moltiplicazione e divisione
| Operazione | Effetto |
|---|---|
| shift **sinistro** di $k$ | moltiplica per $2^k$ |
| shift logico **destro** di $k$ | divide per $2^k$ (numeri **senza segno**) |
| shift aritmetico **destro** di $k$ | divide per $2^k$ (numeri **con segno**) |

> [!warning] Attenzione
> Usare LSR su un numero negativo in complemento a due dà un risultato **sbagliato**:
> serve ASR. E lo shift a destra dei negativi arrotonda verso $-\infty$, non verso zero.

## Realizzazione
Uno shifter a $N$ bit si costruisce con $N$ multiplexer $N$:1 (uno per bit di uscita),
oppure — più efficientemente — con un **barrel shifter**: una cascata di $\log_2 N$
livelli di mux 2:1, dove il livello $j$ sposta di $2^j$ posizioni se il bit $j$ della
quantità di shift è 1.

## Nota su ARM
Nell'architettura ARM lo shifter è **integrato nel datapath**: il secondo operando di
un'istruzione può essere shiftato "gratis", nella stessa istruzione
(→ [[Istruzioni logiche e di shift]]).

## Da ricordare
- LSL / LSR riempiono con 0; ASR replica il **segno**; ROR ricircola i bit.
- Shift sinistro = ×$2^k$; shift destro = ÷$2^k$ (ASR per i numeri con segno).
- Barrel shifter: $\log_2 N$ livelli di mux.

## Domande flash
1. `10110 ASR 1` quanto fa? E `10110 LSR 1`?
2. Perché per dividere $-8$ per 2 serve ASR?
