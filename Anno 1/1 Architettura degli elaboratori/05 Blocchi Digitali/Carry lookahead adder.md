---
Materia: Architettura degli elaboratori
tags:
  - aritmetica
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 5.2.1'
Imparato: false
Ordine: 503
aliases:
  - CLA
  - carry lookahead
  - prefix adder
---
Il **carry-lookahead adder** è un [[Half adder e full adder|sommatore]] a [[Ripple carry adder|propagazione del riporto]] che risolve il problema del ritardo lineare. L'osservazione chiave:

> Si può determinare **rapidamente** se un blocco di colonne genererà un [[Addizione binaria e overflow|riporto]] in uscita, **senza attendere** che il riporto si propaghi bit per bit attraverso il blocco.

Il CLA divide il sommatore in **blocchi** (tipicamente di 4 bit) e calcola in parallelo i riporti in ingresso a ciascun blocco.

## Segnali generate e propagate
I CLA usano i segnali **generate** ($G$) e **propagate** ($P$), che descrivono come una colonna (o un blocco) si comporta rispetto al riporto.

Per la colonna $i$:
- la colonna **genera** un riporto se produce un $C_{out}$ **indipendentemente** dal riporto in ingresso: succede solo se **entrambi** i bit sono 1
  $$G_i = A_i B_i$$
- la colonna **propaga** un riporto se produce un $C_{out}$ **quando** c'è un riporto in ingresso: succede se **almeno uno** dei due bit è 1
  $$P_i = A_i + B_i$$

Da cui l'equazione fondamentale del riporto:

$$C_i = A_iB_i + (A_i + B_i)C_{i-1} = G_i + P_i C_{i-1}$$

## Estensione ai blocchi
Le definizioni si estendono a **blocchi** di più colonne. Un blocco:
- **genera** un riporto se lo produce da sé, indipendentemente dal riporto in ingresso;
- **propaga** un riporto se **tutte** le sue colonne propagano.

Per un blocco di 4 colonne (bit 3:0):
$$P_{3:0} = P_3 P_2 P_1 P_0$$
$$G_{3:0} = G_3 + P_3\left(G_2 + P_2(G_1 + P_1 G_0)\right)$$

e il riporto in uscita dal blocco:
$$C_{i} = G_{i:j} + P_{i:j}\,C_{j-1}$$

## Perché è veloce
Il ritardo complessivo diventa:

$$t_{CLA} = t_{pg} + t_{pg\_block} + \left(\frac{N}{k} - 1\right)t_{AND\_OR} + k\, t_{FA}$$

dove $k$ è la dimensione del blocco. Il punto chiave: il termine dominante scala con $N/k$ e non con $N$, quindi per $N$ grande il CLA è **molto** più veloce del ripple-carry. Il ritardo cresce ancora linearmente, ma con pendenza $1/k$ del ripple.

## Prefix adder (cenno)
Portando l'idea all'estremo con una struttura ad **albero** di calcolo dei generate/propagate, si ottiene il **prefix adder**, il cui ritardo cresce come $O(\log_2 N)$: è la struttura usata nei processori ad alte prestazioni.

$$t_{PA} = t_{pg} + \log_2 N \cdot t_{pg\_prefix} + t_{XOR}$$

## Confronto
| Sommatore | Ritardo | Area |
|---|---|---|
| Ripple-carry | $O(N)$ | minima |
| Carry-lookahead | $O(N/k)$ | media |
| Prefix | $O(\log_2 N)$ | massima |


