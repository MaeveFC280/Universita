---
Materia: Basi di dati
tags:
  - algebra_relazionale
  - operatore_unario
Link risorse:
Libro: '"Sistemi di basi di dati. Fondamenti e complementi" Capitolo 6.1.1'
Imparato: true
Ordine: 1
aliases:
  - SELECT
---
L'operazione SELECT (selezione) seleziona un sottoinsieme di tuple che soddisfano una **condizione di selezione**. Il risultato di SELECT è una relazione con gli stessi attributi di R
$$
\sigma_{<\text{condizione di selezione}>}(R)
$$
Il simbolo $\sigma$ è usato per denotare il SELECT e la condizione è un'espressione booleana che utilizza gli attributi di R. La condizione può essere formato da un numero qualsiasi di clausole di forma:
$$
\text{<nome di attributo><operatore di confronto><valore costante>}
$$
Le clausole possono essere unite da AND, OR, NOT
Il grado della relazione risultante è identico a $\text{R}$, mentre il numero di tuple è minore o uguale. Ciò vuole dire che $|\sigma C\ (\text{R} )|\underline{<}|\text{R}|$ per ogni condizione $C$ 

La selezione è **commutativa**
$$
\sigma _{<\text{codnizione1}>}(\sigma_{<\text{condizione2}>}(R))=
\sigma _{<\text{codnizione2}>}(\sigma_{<\text{condizione1}>}(R))
$$
Inoltre è possibile unire le condizione direttamente con AND.

Questa operazione ha come corrispettivo in [[Introduzione SQL|SQL]] l'operazione [[SELECT]]