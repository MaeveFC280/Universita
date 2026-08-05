---
tags: [architettura, aritmetica, numerazione, cap5]
capitolo: 5
sezione: "5.3.1"
pagine_pdf: 271-272
---

# Notazione a virgola fissa (fixed-point)

## Il problema
I calcolatori operano sia su **interi** sia su **frazioni**. Servono rappresentazioni
per i numeri non interi.

## La rappresentazione
La notazione a **virgola fissa** ha un **punto binario implicito** tra la parte intera e
la parte frazionaria. La posizione del punto **non è memorizzata**: è una convenzione
concordata tra chi scrive e chi legge il dato.

Esempio: formato a 8 bit con 4 bit interi e 4 frazionari, notazione "4.4":

$$0110.1100_2 = 4 + 2 + 0{,}5 + 0{,}25 = 6{,}75_{10}$$

I pesi della parte frazionaria sono $2^{-1} = 0{,}5$, $2^{-2} = 0{,}25$,
$2^{-3} = 0{,}125$, $2^{-4} = 0{,}0625$.

## Numeri negativi
Si usano gli stessi schemi degli interi: **segno/modulo** o **complemento a due**.
La convenzione più usata è il complemento a due, per gli stessi motivi visti negli
interi (l'addizione ordinaria funziona).

## Aritmetica
> [!tip] Il vantaggio della virgola fissa
> Sommare e sottrarre numeri in virgola fissa **con lo stesso formato** si fa con un
> normale sommatore intero: il punto binario è allineato per costruzione. Nessun
> hardware aggiuntivo.
>
> La moltiplicazione richiede solo di **riaggiustare** la posizione del punto: il
> prodotto di due numeri in formato $a.b$ è in formato $2a.2b$.

## Confronto con la virgola mobile
| | virgola fissa | virgola mobile |
|---|---|---|
| range dinamico | **ristretto** | ampio |
| precisione relativa | variabile (assoluta costante) | costante (relativa) |
| hardware | **semplice** (sommatore intero) | complesso |
| uso tipico | DSP, microcontrollori, grafica embedded | calcolo scientifico, general purpose |

## Da ricordare
- Il punto binario è **implicito**, deciso per convenzione.
- I pesi frazionari sono $2^{-1}, 2^{-2}, \dots$.
- Somme e sottrazioni: hardware intero, senza modifiche.

## Domande flash
1. Quanto vale $0011.0100_2$ in formato 4.4?
2. Rappresenta $-2{,}25$ in formato 4.4 complemento a due.

Collegato a: [[Virgola mobile IEEE 754]]
