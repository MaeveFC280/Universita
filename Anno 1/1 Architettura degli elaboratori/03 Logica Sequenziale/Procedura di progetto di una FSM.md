---
Materia: Architettura degli elaboratori
tags:
  - FSM
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 3.4.5'
Imparato: false
Ordine: 308
aliases:
  - progetto di una FSM
  - diagramma degli stati
---
Le [[Macchine a stati finiti - Moore e Mealy|macchine a stati finiti]] sono un modo potente e **sistematico** per progettare circuiti sequenziali partendo da una specifica scritta.

## I passi
1. **Identifica ingressi e uscite.**
2. **Abbozza un diagramma di transizione di stato.**
3. Scrivi le tabelle:
   - per una macchina di **Moore**:
     - tabella di transizione di stato,
     - tabella di uscita;
   - per una macchina di **Mealy**:
     - tabella **combinata** di transizione di stato e uscita.
1. **Scegli la codifica degli stati.**[[Codifica degli stati - binaria e one-hot|La scelta influenza il progetto hardware risultante]].
2. **Scrivi le equazioni booleane** per la logica dello stato successivo e per la
   logica di uscita.
3. **Disegna lo schema del circuito.**

## Dallo schema al diagramma
Ricavare il diagramma di transizione partendo da uno schema segue quasi esattamente il procedimento a rovescio:
1. **Esamina il circuito**, individuando ingressi, uscite e bit di stato.
2. **Scrivi le equazioni** dello stato successivo e delle uscite.
3. **Crea le tabelle** dello stato successivo e delle uscite.
4. **Riduci** la tabella dello stato successivo **eliminando gli stati non
   raggiungibili**.
5. **Assegna un nome** a ogni combinazione valida di bit di stato.
6. **Riscrivi** le tabelle usando i nomi degli stati.
7. **Disegna il diagramma** di transizione di stato.
8. **Descrivi a parole** cosa fa la FSM.

> [!important] Il passo 4 è quello che si dimentica
> Se la codifica usa $k$ bit ma gli stati validi sono meno di $2^k$, alcune
> combinazioni sono **non raggiungibili** e vanno eliminate prima di dare nomi agli
> stati. E il passo 8 è il vero controllo di correttezza: se non riesci a dire a parole
> cosa fa il circuito, probabilmente hai sbagliato qualcosa.

## Decomposizione di FSM complesse
Progettare FSM complesse è spesso più facile se si possono **scomporre in più macchine
più semplici che interagiscono**, in modo che le uscite di alcune siano gli ingressi di
altre. È un'applicazione di **gerarchia e modularità** al progetto sequenziale.

Esempio tipico: una FSM "principale" che gestisce le fasi di un'operazione, più un
**contatore** separato che conta i cicli e segnala alla principale quando ha finito.
Senza decomposizione, gli stati del contatore andrebbero replicati dentro la macchina
principale, moltiplicandone il numero.

