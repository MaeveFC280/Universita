---
Materia: Architettura degli elaboratori
tags:
  - algebra_booleana
  - Logica
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 2.2'
Imparato: false
Ordine: 202
aliases:
  - letterale
  - mintermine
  - maxtermine
  - implicante
---

# Terminologia booleana: letterali, mintermini, maxtermini

Le equazioni booleane trattano variabili che valgono solo TRUE o FALSE.

## Vocabolario essenziale
| Termine | Definizione |
|---|---|
| **Complemento** | l'inverso di una variabile: $\overline{A}$ |
| **Letterale** | una variabile o il suo complemento: $A$, $\overline{A}$, $B$, $\overline{B}$ |
| **Implicante** (o **prodotto**) | AND di uno o più letterali: $A\overline{B}C$ |
| **Mintermine** | prodotto che contiene **tutte** le variabili di ingresso: $A\overline{B}C$ in una funzione di 3 variabili |
| **Somma** | OR di uno o più letterali: $A + \overline{B}$ |
| **Maxtermine** | somma che contiene **tutte** le variabili di ingresso: $A + \overline{B} + C$ |

## Precedenza degli operatori
Dalla più alta alla più bassa:
1. **NOT**
2. **AND**
3. **OR**

Quindi $Y = A + BC$ si legge $A$ OR ($B$ AND $C$), e $\overline{A} + B \ne \overline{A+B}$.
L'ordine conta: usa le parentesi quando c'è il minimo dubbio.

## Tabelle di verità
Una tabella di verità con $N$ ingressi ha $2^N$ righe, una per ogni combinazione dei
valori d'ingresso. La specifica funzionale di un circuito combinatorio si esprime
tipicamente come tabella di verità o come equazione booleana.

## Da ricordare
- **Mintermine e maxtermine contengono TUTTE le variabili** — è questo che li
  distingue da un generico prodotto o somma.
- Precedenza: NOT > AND > OR.
- $N$ ingressi ⇒ $2^N$ righe.

## Domande flash
1. $AB$ è un mintermine in una funzione di 3 variabili?
2. Quante righe ha la tabella di verità di una funzione a 5 ingressi?

Collegato a: [[Forme canoniche SOP e POS]]
