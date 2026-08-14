---
Materia: Architettura degli elaboratori
tags:
  - algebra_booleana
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 2.2.2-2.2.3'
Imparato: true
Ordine: 203
aliases:
  - SOP
  - POS
  - somma di prodotti
  - prodotto di somme
---
Da **qualunque** tabella di verità si può scrivere un'equazione booleana, in due modi
duali fra loro.

## Somma di prodotti (SOP — *sum-of-products*)
Si sommano (OR) i **mintermini** corrispondenti alle righe in cui l'uscita vale **1**.

Procedura:
1. individua le righe con uscita $Y = 1$;
2. per ognuna scrivi il mintermine (variabile diretta se il bit è 1, complementata se è 0);
3. metti in OR tutti i mintermini.

Esempio con $A, B$ e $Y=1$ nelle righe $AB = 01$ e $AB = 11$:
$$Y = \overline{A}B + AB$$

### Notazione sigma
$$Y = \Sigma(m_1, m_3)$$
oppure $Y = \Sigma m(1,3)$: i mintermini si numerano come il valore binario della riga.

## Prodotto di somme (POS — *product-of-sums*)
Si moltiplicano (AND) i **maxtermini** corrispondenti alle righe in cui l'uscita vale **0**.

Procedura:
1. individua le righe con uscita $Y = 0$;
2. per ognuna scrivi il maxtermine con la **polarità invertita** rispetto ai bit di riga
   (bit 0 → variabile diretta, bit 1 → variabile complementata);
3. metti in AND tutti i maxtermini.

Con lo stesso esempio ($Y=0$ nelle righe $AB=00$ e $AB=10$):
$$Y = (A+B)(\overline{A}+B)$$

### Notazione pi greco
$$Y = \Pi(M_0, M_2)$$

## Confronto
| | SOP | POS |
|---|---|---|
| si guardano le righe con | $Y=1$ | $Y=0$ |
| si usano | mintermini | maxtermini |
| si combinano con | OR | AND |
| polarità dei letterali | come i bit di riga | **invertita** rispetto ai bit di riga |

> [!tip] Quale conviene
> Se la funzione ha pochi 1 conviene SOP (poche righe da elencare); se ha pochi 0
> conviene POS. Entrambe le forme descrivono la **stessa** funzione.

## Perché "canonica"
Perché è la forma **standard** ottenibile meccanicamente dalla tabella di verità.
Non è (in generale) la forma **minima**: per minimizzare servono l'algebra di Boole o
le mappe di Karnaugh.

