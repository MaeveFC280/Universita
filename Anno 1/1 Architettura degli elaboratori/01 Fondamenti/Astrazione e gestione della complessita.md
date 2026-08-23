---
Materia: Architettura degli elaboratori
tags:
  - astrazione
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 1.1-1.2'
Imparato: true
Ordine: 101
aliases:
  - Da 0 a 1
  - Astrazione
  - astrazione
  - gerarchia
  - modularità
  - regolarità
---
## Idea centrale
La tecnica fondamentale per gestire la complessità è l'**astrazione**: si nasconde il dettaglio irrilevante e si espone solo ciò che serve al livello superiore. Un sistema può essere osservato da molti livelli di astrazione diversi, e a ogni livello corrispondono "mattoni" tipici.

## I livelli di astrazione di un sistema elettronico
Dal basso verso l'alto:

| Livello            | Mattoni tipici                  | Disciplina                                            |
| ------------------ | ------------------------------- | ----------------------------------------------------- |
| Fisica             | elettroni                       | fisica dei dispositivi                                |
| Dispositivi        | diodi, transistor               | elettronica                                           |
| Circuiti analogici | amplificatori                   | elettronica                                           |
| Circuiti digitali  | porte logiche (AND, OR, NOT)    | **progetto digitale**                                 |
| Moduli logici      | sommatori, memorie, multiplexer | **progetto digitale**                                 |
| Microarchitettura  | datapath, unità di controllo    | [[Microarchitettura - datapath e unita di controllo]] |
| Architettura       | istruzioni, registri            | [[Principi di assembly]]        |
| Sistema operativo  | driver, gestione memoria        | informatica                                           |
| Applicazioni       | programmi                       | informatica                                           |

> [!tip] Perché conta
> Chi progetta un processore non ragiona in termini di elettroni: lavora con [[Porte logiche|porte logiche]] e registri. Chi scrive un programma non ragiona in termini di transistor. L'astrazione è ciò che rende possibile costruire sistemi con miliardi di componenti.

## Le tre discipline di supporto
- **Gerarchia**: si divide il sistema in moduli, e ogni modulo in sottomoduli, fino ad arrivare a pezzi comprensibili.
- **Modularità**: ogni modulo ha una funzione e un'interfaccia ben definite; non produce effetti collaterali fuori dalla propria interfaccia.
- **Regolarità**: si favorisce l'uniformità, così che i moduli si possano riusare e sostituire facilmente.
