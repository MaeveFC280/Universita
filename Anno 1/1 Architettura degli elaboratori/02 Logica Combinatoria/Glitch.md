---
Materia: Architettura degli elaboratori
tags:
  - timing
  - logica_combinatoria
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 2.9.2'
Imparato: false
Ordine: 212
aliases:
  - glitch
  - alea
---

# Glitch

## Definizione
Un **glitch** (o *hazard*) si verifica quando **una singola transizione di un ingresso
provoca più transizioni dell'uscita**, prima che questa si stabilizzi sul valore
finale corretto.

## Perché avviene
Perché i vari cammini attraverso il circuito hanno **ritardi diversi**. Se il cambio di
una variabile "spegne" un implicante prima che ne "accenda" un altro, l'uscita passa
momentaneamente per un valore sbagliato.

## Come si riconoscono sulla K-map
> Un glitch può verificarsi quando il cambio di **una sola variabile** attraversa il
> confine tra **due cerchi diversi** della mappa di Karnaugh.

Se invece il cambiamento resta **all'interno di un unico cerchio**, non c'è glitch: quel
solo implicante copre entrambe le configurazioni e mantiene l'uscita stabile.

## Come si eliminano (se serve)
Aggiungendo un implicante **ridondante** che "copre a cavallo" del confine tra i due
cerchi, così che nessuna transizione singola scavalchi un confine scoperto.
Il costo è hardware in più, per una funzione logicamente già corretta.

## L'atteggiamento giusto
> [!important] Il punto chiave del libro
> Lo scopo di studiare i glitch **non è eliminarli**, ma **essere consapevoli che
> esistono**. In un circuito **sincrono** i glitch sono innocui: si aspetta che il
> ritardo di propagazione sia trascorso prima di campionare il segnale sul fronte di
> clock, e a quel punto l'uscita è già stabile.

Il glitch diventa un problema serio solo in casi specifici:
- circuiti **asincroni**;
- segnali usati come **clock** o come **reset asincrono**;
- uscite che pilotano direttamente qualcosa di sensibile ai transitori.

## Da ricordare
- Glitch = transizioni multiple dell'uscita per un solo cambio di ingresso.
- Sulla K-map: transizione che attraversa il confine tra due cerchi.
- Nei sistemi sincroni sono tollerati: conta solo il valore al fronte di clock.

## Domande flash
1. Perché un glitch è innocuo in un circuito sincrono?
2. Come si elimina un glitch con un implicante ridondante, e a che prezzo?
