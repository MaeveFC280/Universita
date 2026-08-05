---
tags: [architettura, combinatoria, timing, cap2]
capitolo: 2
sezione: "2.9"
pagine_pdf: 104-108
---

# Timing combinatorio: ritardi e cammino critico

Fin qui si è parlato di **cosa** fa un circuito. Ora di **quando** lo fa: la specifica
temporale. In pratica è ciò che determina la frequenza di clock raggiungibile.

## Le due grandezze
Un'uscita richiede tempo per reagire a un cambio dell'ingresso. Si misura il ritardo
dal **punto al 50%** del segnale di ingresso al punto al 50% del segnale di uscita.

| Grandezza | Simbolo | Definizione |
|---|---|---|
| **Ritardo di propagazione** | $t_{pd}$ | tempo **massimo** perché l'uscita si stabilizzi dopo un cambio dell'ingresso |
| **Ritardo di contaminazione** | $t_{cd}$ | tempo **minimo** perché l'uscita **inizi** a cambiare dopo un cambio dell'ingresso |

Sono un limite **superiore** e uno **inferiore**: non due misure della stessa cosa.

## Cammino critico e cammino breve
- **Cammino critico** (*critical path*): il percorso **più lungo**, e quindi più lento,
  dall'ingresso all'uscita. Determina $t_{pd}$ e **limita la velocità** del circuito.
- **Cammino breve** (*short path*): il percorso **più corto**, e quindi più veloce.
  Determina $t_{cd}$.

$$t_{pd} = \sum_{\text{cammino critico}} t_{pd,\text{elemento}} \qquad
t_{cd} = \sum_{\text{cammino breve}} t_{cd,\text{elemento}}$$

Esempio: circuito con due AND in serie seguiti da un OR sul cammino lungo, e un solo
AND sul cammino corto:
$$t_{pd} = 2t_{pd-AND} + t_{pd-OR} \qquad t_{cd} = t_{cd-AND}$$

## Cause fisiche del ritardo
- tempo di **carica delle capacità** del circuito;
- **velocità della luce** nei collegamenti (non trascurabile su chip grandi).

## Perché il ritardo non è un numero unico
- **ritardi di salita e di discesa diversi** (rising/falling delay);
- **temperatura**: i circuiti rallentano da caldi e accelerano da freddi;
- **ingressi/uscite multiple**, alcuni più veloci di altri;
- variazioni di processo produttivo e di tensione di alimentazione.

Per questo i costruttori forniscono nei **data sheet** i limiti di $t_{pd}$ e $t_{cd}$
nel caso peggiore, ed è su quelli che si progetta.

## Da ricordare
- $t_{pd}$ = massimo, dal cammino **critico**. $t_{cd}$ = minimo, dal cammino **breve**.
- Il cammino critico limita la frequenza di clock del sistema.
- I ritardi sono intervalli, non valori esatti: si progetta sul caso peggiore.

## Domande flash
1. Se ogni porta ha $t_{pd}=100$ ps, quanto vale $t_{pd}$ di una catena di 4 porte?
2. Perché serve conoscere $t_{cd}$ e non basta $t_{pd}$?
   (risposta → [[Timing sequenziale - setup hold e clock skew]])

Collegato a: [[Glitch]]
