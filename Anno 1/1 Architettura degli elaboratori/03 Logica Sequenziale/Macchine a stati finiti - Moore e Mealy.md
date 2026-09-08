---
Materia: Architettura degli elaboratori
tags:
  - FSM
  - logica_sequenziale
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 3.4'
Imparato: true
Ordine: 307
aliases:
  - FSM
  - macchina a stati finiti
  - Moore
  - Mealy
---
## Struttura canonica
Un [[Circuiti combinatori e sequenziali|circuito sequenziale]] sincrono si può sempre disegnare nella forma di una **macchina a stati finiti** (*finite state machine*, **FSM**), composta da:
- un **registro di stato** a $k$ bit;
- la **logica combinatoria dello stato successivo**, che calcola $S'$ da $S$ e dagli ingressi;
- la **logica combinatoria di uscita**, che calcola le uscite.
Il nome deriva dal fatto che un circuito con $k$ registri può trovarsi in uno di un numero **finito** di stati, precisamente $2^k$.

## Moore e Mealy

|                                         | ***Moore***                                  | ***Mealy***                                            |
| --------------------------------------- | -------------------------------------------- | ------------------------------------------------------ |
| *Le uscite dipendono da*              | solo lo **stato** corrente                   | **stato** corrente E **ingressi** correnti             |
| *Nel diagramma le uscite si scrivono* | **dentro i cerchi** (negli stati)            | **sugli archi** (sulle transizioni)                    |
| *Reattività*                          | l'uscita cambia solo dopo il fronte di clock | l'uscita può cambiare subito con l'ingresso            |
| *Numero di stati*                     | in genere maggiore                           | in genere minore                                       |
| *Rischio di glitch sulle uscite*      | minore                                       | maggiore (l'uscita segue l'ingresso in modo asincrono) |

> [!tip] Come riconoscerle a vista
> - Diagramma: se le uscite sono **nei cerchi** è Moore, se sono **sugli archi** è Mealy.
> - Schema: se esiste un cammino combinatorio **diretto** dagli ingressi alle uscite (che non passa per il registro), è Mealy.

![[Macchine a stati finiti - Moore e Mealy-1787496585407.webp|800]]

## Diagramma di transizione di stato
- I **cerchi** rappresentano gli **stati**.
- Gli **archi** rappresentano le **transizioni** tra stati.
- Le transizioni avvengono **sul fronte di salita del [[Timing sequenziale - setup hold e clock skew|clock]]**; il clock **non si disegna**, perché in un circuito sequenziale sincrono è sempre presente per definizione.
- L'arco etichettato **Reset**, che entra in uno stato "venendo dal nulla", indica lo stato in cui il sistema entra al reset.
- Se da uno stato escono **più archi**, gli archi sono etichettati con l'ingresso che provoca la transizione.
- Se da uno stato esce **un solo arco**, quella transizione avviene **sempre**, indipendentemente dagli ingressi.
## Tabelle
- **Tabella di transizione di stato** (*state transition table*): per ogni combinazione di stato corrente e ingressi, indica lo stato successivo.
- **Tabella di uscita** (*output table*): per ogni stato (Moore) indica le uscite.
- Per una macchina di **Mealy** si scrive **una tabella combinata** di transizione e uscita, perché le uscite dipendono anche dagli ingressi.

![[Macchine a stati finiti - Moore e Mealy-1787496975053.webp]]
