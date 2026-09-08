---
Materia: Architettura degli elaboratori
tags:
  - algebra_booleana
  - Logica
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 2.2'
Imparato: true
Ordine: 202
aliases:
  - letterale
  - mintermine
  - maxtermine
  - implicante
---
Le equazioni booleane trattano variabili che valgono solo TRUE o FALSE. Un'equazione è semplificabile tramite [[Assiomi e teoremi dell algebra di Boole|algebra di Boole]].
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
Quindi $Y = A + BC$ si legge $A$ OR ($B$ AND $C$), e $\overline{A} + B \ne \overline{A+B}$. Simile all'algebra classica.
## Tabelle di verità
Una [[Porte logiche|tabella di verità]] con $N$ ingressi ha $2^N$ righe, una per ogni combinazione dei valori d'ingresso. La specifica funzionale di un [[Circuiti combinatori e sequenziali|circuito combinatorio]] si esprime tipicamente come tabella di verità o come equazione booleana.
