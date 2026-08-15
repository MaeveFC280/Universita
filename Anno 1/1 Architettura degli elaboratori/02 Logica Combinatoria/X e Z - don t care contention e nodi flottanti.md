---
Materia: Architettura degli elaboratori
tags:
  - logica_combinatoria
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 2.6'
Imparato: true
Ordine: 207
aliases:
  - don't care
  - contention
  - nodo flottante
  - tri-state
---
[[Assiomi e teoremi dell algebra di Boole|algebra di Boole]] conosce solo 0 e 1, ma i circuiti reali hanno anche valori **illegali** e **flottanti**. Si indicano con **X** e **Z**.
## X — valore illegale o sconosciuto
Il simbolo **X** indica che un nodo ha un valore **sconosciuto o illegale**.
Tipicamente accade per **contention** (*contesa*): un nodo è pilotato contemporaneamente verso 1 e verso 0 da due elementi diversi.
- È considerato un **errore** e va evitato.
- La tensione effettiva sul nodo in contesa è un valore intermedio, che dipende dalla
  forza relativa dei due driver; **spesso, ma non sempre**, cade nella zona proibita.
- La contention può inoltre far scorrere **corrente elevata** tra alimentazione e
  massa, con surriscaldamento e possibile danneggiamento del chip.

> [!warning] Doppio uso della lettera X
> **X** significa anche **don't care** nelle tabelle di verità (vedi sotto). È un
> simbolo sovraccarico: il significato va dedotto dal contesto. Nel testo del libro
> gli X "illegali" sono in genere sui **nodi/uscite**, gli X "don't care" negli
> **ingressi** delle tabelle.

## X — don't care
Un **don't care** indica che il valore è **indifferente**:
- negli **ingressi** di una tabella di verità: quella variabile non influisce sul risultato per quella riga;
- nelle **uscite**: quella combinazione di ingressi non si verificherà mai, oppure il valore d'uscita non ci interessa.
I don't care sono preziosi: nelle[[Mappe di Karnaugh| mappe di Karnaugh]] possono essere trattati come 0 o come 1, a seconda di ciò che conviene, permettendo una minimizzazione più spinta.
## Z — nodo flottante
Il simbolo **Z** indica un nodo **non pilotato**, né HIGH né LOW: è **flottante** (*floating*), in **alta impedenza**, *hi-Z*.
- Un nodo flottante **non è necessariamente un errore**: è il funzionamento normale di
  un bus condiviso o di un'uscita three-state.
- Ma la sua tensione è imprevedibile e sensibile al rumore, quindi un ingresso
  flottante è un problema.
## Il buffer three-state (tristate)
Ha un ingresso dati $A$, un ingresso di **enable** $E$ e un'uscita $Y$:
- se $E = 1$ → si comporta da buffer, $Y = A$;
- se $E = 0$ → l'uscita è **flottante (Z)**, il buffer è "staccato".

Uso tipico: **bus condiviso**. Più driver pilotano lo stesso bus, ma **al massimo uno
per volta** ha l'enable attivo; gli altri stanno in Z. È così che si evita la contention.
