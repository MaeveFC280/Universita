---
Materia: Architettura degli elaboratori
tags:
  - logica_sequenziale
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 3.2.4-3.2.5'
Imparato: false
Ordine: 304
aliases:
  - flip-flop D
  - registro
  - master-slave
---
## Struttura master-slave
Un **flip-flop D** si costruisce con **due latch D in cascata**, comandati da clock
**complementari**:
- il primo latch, $L_1$, è detto **master**;
- il secondo, $L_2$, è detto **slave**;
- il nodo intermedio si chiama $N_1$.

## Funzionamento
- **$CLK = 0$**: il master è **trasparente**, lo slave è **opaco**. Il valore presente su
  $D$ si propaga fino a $N_1$, ma non oltre: $Q$ resta fermo.
- **$CLK = 1$**: il master diventa **opaco**, lo slave diventa **trasparente**. Il valore
  congelato in $N_1$ passa a $Q$, ma nessun nuovo dato può entrare nel master.

Risultato: il valore che si trovava su $D$ **immediatamente prima del fronte di salita**
del clock viene copiato su $Q$ subito dopo il fronte. In tutto il resto del ciclo, $Q$
resta stabile.

## Terminologia
- Si chiama **flip-flop attivato sul fronte** (*edge-triggered*), **flip-flop D**,
  **flip-flop master-slave**, o semplicemente **registro a 1 bit**.
- Nel simbolo, il **triangolo** indica un ingresso di clock sensibile al fronte.
- La distinzione dei ruoli è netta: **$D$ specifica quale sarà il nuovo stato, il fronte
  di clock indica quando lo stato deve essere aggiornato.**

> [!important] Latch vs flip-flop
> | | latch D | flip-flop D |
> |---|---|---|
> | sensibile a | **livello** del clock | **fronte** del clock |
> | trasparenza | sì, mentre $CLK=1$ | mai |
> | il dato passa | in qualunque istante con $CLK$ alto | solo sul fronte |
>
> Il flip-flop è quello che rende possibile il progetto sincrono, perché garantisce che
> lo stato cambi in **istanti discreti e noti**.

## Registri
Un **registro a $N$ bit** è un banco di $N$ flip-flop che condividono lo **stesso
ingresso di clock**, così che **tutti i bit si aggiornano nello stesso istante**.

I registri sono l'elemento di stato fondamentale nei sistemi digitali: contengono lo
stato di macchine a stati finiti, i dati intermedi nelle pipeline, il *register file*
del processore.

## Da ricordare
- Flip-flop = 2 latch, clock complementari, master + slave.
- Campiona $D$ sul **fronte di salita** del clock.
- Registro a $N$ bit = $N$ flip-flop con clock comune.

## Domande flash
1. Cosa contiene $N_1$ quando $CLK=1$?
2. Perché un flip-flop non è mai trasparente?
3. Come si distinguono a colpo d'occhio i simboli di latch e flip-flop?
