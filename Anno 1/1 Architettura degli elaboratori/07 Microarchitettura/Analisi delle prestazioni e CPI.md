---
tags:
  - microarchitettura
  - prestazioni
  - cap7
capitolo: 7
sezione: "7.2"
pagine_pdf: 405-406
---

# Analisi delle prestazioni e CPI

## Come si misurano le prestazioni
Il modo corretto di misurare le prestazioni è **misurare il tempo di esecuzione di un
programma di interesse**. Collezioni di programmi scelti come riferimento si chiamano
**benchmark**.

> [!warning] Le metriche ingannevoli
> La sola **frequenza di clock** non misura le prestazioni: un processore a 3 GHz può
> essere più lento di uno a 2 GHz se ha un CPI peggiore o se il compilatore genera più
> istruzioni. Lo stesso vale per il conteggio dei transistor o dei core.

## L'equazione fondamentale delle prestazioni

$$\text{Tempo di esecuzione} = \left(\text{n° istruzioni}\right) \times \left(\frac{\text{cicli}}{\text{istruzione}}\right) \times \left(\frac{\text{secondi}}{\text{ciclo}}\right)$$

ovvero

$$T_{exec} = N_{istr} \times CPI \times T_c$$

## I tre fattori
| Fattore | Da cosa dipende |
|---|---|
| **n° di istruzioni** | dal programma, dal **compilatore** e dall'**instruction set** |
| **CPI** (*cycles per instruction*) | dalla **microarchitettura** |
| **$T_c$** (periodo di clock) | dalla **microarchitettura** e dalla **tecnologia** del circuito |

- Il **CPI** è il numero di cicli di clock necessari per eseguire un'istruzione. Se
  istruzioni diverse richiedono numeri di cicli diversi, si usa il CPI **medio**,
  pesato sulla frequenza relativa di ciascun tipo di istruzione:
  $$CPI = \sum_i f_i \cdot CPI_i$$
- Il **numero di secondi per ciclo** è il **periodo di clock** $T_c$, determinato dal
  **cammino critico** del processore (→ [[Timing sequenziale - setup hold e clock skew]]).

Il reciproco del CPI è l'**IPC** (*instructions per cycle*), spesso usato per i
processori superscalari.

## Il compromesso strutturale
> [!important] Il punto centrale del capitolo 7
> Le tre microarchitetture illustrano il compromesso tra **CPI** e **$T_c$**:
> - **single-cycle**: $CPI = 1$ ma $T_c$ **grandissimo** (dettato dall'istruzione più lenta);
> - **multiciclo**: $T_c$ **piccolo** ma $CPI$ = 3–5;
> - **pipelined**: $T_c$ piccolo **e** $CPI \approx 1$ — il meglio dei due, al costo di
>   complessità di controllo (hazard, stalli, predizione dei salti).
>
> Ottimizzare uno solo dei due fattori non serve: conta il **prodotto**.

## Esempio di calcolo
Un programma di 100 miliardi di istruzioni su un processore con $CPI = 4$ e frequenza
1 GHz ($T_c = 1$ ns):

$$T_{exec} = 100 \times 10^9 \times 4 \times 1 \times 10^{-9} = 400\ \text{s}$$

## Altri fattori
Molti altri elementi influenzano le prestazioni complessive di un calcolatore: la
**gerarchia di memoria** (→ [[Metriche di prestazione - miss rate e AMAT]]), il sistema
di I/O, il sistema operativo, la qualità del compilatore.

## Da ricordare
- $T_{exec} = N_{istr} \times CPI \times T_c$: **l'equazione da sapere**.
- Numero di istruzioni ← compilatore + ISA; CPI ← microarchitettura;
  $T_c$ ← microarchitettura + tecnologia.
- Non giudicare un processore dalla sola frequenza.

## Domande flash
1. Un processore con CPI 2 a 1 GHz vs CPI 5 a 3 GHz: quale è più veloce?
2. Su quale dei tre fattori agisce il compilatore?
