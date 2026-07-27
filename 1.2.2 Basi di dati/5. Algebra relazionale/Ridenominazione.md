---
Materia: Basi di dati
tags:
  - algebra_relazionale
  - operatore_unario
Link risorse:
Libro: '"Sistemi di basi di dati. Fondamenti e complementi" Capitolo 6.1.3'
Imparato: true
Ordine: 4
aliases:
  - RENAME
---
In generale, è probabile che si vogliano eseguire **più operazioni** di algebra relazionale **una di seguito all’altra.** In questo caso è possibile scrivere le operazioni come una singola espressione dell’algebra relazionale nidificando le operazioni, oppure **applicare una operazione alla volta e creare relazioni che danno il risultato intermedio. In quest’ultimo caso occorre dare un nome alle relazioni che contengono i risultati intermedi.**
$$
\text{<NomeOperazione>}\leftarrow \text{<operazione>}
$$
L’operazione di assegnazione è indicata dalla freccia. 
È possibile anche definire un’operazione RENAME (ridenominazione) formale – che può r**idenominare il**
**nome di una relazione o i nomi degli attributi, o entrambi** – come operatore unario. L’operazione
RENAME generale, quando viene applicata a una relazione R di grado n, è indicata da una delle seguenti
tre forme:
$$
\rho _{S(B_{1},B_{2},\dots B_{n})}(R)
$$
$$
\rho_{S}(R)
$$
$$
\rho_{(B_{1},B_{2},\dots Bn)}
$$
Dove il simbolo ρ (rho) è usato per indicare l’operatore RENAME, $S$ è il nuovo nome della relazione, e $B_{1},B_{2},\dots Bn$  sono i nuovi nomi degli attributi. La prima espressione dà un nome nuovo sia alla relazione sia ai suoi attributi, la seconda solo alla relazione, la terza solo agli attributi.

In [[Introduzione SQL|SQL]] la ridenominazione avviene tramite [[RENAME|AS]]