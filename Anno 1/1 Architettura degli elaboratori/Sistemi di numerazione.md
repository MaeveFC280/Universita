---
Materia: Architettura degli elaboratori
tags:
  - Binario
Link risorse: https://youtu.be/QZwneRb-zqA?si=cP0ZyNW7ELlDQNCI&t=306
Libro: '"Digital Design and Computer Architecture"'
Imparato: false
Ordine: 3
aliases:
  - sistema binario
---
# Numerazione binaria
Nel sistema decimale sono presenti 10 cifre (0,1,2,3,4,5,6,7,8,9). Ogni numero posto a sinistra del primo vale tale numero **dieci volte tanto** (10: l'uno posto a sinistra vale 1 moltiplicato per 10).
Nel sistema binario le cifre sono 0 e 1 e i numeri a sinistra valgono **il doppio**. 
![[Sistemi di numerazione-1785675970006.webp|700]]
Nei numeri decimali si distinguono un **bit più significativo**, ovvero quello più a sinistra e un **bit meno significativo**, ovvero quello più a destra
## Da decimale a binario
Si divide ripetutamente il numero intero decimale per 2 fino ad ottenere quoziente nullo. Il numero binario è la sequenza di quozienti, dove il bit più significativo è l'ultimo quoziente calcolato.

*Esempio:* $15_{(10)}=\frac{15}{2}=7,5\rightarrow \frac{7}{2}=3,5\rightarrow \frac{3}{2}=1,5\rightarrow \frac{1}{2}=0,5\rightarrow 1111$
## Da binario a decimale
Si moltiplica la cifra binaria per 2 elevato alla posizione, contata partendo da 0 a destra.
*Esempio:* $1101_{(2)}=1*2^0+0\cdot2^1+1\cdot 2^2+1\cdot 2^3=1+4+8=13_{(10)}$
## Somme
Similmente alle addizioni in decimale, $1+0=0$ e $0+0=0$. Quando di sommano 1 insieme si ha 0 con il resto di 1.
*Esempio:* $100011 +000111=101010$
![[Sistemi di numerazione-1785676210811.webp]]
Questa operazione ci permette di utilizzare gli **adder** nei circuiti.
## Numeri negativi
## Sottrazioni
## Prodotti
## Virgola
## Sistema 10088e3628

# Numerario 12
# 8