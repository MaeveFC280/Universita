---
Materia: Architettura degli elaboratori
tags:
  - ARM
  - assembly
  - flusso_di_controllo
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 6.3.3'
Imparato: true
Ordine: 609
aliases:
  - cicli
  - while
  - for
---
I **cicli** eseguono ripetutamente un blocco di codice in base a una [[Branch ed esecuzione condizionale|condizione]].

## while
Un ciclo `while` esegue ripetutamente il blocco **finché** la condizione **non** è più soddisfatta. Come per l'`if`, il codice assembly verifica la **condizione opposta** a quella del codice di alto livello.

```c
int pow = 1;
int x = 0;
while (pow != 128) {
    pow = pow * 2;
    x = x + 1;
}
```
```armasm
        ; R0 = pow, R1 = x
        MOV  R0, #1
        MOV  R1, #0
while
        CMP  R0, #128       ; verifica la condizione
        BEQ  done           ; se pow == 128 ESCI  <-- condizione opposta
        LSL  R0, R0, #1     ; pow = pow * 2
        ADD  R1, R1, #1     ; x = x + 1
        B    while          ; torna a verificare
done
```

Struttura generale:
```
etichetta_test
    <verifica la condizione>
    B<cond_opposta>  fine
    <corpo>
    B  etichetta_test
fine
```

## do / while
Il corpo si esegue **almeno una volta**, poi si verifica la condizione. È più efficiente in assembly, perché serve **un solo branch** per iterazione anziché due.

```
loop
    <corpo>
    <verifica>
    B<cond>  loop
```

## for
Un pattern estremamente comune è: **inizializzare** una variabile prima del ciclo, **verificarla** nella condizione e **modificarla** a ogni iterazione.
- l'**inizializzazione** si esegue **una volta**, prima che il ciclo cominci;
- la **condizione** si verifica **all'inizio** di ogni iterazione;
- l'**operazione** si esegue **alla fine** di ogni iterazione.

```c
int sum = 0;
for (i = 0; i != 10; i = i + 1)
    sum = sum + i;
```
```armasm
    ; R0 = i, R1 = sum
    MOV  R1, #0        ; sum = 0
    MOV  R0, #0        ; inizializzazione: i = 0
for
    CMP  R0, #10       ; condizione
    BEQ  done          ; esci se i == 10
    ADD  R1, R1, R0    ; corpo: sum = sum + i
    ADD  R0, R0, #1    ; operazione: i = i + 1
    B    for
done
```

> [!tip] Contare a scendere
> Se l'ordine delle iterazioni è irrilevante, contare **verso zero** permette di sfruttare il [[Flag di condizione e istruzione CMP|flag Z]] e risparmiare il `CMP`: ``` MOV  R0, #10 loop SUBS R0, R0, #1     ; decrementa E aggiorna i flag ...corpo... BNE  loop           ; nessun CMP necessario ```
