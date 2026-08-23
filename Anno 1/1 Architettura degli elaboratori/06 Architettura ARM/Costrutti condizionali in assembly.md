---
Materia: Architettura degli elaboratori
tags:
  - ARM
  - assembly
  - flusso_di_controllo
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 6.3.3'
Imparato: true
Ordine: 608
aliases:
  - if else
  - switch case
---
Le istruzioni [[Branch ed esecuzione condizionale|condizionali]] sono i mattoni con cui si traducono i costrutti dei
linguaggi di alto livello.

> [!important] Pensare al contrario
> **Il codice assembly verifica la condizione OPPOSTA a quella del codice di alto livello.**
> In C si dice "**se** la condizione è vera, esegui il blocco". In assembly si dice "**se** la condizione è **falsa**, **salta oltre** il blocco".

## if
```c
if (i == j)
    f = g + h;
f = f - i;
```
``` armasm
    ; R0=f, R1=g, R2=h, R3=i, R4=j
    CMP  R3, R4        ; confronta i e j
    BNE  L1            ; se i != j SALTA il blocco  <-- condizione opposta
    ADD  R0, R1, R2    ; f = g + h
L1
    SUB  R0, R0, R3    ; f = f - i
```

### Variante con esecuzione condizionale
Per blocchi brevissimi si evita il branch:
```armasm
    CMP    R3, R4
    ADDEQ  R0, R1, R2  ; eseguita solo se i == j
    SUB    R0, R0, R3
```

## if / else
Eseguono **uno di due blocchi** in base a una [[Branch ed esecuzione condizionale|condizione]]. Serve un branch
**incondizionato** alla fine del primo blocco, per scavalcare il secondo.

```c
if (i == j)
    f = g + h;
else
    f = f - i;
```
```
    CMP  R3, R4
    BNE  L1            ; se i != j vai all'else
    ADD  R0, R1, R2    ; blocco if
    B    L2            ; salta l'else  <-- FONDAMENTALE
L1
    SUB  R0, R0, R3    ; blocco else
L2
```

> [!warning] L'errore più comune
> Dimenticando il `B L2` alla fine del blocco `if`: il programma eseguirebbe **entrambi** i blocchi.

## switch / case
Eseguono uno di **più** blocchi in base al valore di una variabile. Si traducono con una **catena di confronti** (equivalente a una serie di `if/else if`):

```c
switch (amount) {
  case 20:  fee = 2;  break;
  case 50:  fee = 3;  break;
  case 100: fee = 5;  break;
  default:  fee = 0;
}
```
```
    CMP  R0, #20
    BNE  case50
    MOV  R1, #2
    B    done
case50
    CMP  R0, #50
    BNE  case100
    MOV  R1, #3
    B    done
case100
    CMP  R0, #100
    BNE  default
    MOV  R1, #5
    B    done
default
    MOV  R1, #0
done
```

> [!tip] L'alternativa efficiente: jump table
> Con molti casi contigui, la catena di confronti è lenta ($O(n)$). Si usa allora una **tabella di salto** (*jump table*): un array in memoria che contiene gli indirizzi dei vari blocchi, indicizzato dal valore della variabile. Si accede in tempo **costante** con un `LDR` e un salto.

