---
Materia: Architettura degli elaboratori
tags:
  - prestazioni
  - logica_sequenziale
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 3.6'
Imparato: false
Ordine: 311
aliases:
  - latenza
  - throughput
  - pipelining
  - parallelismo
---
## Le due metriche
La velocità di un sistema si caratterizza con **latenza** e **throughput** dell'informazione che lo attraversa. Si definisce **token** un gruppo di ingressi che vengono elaborati insieme per produrre un gruppo di uscite.

| Metrica | Definizione |
|---|---|
| **Latenza** | il tempo che un **singolo token** impiega dall'inizio alla fine dell'elaborazione |
| **Throughput** | il **numero di token** che il sistema può produrre **per unità di tempo** |

> [!important] Non sono la stessa cosa
> Migliorare il throughput **non** significa migliorare la latenza, e spesso il pipelining **peggiora** la latenza di un singolo token pur aumentando il throughput.

## Parallelismo
Il throughput si può migliorare elaborando **più token contemporaneamente**: è il **parallelismo**, che si presenta in due forme.

### Parallelismo spaziale
Si duplica l'hardware: **più copie** dello stesso blocco elaborano token diversi **nello stesso momento**.
- Costo: area (hardware replicato).
- Latenza del singolo token: **invariata**.

### Parallelismo temporale (pipelining)
Il compito è suddiviso in **stadi**, come una catena di montaggio. In ogni istante ogni stadio lavora su un **token diverso**, così che più token si **sovrappongono** nel tempo. Il parallelismo temporale è comunemente chiamato **pipelining**.
- Costo: registri di pipeline tra gli stadi, e complessità di controllo.
- Latenza del singolo token: **peggiora** (attraversa tutti i registri intermedi).

## Relazioni
Se un sistema senza parallelismo elabora un token in tempo $L$ (latenza), allora:
$$\text{throughput} = \frac{1}{L}$$

Con parallelismo di grado $P$ (spaziale con $P$ copie, o pipeline con $P$ stadi bilanciati):
$$\text{throughput} = \frac{P}{L}$$

Nel pipelining con $P$ stadi, ogni stadio dura $L/P$ (più l'overhead dei registri) e il throughput ideale è un token per ciclo.

> [!tip] Il limite pratico del pipelining
> Gli stadi devono essere **bilanciati**: il ciclo di clock è dettato dallo stadio più lento. E ogni stadio aggiunge l'overhead temporale $t_{pcq} + t_{setup}$ descritto nei [[Timing sequenziale - setup hold e clock skew|vincoli di timing sequenziale]], quindi oltre un certo numero di stadi il guadagno svanisce.
