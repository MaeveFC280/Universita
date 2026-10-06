---
Materia: Architettura degli elaboratori
tags:
  - ARM
  - assembly
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 6.3.2'
Imparato: true
Ordine: 606
aliases:
  - CMP
  - flag NZCV
  - condition flags
---
## I flag
Le istruzioni ARM possono **opzionalmente** aggiornare i **flag di condizione** (o *status bits*) in base al risultato prodotto. I quattro flag sono:

| Flag | Nome | Vale 1 quando |
|---|---|---|
| **N** | *Negative* | il risultato è **negativo** (msb = 1) |
| **Z** | *Zero* | il risultato è **zero** |
| **C** | *Carry* | c'è stato un **riporto** in uscita (aritmetica senza segno) |
| **V** | *oVerflow* | si è verificato **overflow** in complemento a due |

I flag risiedono nel registro di stato del processore (**CPSR**).

## Come si impostano i flag

### Con il suffisso S
Aggiungendo **`S`** al mnemonico, l'istruzione aggiorna i flag oltre a scrivere il risultato:
```
ADDS R0, R1, R2     ; R0 = R1 + R2  E aggiorna N,Z,C,V
SUBS R0, R1, R2     ; idem per la sottrazione
```
Senza `S`, i flag **non vengono toccati**.

### Con CMP (il modo più comune)
Il modo più comune di impostare i flag è l'istruzione **`CMP`** (*compare*):

```
CMP R1, R2          ; calcola R1 - R2, aggiorna i flag, SCARTA il risultato
CMP R1, #10         ; confronta con un immediato
```

`CMP` **sottrae** il secondo operando dal primo e aggiorna i flag, ma **non memorizza** il risultato in alcun registro. Serve unicamente a preparare i flag per un'istruzione condizionale successiva.

| Istruzione    | **Operazione (risultato scartato)** |
| ------------- | ----------------------------------- |
| `CMP Rn, Op2` | $Rn -$ Op2                          |
| `CMN Rn, Op2` | $Rn +$ Op2 (*compare negative*      |
| `TST Rn, Op2` | $Rn$ AND Op2 (test di bit)          |
| `TEQ Rn, Op2` | $Rn$ EOR Op2 (test di uguaglianza)  |

## Come si leggono i flag
Le **istruzioni successive** possono eseguirsi **condizionalmente** in base allo stato dei flag. Con questo meccanismo si implementa `if` tramite [[Branch ed esecuzione condizionale|i cicli e i salti condizionati]].

*Esempio dell'idioma fondamentale:*
```
CMP  R1, R2         ; confronta
BEQ  uguali         ; salta se sono uguali (Z=1)
```

### Le principali condizioni
| Suffisso | Significato | Flag |
|---|---|---|
| `EQ` | uguale | $Z=1$ |
| `NE` | diverso | $Z=0$ |
| `MI` | negativo (*minus*) | $N=1$ |
| `PL` | positivo o zero (*plus*) | $N=0$ |
| `GE` | $\ge$ (**con segno**) | $N = V$ |
| `LT` | $<$ (**con segno**) | $N \ne V$ |
| `GT` | $>$ (**con segno**) | $Z=0$ e $N=V$ |
| `LE` | $\le$ (**con segno**) | $Z=1$ oppure $N \ne V$ |
| `HS`/`CS` | $\ge$ (**senza segno**) | $C=1$ |
| `LO`/`CC` | $<$ (**senza segno**) | $C=0$ |
| `HI` | $>$ (senza segno) | $C=1$ e $Z=0$ |
| `LS` | $\le$ (senza segno) | $C=0$ oppure $Z=1$ |
| `VS`/`VC` | overflow / no overflow | $V=1$ / $V=0$ |
| `AL` | sempre (default) | — |

> [!warning] Con segno vs senza segno
> `GT/LT/GE/LE` sono per numeri **con segno**; `HI/LO/HS/LS` per numeri **senza segno**.
