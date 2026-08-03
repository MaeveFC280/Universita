---
Materia: Basi di dati
tags:
  - progettazione_concettuale
  - UML
Link risorse:
Imparato: true
Ordine: 2
aliases:
---
Sia in UML, sia in [[Gerarchie in EER|ER]] è possibile indicare molteplici rapporti di tipo gerarchico tra le entità 
## Aggregazione
 La classe A è composta da oggetti di B, componente.
B esiste anche senza A
![[Pasted image 20260610205357.png|Aggregazione]]
## Composizione
 Se cancello A cancello B
C’è un vincolo sul comportamento della base di dati
![[Pasted image 20260610205450.png|Composizione]]
## Generalizzazione 
A partire da classi più specializzate **si risale a una classe più generale** che raccoglie ciò che hanno in comune.
## Specializzazione 
La specializzazione è come un **raffinamento concettuale**: si parte da una classe più generale e si distinguono delle **sottoclassi** più specifiche.
La **classe specializzata** possiede i suoi attributi propri ma **eredita** anche gli attributi della classe generale; la stessa ereditarietà vale anche per le **associazioni**. Inoltre, ogni istanza della sottoclasse è anche istanza della superclasse, ma non viceversa.

Una specializzazione ha senso solo quando esistono caratteristiche specifiche della classe figlia, in termini di attributi o metodi, che giustificano la separazione.
## Associazioni totali e parziali
-  **Totale**: ogni istanza della classe generale deve appartenere ad una delle sottoclassi
- **Parziale**: ogni istanza della classe generale può non appartenere ad una sottoclasse
## Disgiunzione e overlapping
 - **Disgiunta**: ogni istanza della classe generale può appartenere al più a una sola sottoclasse
 - **Overlapping**: una stessa istanza può appartenere contemporaneamente a più sottoclassi.

Nel caso di ereditarietà multipla di parla di [[Reticolo di specializzazione]]
Le classi in basso ereditano una sola volta gli attributi delle classi generalizzate.