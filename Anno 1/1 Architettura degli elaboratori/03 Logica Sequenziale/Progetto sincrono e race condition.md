---
Materia: Architettura degli elaboratori
tags:
  - logica_sequenziale
  - timing
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 3.3'
Imparato: false
Ordine: 306
aliases:
  - progetto sincrono
  - race condition
---
## Il problema dei circuiti asincroni
La definizione di circuito sequenziale è per esclusione: sono sequenziali **tutti** i
circuiti che non sono combinatori, cioè quelli le cui uscite non si possono determinare
guardando solo gli ingressi correnti.

I circuiti sequenziali arbitrari possono comportarsi molto male:
- **circuiti instabili o astabili**: non hanno stati stabili e oscillano
  indefinitamente (es. un anello di tre inverter);
- **race condition** (*condizione di corsa*): il circuito **funziona o fallisce a
  seconda di quali porte sono più lente di altre**. È un guasto che dipende dai
  ritardi fisici, quindi imprevedibile, sensibile alla temperatura, difficilissimo da
  diagnosticare in laboratorio.

> I circuiti asincroni sono **tristemente noti** per le race condition.

## Cammini ciclici
Il tratto comune di questi circuiti è la presenza di **cammini ciclici** (*cyclic
paths*): anelli in cui le uscite sono riportate direttamente sugli ingressi. Sono
sequenziali proprio per questo, e sono la sede di corse e instabilità.

## La soluzione: rompere gli anelli con i registri
Per evitare questi problemi, il progettista **rompe i cammini ciclici inserendo
registri** da qualche parte nell'anello.

I registri contengono lo **stato del sistema**, che cambia **solo sul fronte di clock**:
si dice quindi che lo stato è **sincronizzato al clock**. Se il clock è
sufficientemente lento perché tutti gli ingressi dei registri si stabilizzino, tutte le
race condition sono eliminate.

## Definizione: circuito sequenziale sincrono
Un circuito è **sequenziale sincrono** se rispetta **tutte** queste regole di
composizione:

1. Ogni elemento del circuito è **o un registro o un circuito combinatorio**.
2. **Almeno un** elemento è un registro.
3. **Tutti i registri ricevono lo stesso segnale di clock**.
4. **Ogni cammino ciclico contiene almeno un registro**.

I circuiti sequenziali che non sono sincroni si dicono **asincroni**.

## Specifica di un circuito sequenziale sincrono
Un circuito sequenziale sincrono ha:
- un insieme finito di **stati discreti** $\{S_0, S_1, \dots, S_{k-1}\}$;
- una **specifica funzionale**: lo stato successivo e le uscite come funzione dello
  stato corrente e degli ingressi;
- una **specifica temporale**, costituita da:
  - $t_{pcq}$ (*propagation clock-to-Q*): limite **superiore** al tempo dal fronte di
    salita del clock fino alla stabilizzazione dell'uscita;
  - $t_{ccq}$ (*contamination clock-to-Q*): limite **inferiore**, tempo minimo prima che
    l'uscita **inizi** a cambiare dopo il fronte.

Il flip-flop è il **più semplice** circuito sequenziale sincrono: un ingresso $D$, un
clock, un'uscita $Q$, due stati $\{0, 1\}$.

## Notazione
Si indica con $S$ lo stato corrente e con $S'$ (*S primo*) lo **stato successivo**.

## Nota sull'asincrono
In teoria il progetto asincrono è **più generale** di quello sincrono, perché il timing
non è vincolato da registri clocchati, e in linea di principio può essere più veloce.
In pratica è così difficile da rendere corretto che quasi tutti i sistemi reali sono
sincroni.

## Da ricordare
- Le **4 regole** di composizione sincrona (in particolare: ogni ciclo ha un registro,
  tutti i registri hanno lo stesso clock).
- Race condition = corretto funzionamento dipendente dai ritardi delle porte.
- $t_{pcq}$ = max, $t_{ccq}$ = min, dal fronte di clock all'uscita.
- $S'$ = stato successivo.

## Domande flash
1. Un circuito con due registri comandati da clock diversi è sincrono?
2. Perché inserire un registro in un anello elimina la race condition?

Collegato a: [[Macchine a stati finiti - Moore e Mealy]] · [[Timing sequenziale - setup hold e clock skew]]
