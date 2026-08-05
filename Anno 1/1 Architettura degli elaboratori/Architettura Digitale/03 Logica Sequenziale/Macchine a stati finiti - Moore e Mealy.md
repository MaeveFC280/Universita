---
tags: [architettura, sequenziale, fsm, cap3]
capitolo: 3
sezione: "3.4"
pagine_pdf: 139-149
aliases: [FSM, macchine a stati]
---

# Macchine a stati finiti: Moore e Mealy

## Struttura canonica
Un circuito sequenziale sincrono si può sempre disegnare nella forma di una
**macchina a stati finiti** (*finite state machine*, **FSM**), composta da:
- un **registro di stato** a $k$ bit;
- la **logica combinatoria dello stato successivo**, che calcola $S'$ da $S$ e dagli
  ingressi;
- la **logica combinatoria di uscita**, che calcola le uscite.

Il nome deriva dal fatto che un circuito con $k$ registri può trovarsi in uno di un
numero **finito** di stati, precisamente $2^k$.

## Le due classi
| | **Moore** | **Mealy** |
|---|---|---|
| Le uscite dipendono da | **solo lo stato corrente** | **stato corrente E ingressi correnti** |
| Nel diagramma le uscite si scrivono | **dentro i cerchi** (negli stati) | **sugli archi** (sulle transizioni) |
| Reattività | l'uscita cambia solo dopo il fronte di clock | l'uscita può cambiare **subito** con l'ingresso |
| Numero di stati | in genere **maggiore** | in genere **minore** |
| Rischio di glitch sulle uscite | minore | maggiore (l'uscita segue l'ingresso in modo asincrono) |

> [!tip] Come riconoscerle a vista
> Guarda il diagramma: se le uscite sono **nei cerchi** è Moore, se sono **sugli archi**
> è Mealy. Sullo schema: se esiste un cammino combinatorio **diretto** dagli ingressi
> alle uscite (che non passa per il registro), è Mealy.

## Diagramma di transizione di stato
- I **cerchi** rappresentano gli **stati**.
- Gli **archi** rappresentano le **transizioni** tra stati.
- Le transizioni avvengono **sul fronte di salita del clock**; il clock **non si
  disegna**, perché in un circuito sequenziale sincrono è sempre presente per
  definizione.
- L'arco etichettato **Reset**, che entra in uno stato "venendo dal nulla", indica lo
  stato in cui il sistema entra al reset.
- Se da uno stato escono **più archi**, gli archi sono etichettati con l'ingresso che
  provoca la transizione.
- Se da uno stato esce **un solo arco**, quella transizione avviene **sempre**,
  indipendentemente dagli ingressi.

## Tabelle
- **Tabella di transizione di stato** (*state transition table*): per ogni combinazione
  di stato corrente e ingressi, indica lo stato successivo.
- **Tabella di uscita** (*output table*): per ogni stato (Moore) indica le uscite.
- Per una macchina di **Mealy** si scrive **una tabella combinata** di transizione e
  uscita, perché le uscite dipendono anche dagli ingressi.

## Da ricordare
- $k$ registri ⇒ fino a $2^k$ stati.
- Moore: uscite = f(stato). Mealy: uscite = f(stato, ingressi).
- Nel diagramma: Moore → uscite nei cerchi; Mealy → uscite sugli archi.
- Un solo arco uscente = transizione incondizionata.

## Domande flash
1. Una FSM di Mealy con 3 stati equivale a una di Moore con quanti stati?
   (dipende: in generale servono più stati per "ricordare" l'ingresso)
2. Perché il clock non appare nel diagramma di transizione?

Collegato a: [[Procedura di progetto di una FSM]] · [[Codifica degli stati - binaria e one-hot]]
