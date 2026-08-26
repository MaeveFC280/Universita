---
Materia: Architettura degli elaboratori
tags:
  - aritmetica
  - Logica
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 5.2.2-5.2.4'
Imparato: false
Ordine: 504
aliases:
  - ALU
  - sottrattore
  - comparatore
---
## Sottrattore
Ricordando che $A - B = A + (-B)$ e che in [[Segno, modulo e complemento a due|complemento a due]] si nega **invertendo i bit e aggiungendo 1**:

$$Y = A - B = A + \overline{B} + 1$$

Realizzazione: si usa un **normale [[Half adder e full adder|sommatore]]**, si invertono i bit di $B$ con degli inverter, e si forza $C_{in} = 1$.

> [!tip] Conseguenza architetturale
> Lo **stesso hardware** somma e sottrae. Basta un segnale di controllo che decide se invertire $B$ e mettere il carry in ingresso a 1. È il motivo per cui il complemento a due ha vinto.


![[Sottrattori comparatori e ALU-1787752527431.webp]]
## Comparatori
Un **comparatore** determina se due numeri binari sono uguali o se uno è maggiore o minore dell'altro.

### Comparatore di uguaglianza
Produce una singola uscita che indica se $A = B$. Funzionamento:
1. si verifica con degli **XNOR** se i bit corrispondenti di ogni colonna sono uguali;
2. si mettono in **AND** tutti i risultati: l'uscita è 1 solo se **tutte** le colonne coincidono.

$$\text{Equal} = \overline{(A_0 \oplus B_0)} \cdot \overline{(A_1 \oplus B_1)} \cdots$$

### Comparatore di magnitudine
Si calcola $A - B$ e si guarda il **bit di segno** del risultato:
- risultato **negativo** (bit di segno = 1) → $A < B$;
- altrimenti → $A \ge B$.

Combinando il bit di segno con i flag di zero e overflow si ottengono tutte le relazioni ($<, \le, >, \ge, =, \ne$).

## ALU (Arithmetic/Logical Unit)
Un'**ALU** combina in un unico blocco una varietà di operazioni matematiche e logiche. Un'ALU tipica esegue **addizione, sottrazione, AND e OR**.
![[Sottrattori comparatori e ALU-1787752697459.webp|322x340]]
### Struttura tipica
- un **sommatore** condiviso per ADD e SUB (con inverter e mux su $B$);
- porte **AND** e **OR** bit a bit;
- un **[[Multiplexer|multiplexer]] di uscita** comandato dal segnale **ALUControl**, che seleziona quale risultato presentare su **ALUResult**.

| ALUControl | Operazione |
|---|---|
| 00 | ADD |
| 01 | SUB |
| 10 | AND |
| 11 | OR |

![[Sottrattori comparatori e ALU-1787753783380.webp|277]]

### I flag di stato
L'ALU produce anche i **flag di condizione**, indispensabili per i salti condizionati:

| Flag               | Significato                                          |
| ------------------ | ---------------------------------------------------- |
| **N** (*negative*) | il risultato è negativo (msb = 1)                    |
| **Z** (*zero*)     | il risultato è zero (NOR di tutti i bit)             |
| **C** (*carry*)    | c'è stato riporto in uscita (aritmetica senza segno) |
| **V** (*overflow*) | overflow in complemento a due                        |



![[Sottrattori comparatori e ALU-1787753748972.webp|393]]