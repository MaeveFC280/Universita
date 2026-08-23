---
Materia: Architettura degli elaboratori
tags:
  - microarchitettura
  - datapath
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 7.1'
Imparato: true
Ordine: 701
aliases:
  - microarchitettura
  - datapath
  - unità di controllo
---
L'**architettura** di un calcolatore è definita dal suo **instruction set** e dallo **stato architetturale**. La **microarchitettura** è il **collegamento tra la logica e l'architettura**: è il modo specifico in cui si realizza in hardware una data architettura.

> Una stessa architettura ammette **molte** microarchitetture diverse, con caratteristiche differenti di prestazioni, costo e complessità. Ed è per questo che processori diversi eseguono lo stesso software.

## Stato architetturale e stato non architetturale
- **Stato architetturale**: ciò che il programmatore vede. In ARM: i **16 registri** a 32 bit (R0–R15, compreso il PC) e i **flag di stato**, più la memoria.
- **Stato non architetturale**: registri interni che la microarchitettura aggiunge per **semplificare la logica** o **migliorare le prestazioni**, e che il programmatore **non vede** (registri di pipeline, registri temporanei del [[Processore multiciclo - datapath|multiciclo]], cache…).

## Le due parti
Ogni microarchitettura si divide in **due parti interagenti**:

| Parte | Compito | Tipo di logica |
|---|---|---|
| **datapath** | opera sulle **parole di dati**: contiene memorie, registri, ALU, multiplexer | prevalentemente **combinatoria**, più gli elementi di stato |
| **unità di controllo** | riceve l'**istruzione corrente** dal datapath e gli dice **come eseguirla**, generando i segnali di multiplexer, di abilitazione registri e di scrittura in memoria | **FSM** o logica combinatoria |

## Il sottoinsieme ARM
Per rendere trattabile il progetto, si realizza un **sottoinsieme** dell'instruction set:
- **[[Operandi|istruzioni di elaborazione dati]]**: `ADD`, `SUB`, `AND`, `ORR` (con secondo operando immediato o registro)
- **[[Istruzioni LDR e STR|istruzioni di memoria]]**: `LDR`, `STR`
- **[[Branch ed esecuzione condizionale|branch]]**: `B`

## Gli elementi di stato
| Elemento | Caratteristica |
|---|---|
| **memoria istruzioni** | 1 porta di **lettura**; lettura **combinatoria** |
| **register file** | 2 porte di lettura + 1 di scrittura; letture **combinatorie**, scrittura **sincrona** al fronte |
| **memoria dati** | **una sola** porta di lettura/scrittura; se `WE = 1` scrive sul fronte, altrimenti legge |
| **PC** | logicamente parte del register file (R15), ma **realizzato come registro separato** |

> [!important] Due dettagli che ricorrono in tutti gli esercizi
> 1. **La memoria istruzioni, il [[Register file ROM e logic array|register file]] e la memoria dati si leggono in modo combinatorio**: presentato l'indirizzo, il dato appare dopo un certo ritardo, senza bisogno di clock. Le **scritture** invece sono sincrone: avvengono solo sul fronte di salita. 2. **Il PC è logicamente R15**, ma è tenuto come registro a parte perché è letto e scritto ogni ciclo. E **leggere R15 deve restituire PC + 8**, quindi serve un [[Half adder e full adder|sommatore]] dedicato per rispettare il comportamento di [[Registri ARM|R15]].

Poiché gli elementi di stato cambiano solo sul **fronte di salita** del clock, il processore si può vedere come una **gigantesca [[Macchine a stati finiti - Moore e Mealy|macchina a stati finiti]]**, o come un insieme di FSM interagenti.

## Le tre microarchitetture

| Microarchitettura | Cicli per istruzione | Stato non arch. | $T_c$ |
|---|---|---|---|
| **single-cycle** | **1** (CPI = 1) | **nessuno** | molto **lungo** |
| **multiciclo** | **variabile** (3–5) | diversi registri | **breve** |
| **pipelined** | ≈1 (throughput) | registri di pipeline | breve |

- Il **[[Processore single-cycle - datapath|single-cycle]]** esegue un'intera istruzione in **un solo ciclo**: semplice, non richiede stato non architetturale, ma il **tempo di ciclo** è dettato dall'istruzione più lenta.
- Il **multiciclo** spezza l'istruzione in più passi, aggiungendo **registri non architetturali** per conservare i risultati intermedi. Riusa lo stesso hardware in cicli diversi (una sola memoria, un solo sommatore).
- Il **pipelined** applica il **[[Parallelismo latenza e throughput|pipelining]]** al single-cycle, ottenendo throughput elevato con clock veloce.


![[Datapath e unita di controllo-1787502063076.webp]]