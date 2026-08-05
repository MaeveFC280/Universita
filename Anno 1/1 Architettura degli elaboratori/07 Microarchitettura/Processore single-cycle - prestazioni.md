---
Materia: Architettura degli elaboratori
tags:
  - microarchitettura
  - prestazioni
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 7.3.3'
Imparato: false
Ordine: 705
aliases:
  - prestazioni single-cycle
  - periodo di clock
---

# Processore single-cycle: prestazioni e limiti

## CPI
**Ogni istruzione** del processore single-cycle richiede **esattamente un ciclo di
clock**, quindi:

$$CPI = 1$$

Questo è il valore ideale — e sembrerebbe ottimo. Il problema è il **tempo di ciclo**.

## Il cammino critico
Il periodo di clock deve essere abbastanza lungo perché **l'istruzione più lenta** possa
completarsi in un ciclo. Per il processore descritto, l'istruzione critica è **`LDR`**,
perché è la sola che attraversa **tutti** i blocchi:

1. lettura del PC ($t_{pcq\_PC}$)
2. lettura della **memoria istruzioni** ($t_{mem}$)
3. decodifica e lettura del **register file** (in parallelo con Extend e mux)
4. calcolo dell'indirizzo nell'**ALU** ($t_{ALU}$)
5. lettura della **memoria dati** ($t_{mem}$)
6. multiplexer di write-back ($t_{mux}$)
7. **setup** del register file ($t_{RFsetup}$)

$$T_c \ge t_{pcq\_PC} + 2t_{mem} + t_{decode} + t_{RFread} + t_{ALU} + t_{mux} + t_{RFsetup}$$

> [!important] I colli di bottiglia reali
> Nella maggior parte delle implementazioni, **l'ALU, la memoria e il register file sono
> sostanzialmente più lenti** degli altri blocchi combinatori (mux, extend, decoder).
> Quindi il tempo di ciclo è dominato da: **due accessi a memoria + un'ALU + un accesso
> al register file**.
>
> Il risultato finale, in `Result`, deve arrivare al register file rispettando il
> **tempo di setup** prima del successivo fronte di salita.

## Le tre debolezze del single-cycle
> Il processore single-cycle ha **tre debolezze notevoli**:

1. **Richiede un ciclo di clock lunghissimo**, dimensionato sull'istruzione più lenta
   (`LDR`), anche se molte istruzioni sarebbero molto più veloci. Le istruzioni brevi
   "sprecano" il tempo residuo del ciclo.
2. **Richiede tre sommatori** (l'ALU più i due sommatori per PC+4 e PC+8): i sommatori
   sono circuiti relativamente costosi in area.
3. **Richiede due memorie separate** — una per le istruzioni e una per i dati — perché
   entrambe devono essere accedute nello **stesso ciclo**. Nella realtà si hanno due
   **cache** separate (istruzioni e dati) alimentate da un'unica memoria principale
   (→ [[Cache - organizzazione e parametri]]).

## La conclusione
Il single-cycle è **il progetto più semplice da capire e da verificare**, ed è per questo
che si studia per primo. Ma le sue prestazioni sono modeste e il costo in hardware
duplicato è elevato.

Il **multiciclo** risolve tutti e tre i problemi: riusa lo stesso hardware in cicli
diversi (un solo sommatore, una sola memoria) e adatta il numero di cicli
all'istruzione. → [[Processore multiciclo - datapath]]

## Da ricordare
- $CPI = 1$, ma $T_c$ dettato da **LDR** (l'istruzione più lunga).
- Il cammino critico attraversa: memoria istruzioni → register file → ALU → memoria dati
  → mux → setup RF.
- Le **3 debolezze**: ciclo lungo, tre sommatori, due memorie.

## Domande flash
1. Perché è `LDR` a determinare il tempo di ciclo?
2. Cosa "spreca" l'istruzione `B` in un processore single-cycle?
3. Perché servono due memorie distinte?
