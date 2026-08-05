---
tags: [architettura, arm, assembly, cap6]
capitolo: 6
sezione: "6.1 - 6.2"
pagine_pdf: 311-314
---

# Linguaggio assembly: principi di progetto

## Che cos'è
L'**architettura** di un calcolatore è definita dal suo **instruction set** (insieme di
istruzioni) e dallo **stato architetturale** (registri e memoria visibili al
programmatore).

Il **linguaggio assembly** è la rappresentazione **leggibile dall'uomo** del linguaggio
macchina del calcolatore. Ogni istruzione assembly corrisponde a una (o poche) istruzioni
macchina.

## I quattro principi di progetto ARM
1. **La regolarità favorisce la semplicità** (*regularity supports simplicity*).
2. **Rendere veloce il caso comune** (*make the common case fast*).
3. **Più piccolo è più veloce** (*smaller is faster*).
4. **Un buon progetto richiede buoni compromessi** (*good design demands good
   compromises*).

> [!important] Come leggere i principi
> Sono la chiave interpretativa di **tutto** il capitolo. Ogni scelta apparentemente
> arbitraria dell'ISA ARM (numero di registri, formati delle istruzioni, numero di
> operandi) si spiega con uno di questi quattro principi. In esame, saper motivare una
> scelta architetturale con il principio corrispondente vale più che ricordarla a
> memoria.

### Regolarità → semplicità
Le istruzioni hanno un formato uniforme: **stesso numero di operandi**, campi in
posizioni fisse. Questo rende la decodifica hardware semplice e veloce.

Esempio: tutte le istruzioni aritmetiche hanno la forma
```
ISTRUZIONE  destinazione, operando1, operando2
ADD   R0, R1, R2      ; R0 = R1 + R2
SUB   R0, R1, R2      ; R0 = R1 - R2
```

### Rendere veloce il caso comune
Le operazioni **frequenti** sono realizzate direttamente in hardware, con una singola
istruzione veloce. Le operazioni **più elaborate e meno comuni** si eseguono con
**sequenze di più istruzioni**, oppure non esistono affatto nell'ISA.

Esempio: non esiste un'istruzione "calcola il seno"; la si ottiene con una sequenza di
istruzioni o in libreria.

### Più piccolo è più veloce
Un numero **limitato** di registri veloci è preferibile a molti registri lenti. Da qui
la scelta di 16 registri (→ [[Registri ARM]]).

### Buoni compromessi
Non tutte le esigenze sono compatibili. Esempio: la regolarità vorrebbe **un solo
formato** di istruzione, ma questo sarebbe troppo rigido; ARM ne definisce **tre**
(→ [[Linguaggio macchina - formati istruzione]]).

## Sintassi assembly ARM
```
ADD R0, R1, R2    ; questo è un commento: da ';' a fine riga
```
- La prima parte dell'istruzione (`ADD`) è il **mnemonico** e indica **quale
  operazione** eseguire.
- Seguono gli **operandi**: prima la **destinazione**, poi le sorgenti.
- In ARM esistono **solo commenti su una riga**: iniziano con **punto e virgola (`;`)**
  e continuano fino a fine riga.

## Esempi elementari
| C | ARM assembly |
|---|---|
| `a = b + c;` | `ADD R0, R1, R2` |
| `a = b - c;` | `SUB R0, R1, R2` |
| `a = b + c - d;` | `ADD R0, R1, R2` <br> `SUB R0, R0, R3` |

## Da ricordare
- I **4 principi**: regolarità, caso comune veloce, piccolo=veloce, buoni compromessi.
- Formato: `MNEMONICO  Rdest, Rsrc1, Rsrc2` — **destinazione per prima**.
- Commenti con `;`, solo su una riga.

## Domande flash
1. Quale principio giustifica il fatto che ARM ha soli 16 registri?
2. Quale principio giustifica l'esistenza di tre formati di istruzione anziché uno?
