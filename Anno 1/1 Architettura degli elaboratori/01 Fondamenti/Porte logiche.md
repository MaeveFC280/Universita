---
Materia: Architettura degli elaboratori
tags:
  - Logica
  - algebra_booleana
Link risorse: https://youtu.be/QZwneRb-zqA?si=hfEXSbPngFlYnGYa&t=50
Libro: '"Digital Design and Computer Architecture" Capitolo 1.5'
Imparato: true
Ordine: 107
aliases:
  - Logic gates
  - logica booleana
  - logic gates
  - NAND
  - NOR
  - tabella di verità
---
Le **porte logiche** sono circuiti digitali elementari: uno o più ingressi binari, una uscita binaria determinata dalla funzione della porta.

## Porte a un ingresso
| Porta              | Funzione           | Note                                                                                    |
| ------------------ | ------------------ | --------------------------------------------------------------------------------------- |
| **NOT** (inverter) | $Y = \overline{A}$ | il pallino (*bubble*) indica l'inversione                                               |
| **BUFFER**         | $Y = A$            | logicamente inutile, elettricamente utile: rigenera il segnale e pilota carichi elevati |

## Porte a due ingressi
| Porta    | Funzione                    | Uscita alta quando…                                       |
| -------- | --------------------------- | --------------------------------------------------------- |
| **AND**  | $Y = AB$                    | **tutti** gli ingressi sono 1                             |
| **OR**   | $Y = A+B$                   | **almeno un** ingresso è 1                                |
| **XOR**  | $Y = A \oplus B$            | un numero **dispari** di ingressi è 1                     |
| **NAND** | $Y = \overline{AB}$         | negazione dell'AND                                        |
| **NOR**  | $Y = \overline{A+B}$        | negazione dell'OR                                         |
| **XNOR** | $Y = \overline{A \oplus B}$ | gli ingressi sono **uguali** (comparatore di uguaglianza) |

La maggior parte delle porte si estende naturalmente a $N$ ingressi: un NOR a 3 ingressi vale 1 solo se **tutti** gli ingressi sono 0.

## Tabelle di verità

### NOT
Inverte il segnale: vero diventa falso e falso diventa vero.

| INPUT | OUTPUT |
| ----- | ------ |
| 1     | 0      |
| 0     | 1      |

### AND
Restituisce vero solo se **entrambi** gli input sono veri.

| A   | B   | OUTPUT |
| --- | --- | ------ |
| 1   | 0   | 0      |
| 0   | 1   | 0      |
| 1   | 1   | 1      |
| 0   | 0   | 0      |

### OR
Restituisce vero se **almeno uno** degli input è vero.

| A   | B   | OUTPUT |
| --- | --- | ------ |
| 1   | 0   | 1      |
| 0   | 1   | 1      |
| 1   | 1   | 1      |
| 0   | 0   | 0      |

### NAND
Restituisce vero se gli input **non sono entrambi** veri (contrario di AND).

| A   | B   | OUTPUT |
| --- | --- | ------ |
| 1   | 0   | 1      |
| 0   | 1   | 1      |
| 1   | 1   | 0      |
| 0   | 0   | 1      |

### XOR
Restituisce vero se **uno solo** degli input è vero.

| A   | B   | OUTPUT |
| --- | --- | ------ |
| 1   | 0   | 1      |
| 0   | 1   | 1      |
| 1   | 1   | 0      |
| 0   | 0   | 0      |

## Proprietà
Le porte logiche sono combinabili tra loro e le funzioni che realizzano obbediscono alle proprietà dell'algebra booleana:

- **commutativa**: $A + B = B + A$, $AB = BA$
- **associativa**: $(A+B)+C = A+(B+C)$, $(AB)C = A(BC)$
- **distributiva**: $A(B+C) = AB + AC$
- **idempotenza**: $A + A = A$, $AA = A$
- **complemento**: $A + \overline{A} = 1$, $A\overline{A} = 0$

L'elenco completo con le dimostrazioni è in: [[Assiomi e teoremi dell algebra di Boole]].

## NAND come porta universale
Da soli NAND si ricavano **tutte** le altre porte: per questo NAND (e ugualmente NOR) si dice **porta universale**. 

### NOT da NAND
![[Logic gates-1785674899875.webp]]

### AND da NAND
![[Logic gates-1785674529626.webp]]

### OR da NAND
Ora che sappiamo come ricavare NOT da NAND, possiamo usarlo per ricavare a sua volta OR.
Questo circuito è quindi ricreabile con soli NAND, sostituendo ogni NOT con lo schema visto sopra.
![[Logic gates-1785675053477.webp]]

> [!tip] Perché funziona
> $\overline{A \cdot A} = \overline{A}$ dà il NOT; negando l'uscita di un NAND si ottiene l'AND; negando i due ingressi di un NAND si ottiene l'OR (è [[Teorema di De Morgan e bubble pushing|De Morgan]] applicato al contrario).