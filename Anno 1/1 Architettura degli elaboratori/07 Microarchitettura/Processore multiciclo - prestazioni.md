---
Materia: Architettura degli elaboratori
tags:
  - microarchitettura
  - prestazioni
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 7.4.3'
Imparato: false
Ordine: 708
aliases:
  - prestazioni multiciclo
  - CPI medio
---
## Il tempo di esecuzione
> Il [[Analisi delle prestazioni e CPI|tempo di esecuzione]] di un'istruzione dipende **sia dal numero di cicli** che richiede **sia dalla durata del ciclo**.

$$T_{exec} = N_{istr} \times CPI \times T_c$$

Mentre il [[Processore single-cycle - datapath|single-cycle]] eseguiva **tutte** le istruzioni in un ciclo, il [[Processore multiciclo - datapath|multiciclo]] usa un **numero variabile** di cicli per le diverse istruzioni.

## Cicli per istruzione
| Istruzione | Cicli |
|---|---|
| `LDR` | 5 |
| `STR` | 4 |
| Data-processing | 4 |
| `B` | 3 |

## Calcolo del CPI medio
Il CPI si calcola come **media pesata** sulla frequenza relativa delle istruzioni nel benchmark:

$$CPI = \sum_i f_i \cdot CPI_i$$

**Esempio** con un mix tipico (25% LDR, 10% STR, 52% data-processing, 13% branch):

$$CPI = 0{,}25(5) + 0{,}10(4) + 0{,}52(4) + 0{,}13(3) = 1{,}25 + 0{,}40 + 2{,}08 + 0{,}39 = 4{,}12$$

## Il cammino critico
Esaminando il [[Microarchitettura - datapath e unita di controllo|datapath]] si individuano **due possibili cammini critici** che limitano il tempo di ciclo:

1. **Il cammino attraverso l'ALU**: lettura del [[Register file ROM e logic array|register file]] (o dei registri non architetturali) → [[Multiplexer|multiplexer]] → ALU → setup di `ALUOut`.
2. **Il cammino attraverso la memoria**: `ALUOut` → multiplexer di indirizzo → memoria → setup di `Instr`/`Data`.

$$T_c \ge \max\big(\underbrace{t_{pcq} + t_{mux} + t_{ALU} + t_{setup}}_{\text{via ALU}},\ \underbrace{t_{pcq} + t_{mux} + t_{mem} + t_{setup}}_{\text{via memoria}}\big)$$

Il ciclo è quindi determinato dal **più lento tra ALU e memoria**, non dalla loro somma come nel single-cycle.

## Il confronto con il single-cycle
> [!important] La lezione da portare a casa
> Il multiciclo ha $T_c$ **molto più breve** ma $CPI \approx 4$. Il single-cycle ha $CPI = 1$ ma $T_c$ molto più lungo. **Il prodotto risulta spesso simile**: nel confronto svolto nel libro il multiciclo non è nettamente più veloce del single-cycle.
>
> Il vero vantaggio del multiciclo non è tanto la velocità quanto:
> - **meno hardware**: una memoria, un [[Half adder e full adder|sommatore]];
> - la **flessibilità** di supportare istruzioni complesse (che richiedono molti cicli)
> senza penalizzare quelle semplici.
>
> Il salto prestazionale vero arriva con il **pipelining**, che ottiene $CPI \approx 1$
> **con** un $T_c$ breve.

### Perché il multiciclo non guadagna quanto si sperava
1. Alcuni cicli sono **sprecati**: in `Decode` si legge il register file anche quando non serve; ogni istruzione paga il ciclo di fetch separato.
2. **Non tutti i passi sono bilanciati**: il ciclo è dettato dal più lento (memoria o ALU), e i passi più brevi sprecano tempo.
3. **L'overhead di sequenziamento** ($t_{pcq} + t_{setup}$) si paga **una volta per ciclo**, quindi 4 volte per istruzione invece di una, perché dipende dai [[Timing sequenziale - setup hold e clock skew|vincoli temporali sequenziali]].

## Da ricordare
- $CPI$ = media pesata dei cicli per tipo di istruzione (≈ 4 per un mix tipico).
- $T_c$ = max tra il cammino via **ALU** e quello via **memoria**.
- Il multiciclo risparmia **hardware**, non necessariamente tempo.
- L'overhead di sequenziamento si paga a **ogni** ciclo: è il costo nascosto del multiciclo.
