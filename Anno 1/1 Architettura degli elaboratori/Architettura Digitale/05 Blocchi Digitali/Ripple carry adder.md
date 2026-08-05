---
tags: [architettura, aritmetica, blocchi, cap5]
capitolo: 5
sezione: "5.2.1"
pagine_pdf: 256-257
---

# Ripple carry adder

## Definizione
Un **sommatore a $N$ bit** somma due ingressi a $N$ bit, $A$ e $B$, più un riporto in
ingresso $C_{in}$, e produce un risultato a $N$ bit $S$ e un riporto in uscita $C_{out}$.
È detto anche **carry propagate adder** (CPA), perché il riporto si propaga da una
colonna all'altra.

## Costruzione
Il modo **più semplice** di costruire un CPA a $N$ bit è mettere in **catena** $N$ full
adder, collegando il $C_{out}$ di ciascuno al $C_{in}$ del successivo. Questo si chiama
**ripple-carry adder** (sommatore a propagazione del riporto).

```
      A3 B3      A2 B2      A1 B1      A0 B0
       |  |       |  |       |  |       |  |
Cout <-FA<--C3---FA<--C2----FA<--C1----FA<-- Cin
       |          |          |          |
       S3         S2         S1         S0
```

## Prestazioni: il problema
Il ritardo del ripple-carry adder **cresce linearmente con il numero di bit**, perché
nel caso peggiore il riporto deve attraversare **tutti** gli stadi:

$$t_{ripple} = N \cdot t_{FA}$$

dove $t_{FA}$ è il ritardo di un full adder (precisamente il ritardo da $C_{in}$ a
$C_{out}$).

Esempio: con $t_{FA} = 300$ ps, un sommatore a 32 bit ha $t_{ripple} = 9{,}6$ ns.
Su un processore da 1 GHz il ciclo di clock è 1 ns: inaccettabile.

## Vantaggi e svantaggi
| Pro | Contro |
|---|---|
| semplicissimo, regolare, modulare | **lento**: $O(N)$ |
| area minima | il ritardo domina il cammino critico del processore |

## Da ricordare
- $t_{ripple} = N \cdot t_{FA}$: ritardo **lineare** in $N$.
- È il sommatore più semplice e il più lento.
- La soluzione al problema è il **carry-lookahead**.

## Domande flash
1. Con $t_{FA}=200$ ps, quanto ritarda un ripple adder a 16 bit?
2. Perché il cammino critico è quello del riporto e non quello della somma?

Collegato a: [[Carry lookahead adder]]
