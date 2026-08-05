---
tags: [architettura, combinatoria, booleana, cap2]
capitolo: 2
sezione: "2.3"
pagine_pdf: 76-82
---

# Assiomi e teoremi dell'algebra di Boole

L'algebra di Boole si costruisce su un insieme di **assiomi** (assunti non dimostrati)
dai quali si **dimostrano** tutti i teoremi. Serve per semplificare le equazioni
booleane e quindi ridurre l'hardware.

## Il principio di dualità
Assiomi e teoremi obbediscono al **principio di dualità**: scambiando
$AND \leftrightarrow OR$ e $0 \leftrightarrow 1$ si ottiene un'affermazione altrettanto vera.
Per questo ogni riga ha una versione e la sua duale.

## Assiomi
| # | Assioma | Duale | Nome |
|---|---|---|---|
| A1 | $B = 0$ se $B \ne 1$ | $B = 1$ se $B \ne 0$ | binario |
| A2 | $\overline{0} = 1$ | $\overline{1} = 0$ | NOT |
| A3 | $0 \cdot 0 = 0$ | $1 + 1 = 1$ | AND/OR |
| A4 | $1 \cdot 1 = 1$ | $0 + 0 = 0$ | AND/OR |
| A5 | $0 \cdot 1 = 1 \cdot 0 = 0$ | $1 + 0 = 0 + 1 = 1$ | AND/OR |

## Teoremi a una variabile
| # | Teorema | Duale | Nome |
|---|---|---|---|
| T1 | $B \cdot 1 = B$ | $B + 0 = B$ | **identità** |
| T2 | $B \cdot 0 = 0$ | $B + 1 = 1$ | **elemento nullo** |
| T3 | $B \cdot B = B$ | $B + B = B$ | **idempotenza** |
| T4 | $\overline{\overline{B}} = B$ | — | **involuzione** |
| T5 | $B \cdot \overline{B} = 0$ | $B + \overline{B} = 1$ | **complementi** |

Interpretazione: T2 dice che un ingresso a 0 su un AND forza l'uscita a 0 (e un
ingresso a 1 su un OR forza l'uscita a 1) — utilissimo per il **masking** dei bit.

## Teoremi a più variabili
| # | Teorema | Duale | Nome |
|---|---|---|---|
| T6 | $BC = CB$ | $B+C = C+B$ | **commutatività** |
| T7 | $(BC)D = B(CD)$ | $(B+C)+D = B+(C+D)$ | **associatività** |
| T8 | $(BC)+(BD) = B(C+D)$ | $(B+C)(B+D) = B + CD$ | **distributività** |
| T9 | $B(B+C) = B$ | $B + BC = B$ | **copertura** (*covering*) |
| T10 | $BC + B\overline{C} = B$ | $(B+C)(B+\overline{C}) = B$ | **combinazione** (*combining*) |
| T11 | $BC + \overline{B}D + CD = BC + \overline{B}D$ | $(B+C)(\overline{B}+D)(C+D) = (B+C)(\overline{B}+D)$ | **consenso** (*consensus*) |
| T12 | $\overline{B_0 B_1 B_2 \dots} = \overline{B_0}+\overline{B_1}+\overline{B_2}+\dots$ | $\overline{B_0 + B_1 + \dots} = \overline{B_0}\ \overline{B_1}\dots$ | **De Morgan** |

> [!important] I tre teoremi da avere in mano
> **T9 copertura, T10 combinazione, T11 consenso** sono quelli che permettono di
> eliminare variabili e termini superflui: sono il motore della minimizzazione
> algebrica.
> - T10 è il caso più usato: due termini che differiscono per un solo letterale si
>   fondono eliminando quel letterale. È esattamente ciò che fa graficamente una
>   coppia di caselle adiacenti in una mappa di Karnaugh.
> - T11 dice che il termine $CD$ è **ridondante**: è già coperto dagli altri due.

## Come si dimostrano i teoremi
Con **prova esaustiva** (*perfect induction*): se le variabili sono in numero finito, si
verifica il teorema su tutte le combinazioni della tabella di verità.

## Minimizzazione
Un'equazione in forma SOP si dice **minimizzata** se usa il minimo numero possibile di
implicanti, e se ogni implicante contiene il minimo numero di letterali.
A volte, per minimizzare, è utile **espandere** un implicante (es. duplicarlo con T3)
per poterlo poi combinare in due modi diversi.

## Da ricordare
- Dualità: AND↔OR, 0↔1.
- T10 combinazione: $BC + B\overline{C} = B$ ← il cuore della semplificazione.
- T11 consenso: il termine "in mezzo" è ridondante.
- Le dimostrazioni si fanno per prova esaustiva.

## Domande flash
1. Semplifica $\overline{A}\,\overline{B}\,\overline{C} + A\overline{B}\,\overline{C}$.
2. Applica T11 a $AB + \overline{A}C + BC$.
3. Qual è il duale di $B + BC = B$?

Collegato a: [[Teorema di De Morgan e bubble pushing]] · [[Mappe di Karnaugh]]
