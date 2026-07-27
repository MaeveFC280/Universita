---
Materia: Basi di dati
tags:
  - progettazione_concettuale
  - ER
Libro: '"Sistemi di basi di dati. Fondamenti e complementi" Capitolo 4'
Link risorse:
Imparato: true
aliases:
Ordine: 2
---
I modelli ER si limitano a fornire uno schema generico dei database, mentre i modelli EER offrono **una rappresentazione più dettagliata delle informazioni**
## Da UML a EER
EER aggiunge:
- Il concetto di **sottoclasse/superclasse** (espresso come tipo/sottotipo)
- L’**[[Gerarchie in EER|ereditarietà]]** di attributi e relazioni
- Il concetto di **categoria/unione** 
- La [[Gerarchie in EER|specializzazione/generalizzazione]].
Alcune indicazioni:
- [[Gerarchie in EER|La lettera d indica una specializzazione disgiunta]];
- [[Gerarchie in EER|La lettera o indica una specializzazione overlapping]];
- [[Gerarchie in EER|La doppia linea verso la superclasse indica specializzazione totale*];
- [[Gerarchie in EER|La linea singola indica specializzazione parziale]].
## Reticolo di specializzazione
- Quando c’è **ereditarietà multipla** non si ha più una semplice gerarchia ad albero, ma un **reticolo** di gerarchie di specializzazione.
- Le classi poste più in basso ereditano **una sola volta** gli attributi delle classi più generali di cui sono specializzazioni.
![[Screenshot 2026-06-11 alle 09.29.04.png]]