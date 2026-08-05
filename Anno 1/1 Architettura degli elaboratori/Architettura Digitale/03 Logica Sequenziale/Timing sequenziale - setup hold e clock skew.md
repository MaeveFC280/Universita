---
tags: [architettura, sequenziale, timing, cap3]
capitolo: 3
sezione: "3.5"
pagine_pdf: 157-173
---

# Timing sequenziale: setup, hold e clock skew

## Campionamento e finestra di apertura
Un flip-flop copia $D$ su $Q$ sul fronte di salita del clock: si dice che
**campiona** (*samples*) $D$ sul fronte.

Perché il campionamento funzioni, il segnale $D$ deve essere **stabile** in un intorno
del fronte di clock, detto **finestra di apertura** (*aperture time*). Fuori da quella
finestra il segnale può glitchare e oscillare liberamente: non ci interessa.

## I quattro tempi del flip-flop
| Simbolo | Nome | Definizione |
|---|---|---|
| $t_{setup}$ | tempo di **setup** | tempo **prima** del fronte in cui $D$ deve essere già stabile |
| $t_{hold}$ | tempo di **hold** | tempo **dopo** il fronte in cui $D$ deve rimanere stabile |
| $t_{pcq}$ | *propagation clock-to-Q* | tempo **massimo** dal fronte alla stabilizzazione di $Q$ |
| $t_{ccq}$ | *contamination clock-to-Q* | tempo **minimo** dal fronte al primo cambiamento di $Q$ |

La finestra di apertura è $t_{setup} + t_{hold}$ a cavallo del fronte.

## La disciplina dinamica
Grazie a questa disciplina il tempo si può pensare **a unità discrete**, i **cicli di
clock**. Invece di scrivere $A(t)$, il valore del segnale $A$ all'istante $t$
(un numero reale), si scrive $A[n]$: il valore di $A$ **alla fine dell'$n$-esimo ciclo**,
con $n$ intero. Questa è l'astrazione che rende trattabile il progetto digitale.

## Vincolo di setup (limita la frequenza)
Il dato deve partire da un registro, attraversare la logica combinatoria e arrivare
stabile all'ingresso del registro successivo **prima** della finestra di setup:

$$T_c \ge t_{pcq} + t_{pd} + t_{setup}$$

Riorganizzando, il ritardo massimo ammesso per la logica combinatoria è:

$$t_{pd} \le T_c - (t_{pcq} + t_{setup})$$

Il termine $t_{pcq} + t_{setup}$ è l'**overhead di sequenziamento** (*sequencing
overhead*): tempo di ciclo speso nel flip-flop e non nel calcolo utile.

> [!info] Come si "aggiusta" una violazione di setup
> Si può **rallentare il clock** (aumentare $T_c$), oppure **spezzare la logica** con
> registri intermedi (pipelining → [[Parallelismo latenza e throughput]]).

## Vincolo di hold (indipendente dalla frequenza!)
Il dato non deve arrivare al registro successivo **troppo presto**, cioè prima che sia
scaduta la finestra di hold:

$$t_{ccq} + t_{cd} \ge t_{hold} \qquad\Longleftrightarrow\qquad t_{cd} \ge t_{hold} - t_{ccq}$$

> [!warning] Il punto che si sbaglia in esame
> Il vincolo di hold **non contiene $T_c$**: rallentare il clock **non risolve** una
> violazione di hold. L'unico rimedio è **ridisegnare il circuito**, tipicamente
> aggiungendo buffer di ritardo sul cammino breve.

## Clock skew
Nella realtà il clock non arriva **nello stesso istante** a tutti i registri: la
differenza si chiama **clock skew** ($t_{skew}$), causata da lunghezze diverse dei fili,
carichi diversi, e dal ritardo dell'albero di distribuzione del clock.

Nel caso peggiore entrambi i vincoli si irrigidiscono:

$$T_c \ge t_{pcq} + t_{pd} + t_{setup} + t_{skew}$$
$$t_{cd} \ge t_{hold} + t_{skew} - t_{ccq}$$

## Metastabilità (cenni)
Se $D$ **viola** la finestra di apertura, l'uscita può entrare in uno stato
**metastabile**: una tensione intermedia, né 0 né 1, per un tempo **non limitato a
priori**. Il flip-flop si risolve dopo un **tempo di risoluzione** che è una variabile
**casuale**: si può rendere la probabilità di errore arbitrariamente piccola
attendendo più a lungo, ma non nulla.

Problema tipico dell'ingresso di segnali **asincroni** (dal mondo esterno, o da un
dominio di clock diverso). Rimedio: un **sincronizzatore**, tipicamente due flip-flop
in cascata, che dà al segnale un ciclo intero per risolversi.

## Da ricordare
- Finestra di apertura = $t_{setup} + t_{hold}$ attorno al fronte.
- **Setup**: $T_c \ge t_{pcq} + t_{pd} + t_{setup}$ → dipende dal clock.
- **Hold**: $t_{cd} \ge t_{hold} - t_{ccq}$ → **non** dipende dal clock.
- Lo skew peggiora entrambi i vincoli.
- Segnali asincroni → sincronizzatore a due flip-flop.

## Domande flash
1. Con $t_{pcq}=50$ ps, $t_{setup}=60$ ps, $t_{pd}=800$ ps, qual è il $T_c$ minimo?
2. Il circuito viola l'hold: rallentare il clock aiuta? Perché?
3. Che cos'è l'overhead di sequenziamento?
