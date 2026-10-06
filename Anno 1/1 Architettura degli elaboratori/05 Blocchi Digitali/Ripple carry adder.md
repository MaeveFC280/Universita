---
Materia: Architettura degli elaboratori
tags:
  - aritmetica
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 5.2.1'
Imparato: true
Ordine: 502
aliases:
  - ripple carry
  - propagazione del riporto
---
Un **[[Half adder e full adder|sommatore]] a $N$ bit** somma due ingressi a $N$ bit, $A$ e $B$, più un [[Addizione binaria e overflow|riporto]] in ingresso $C_{in}$, e produce un risultato a $N$ bit $S$ e un riporto in uscita $C_{out}$. È detto anche **carry propagate adder** (CPA), perché il riporto si propaga da una colonna all'altra.

## Costruzione
Il modo **più semplice** di costruire un CPA a $N$ bit è mettere in **catena** $N$ full adder, collegando il $C_{out}$ di ciascuno al $C_{in}$ del successivo. Questo si chiama **ripple-carry adder** (sommatore a propagazione del riporto).
![[Ripple carry adder-1787752352610.webp|544]]
## Prestazioni
Il ritardo del ripple-carry adder **cresce linearmente con il numero di bit**, perché nel caso peggiore il riporto deve attraversare **tutti** gli stadi:

$$t_{ripple} = N \cdot t_{FA}$$

dove $t_{FA}$ è il ritardo di un full adder (precisamente il ritardo da $C_{in}$ a $C_{out}$).

*Esempio: con $t_{FA} = 300$ ps, un sommatore a 32 bit ha $t_{ripple} = 9{,}6$ ns. Su un processore da 1 GHz il ciclo di clock è 1 ns: inaccettabile.*
