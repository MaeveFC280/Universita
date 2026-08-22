---
Materia: Architettura degli elaboratori
tags:
  - logica_sequenziale
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 3.2.1'
Imparato: true
Ordine: 301
aliases:
  - bistabile
  - elemento di memoria
---
## Dal combinatorio al sequenziale
Le uscite della logica sequenziale dipendono dai valori **correnti e precedenti** degli ingressi: la logica sequenziale ha **memoria**.

Non serve ricordare tutta la storia passata: si distilla l'informazione precedente in una quantità ridotta detta **stato** del sistema. Lo stato di un circuito sequenziale digitale è un insieme di bit, detti **bit di stato** o **variabili di stato**, che contengono tutto ciò che serve a spiegare il comportamento futuro del circuito.
## L'elemento bistabile
Il mattone fondamentale della memoria è l'**elemento bistabile**: un elemento con **due stati stabili**.

Realizzazione minima: **due inverter incrociati** (*cross-coupled inverters*), dove l'ingresso di $I_1$ è l'uscita di $I_2$ e viceversa.
![[Elementi bistabili-1787398631387.webp|323x257]]

- **Caso I: $Q = 0$**
	$\overline{Q}$ vale 1, che riportato in ingresso a $I_1$ produce 0 su $Q$. Coerente con l'ipotesi iniziale → lo stato è **stabile**.
- **Caso II: $Q = 1$**
	$\overline{Q}$ vale 0, che riportato in ingresso produce 1 su $Q$. Anche questo è coerente → **stabile**.

Poiché ci sono due stati stabili, il circuito si dice **bistabile**.
## Quanta informazione memorizza
Un elemento con $N$ stati stabili trasporta $\log_2 N$ bit di informazione. Un elemento **bistabile** memorizza quindi **un bit**, e lo stato è contenuto nel nodo $Q$ (o equivalentemente in $\overline{Q}$, che ne è il complemento).
## Il limite
L'elemento bistabile *puro* **non ha ingressi di controllo**: memorizza un bit, ma non c'è modo di decidere *quale* bit. Da qui la necessità di [[Latch SR|latch]] e [[Flip-flop D e registri|flip-flop D]], che aggiungono ingressi per controllare il valore della variabile di stato.

> [!info] Osservazione sull'accensione
> Il valore in cui si assesta un elemento bistabile all'accensione è imprevedibile, perché dipende dal rumore e dai transitori di alimentazione. Da qui l'esigenza di ingressi di **reset** ([[Flip-flop con enable e reset]]).

