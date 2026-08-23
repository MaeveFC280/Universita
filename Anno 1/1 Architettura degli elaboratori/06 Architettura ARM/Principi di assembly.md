---
Materia: Architettura degli elaboratori
tags:
  - ARM
  - assembly
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 6.1-6.2'
Imparato: true
Ordine: 601
aliases:
  - assembly
  - ISA
  - principi di progetto
---
L'**architettura** di un calcolatore è definita dal suo **instruction set** (insieme di istruzioni) e dallo **stato architetturale** (registri e memoria visibili al programmatore).

Il **linguaggio assembly** è la rappresentazione **leggibile dall'uomo** del linguaggio macchina del calcolatore. Ogni istruzione assembly corrisponde a una (o poche) istruzioni macchina.

## I quattro principi di progetto ARM
1. **La regolarità favorisce la semplicità** 
	Le istruzioni hanno un formato uniforme: **stesso numero di operandi**, campi in posizioni fisse. Questo rende la decodifica hardware semplice e veloce.
	*Esempio: tutte le istruzioni aritmetiche hanno la forma*
```
ISTRUZIONE  destinazione, operando1, operando2
ADD   R0, R1, R2      ; R0 = R1 + R2
SUB   R0, R1, R2      ; R0 = R1 - R2
```
2. **Rendere veloce il caso comune** 
	Le operazioni **frequenti** sono realizzate direttamente in hardware, con una singola istruzione veloce. Le operazioni **più elaborate e meno comuni** si eseguono con **sequenze di più istruzioni**, oppure non esistono affatto nell'ISA. *Esempio: non esiste un'istruzione "calcola il seno"; la si ottiene con una sequenza di istruzioni o in libreria.*
3. **Più piccolo è più veloce**
	Un numero **limitato** di registri veloci è preferibile a molti registri lenti. Da qui la scelta di 16 [[Registri ARM|registri]]
4. **Un buon progetto richiede buoni compromessi** 
	Non tutte le esigenze sono compatibili. Esempio: la regolarità vorrebbe **un solo formato** di istruzione, ma questo sarebbe troppo rigido; ARM ne definisce **[[Linguaggio macchina|tre]]** 
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
| C                | ARM assembly                           |
| ---------------- | -------------------------------------- |
| `a = b + c;`     | `ADD R0, R1, R2`                       |
| `a = b - c;`     | `SUB R0, R1, R2`                       |
| `a = b + c - d;` | `ADD R0, R1, R2` <br> `SUB R0, R0, R3` |