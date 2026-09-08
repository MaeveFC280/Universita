---
Materia: Architettura degli elaboratori
tags:
  - ARM
  - assembly
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 6.2.2'
Imparato: true
Ordine: 602
aliases:
  - registri
  - register set
  - R0-R15
---
Le istruzioni devono prelevare gli operandi da qualche parte. Le opzioni sono:
- **costanti** codificate nell'istruzione stessa,
- **registri**,
- **memoria**.

Gli operandi in costanti o registri si accedono **rapidamente**, ma ne possono contenere poco. La memoria è capiente ma **lenta**. Per questo la maggior parte delle architetture definisce un **piccolo numero di registri** che contengono i dati usati più frequentemente — applicazione del principio **"[[Principi di assembly|più piccolo è più veloce]]"**.

## I 16 registri
ARM ha **16 registri** a 32 bit esadecimali, denominati **R0–R15** (il nome è preceduto dalla lettera `R`).

| Registro | Uso |
|---|---|
| **R0–R3** | argomenti delle funzioni / valori di ritorno |
| **R4–R11** | variabili locali (**da preservare** tra le chiamate) |
| **R12** | **IP** — *intra-procedure-call scratch register* |
| **R13** | **SP** — *stack pointer* |
| **R14** | **LR** — *link register* |
| **R15** | **PC** — *program counter* |

> [!important] I tre registri con nome
> - **R12 = IP**: calcoli o valori intermedi **temporanei** durante le [[Funzioni|chiamate di funzione]]
> - **R13 = SP**: punta alla cima dello [[Lo stack|stack]].
> - **R14 = LR**: contiene l'indirizzo di ritorno di una [[Funzioni|funzione]].
> - **R15 = PC**: **il program counter è accessibile come un normale registro**. Questa
> è una peculiarità di ARM: scrivere in R15 provoca un salto. Viene incrementata per ogni [[Operandi|istruzione]] eseguita

> [!warning] La regola del PC + 8
> **Leggere R15 restituisce PC + 8**, non l'indirizzo dell'istruzione corrente.
>
> Il motivo è storico/implementativo: nella pipeline originale a 3 stadi, quando un'istruzione era in esecuzione, il PC era già avanzato di due istruzioni ($2 \times 4 = 8$ byte).
>
> Questo valore di 8 ricorre nel calcolo degli indirizzi di **branch** e nell'
> **indirizzamento relativo al PC**.

## Convenzioni di preservazione
| Categoria                         | Registri                   | Chi è responsabile                                                                             |
| --------------------------------- | -------------------------- | ---------------------------------------------------------------------------------------------- |
| **Preserved** (*callee-saved*)    | R4–R11, R13 (SP), R14 (LR) | la funzione **[[Funzioni\|chiamata]]** deve ripristinarli            |
| **Nonpreserved** (*caller-saved*) | R0–R3, R12                 | la funzione **[[Funzioni\|chiamatante]]** non può contare su di essi |
