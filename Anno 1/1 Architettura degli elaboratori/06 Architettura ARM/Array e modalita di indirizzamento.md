---
Materia: Architettura degli elaboratori
tags:
  - ARM
  - assembly
  - memoria
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 6.3.4'
Imparato: false
Ordine: 610
aliases:
  - array
  - indirizzamento indicizzato
  - offset
---

# Array e modalità di indirizzamento

## Perché gli array
Per facilità di memorizzazione e di accesso, dati **omogenei** si raggruppano in un
**array**: elementi dello stesso tipo, in posizioni **consecutive** di memoria.
L'accesso avviene tramite l'**indirizzo base** dell'array e l'**indice** dell'elemento.

## Il calcolo dell'indirizzo
Per un array di **word** (4 byte), l'indirizzo dell'elemento $i$ è:

$$\text{indirizzo} = \text{base} + 4i$$

> [!important] Il fattore 4
> Poiché l'indice dell'array è una **variabile** ($i$), va **moltiplicato per 4** prima
> di sommarlo all'indirizzo base. È l'errore più frequente: dimenticare lo scalamento e
> accedere a `base + i` invece di `base + 4i`.

## Le tre tecniche di accesso

### 1. Offset immediato (indice costante noto)
```
LDR R1, [R0, #8]        ; R1 = array[2]   (8 = 4*2)
```

### 2. Registro di offset scalato (il modo idiomatico ARM)
L'offset può essere un **registro shiftato**: si sfrutta lo shifter integrato nel
datapath, ottenendo la moltiplicazione per 4 **gratis**.

```
; R0 = base, R2 = i
LDR R1, [R0, R2, LSL #2]   ; R1 = array[i]   (R2 << 2 == R2 * 4)
```
Questa è la forma più efficiente e la più usata: **una sola istruzione** per indicizzare.

### 3. Aggiornamento del puntatore (pre/post-indexed)
```
LDR R1, [R0], #4        ; R1 = *R0; poi R0 += 4  (post-indexed)
```
Ideale per scorrere l'array in un ciclo senza gestire un indice separato.

## Riepilogo delle modalità di indirizzamento
| Modalità | Sintassi | Indirizzo | Base aggiornato |
|---|---|---|---|
| immediato scalato | `[Rn, #imm]` | $Rn + imm$ | no |
| registro | `[Rn, Rm]` | $Rn + Rm$ | no |
| registro scalato | `[Rn, Rm, LSL #k]` | $Rn + (Rm \ll k)$ | no |
| pre-indexed | `[Rn, #imm]!` | $Rn + imm$ | **sì, prima** |
| post-indexed | `[Rn], #imm` | $Rn$ | **sì, dopo** |

L'offset può essere **sommato o sottratto** (base ± offset).

## Esempio completo: raddoppiare i primi 5 elementi
```c
int arr[5];
for (i = 0; i < 5; i++)
    arr[i] = arr[i] * 2;
```
```
        ; R0 = indirizzo base di arr, R1 = i
        MOV  R1, #0
loop
        CMP  R1, #5
        BGE  done
        LDR  R2, [R0, R1, LSL #2]   ; R2 = arr[i]
        LSL  R2, R2, #1             ; R2 = R2 * 2
        STR  R2, [R0, R1, LSL #2]   ; arr[i] = R2
        ADD  R1, R1, #1
        B    loop
done
```

### Versione con post-indexed (più compatta)
```
        MOV  R1, #5
loop
        LDR  R2, [R0]
        LSL  R2, R2, #1
        STR  R2, [R0], #4      ; scrivi e avanza il puntatore
        SUBS R1, R1, #1
        BNE  loop
```

## Array multidimensionali (cenno)
Un array 2D `a[R][C]` è memorizzato per **righe** (*row-major* in C). L'indirizzo di
`a[i][j]` è:
$$\text{base} + 4 \cdot (i \cdot C + j)$$

## Da ricordare
- Indirizzo elemento $i$ di un array di word: $base + 4i$.
- `[Rn, Rm, LSL #2]` è l'idioma ARM per l'accesso indicizzato: **una istruzione**.
- Post-indexed `[Rn], #4` per scorrere senza indice.

## Domande flash
1. Scrivi in ARM l'accesso a `a[i]` per un array di **byte** anziché di word.
2. Perché `LDR R1, [R0, R2, LSL #2]` è preferibile a due istruzioni separate?
