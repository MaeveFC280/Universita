---
Materia: Architettura degli elaboratori
tags:
  - FSM
  - Binario
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 3.4.4'
Imparato: false
Ordine: 309
aliases:
  - codifica degli stati
  - one-hot
  - state encoding
---
La codifica degli stati (e delle uscite) è in linea di principio **arbitraria**: una
scelta diversa produce un **hardware diverso**, con equazioni booleane, area e ritardi
diversi, pur realizzando la stessa funzione.

Non esiste un modo semplice per trovare la codifica migliore, se non provarle
**tutte** — cosa **impraticabile** quando gli stati sono molti. Tuttavia:
- spesso si trova una buona codifica **per ispezione**, facendo in modo che stati o
  uscite **correlati condividano dei bit**;
- gli strumenti **CAD** esplorano automaticamente lo spazio delle codifiche.

## Le due codifiche principali

### Codifica binaria
Ogni stato è rappresentato come un **numero binario**. Poiché $K$ numeri binari si
rappresentano con $\lceil \log_2 K \rceil$ bit, un sistema con $K$ stati richiede solo
$\lceil \log_2 K \rceil$ bit di stato.

### Codifica one-hot
Si usa **un bit di stato separato per ogni stato**: $K$ stati → $K$ bit, di cui
**esattamente uno** è "caldo" (TRUE) in ogni istante.

### Codifica one-cold
Variante: $K$ stati con $K$ bit, di cui esattamente uno è **FALSE**.

## Confronto
| | binaria | one-hot |
|---|---|---|
| bit di stato per $K$ stati | $\lceil \log_2 K \rceil$ | $K$ |
| numero di flip-flop | **minimo** | elevato |
| logica di stato successivo/uscita | più complessa | **molto semplice** |
| decodifica dello stato | richiede un decoder | immediata (un bit = uno stato) |
| velocità | in genere minore | in genere **maggiore** |

> [!tip] Quando usare cosa
> - **Binaria**: quando gli stati sono molti e i flip-flop costano (es. contatori:
>   un contatore modulo 16 con codifica binaria usa 4 flip-flop, con one-hot ne
>   userebbe 16).
> - **One-hot**: quando gli stati sono pochi, si vuole logica veloce e semplice, o si
>   lavora su **FPGA**, dove i flip-flop sono abbondanti e "gratis" mentre la logica
>   combinatoria è la risorsa scarsa.

## Da ricordare
- Non esiste una regola per la codifica ottima; si va per ispezione o con il CAD.
- Binaria: pochi flip-flop, più logica. One-hot: molti flip-flop, poca logica.
- Buona euristica: fai condividere bit a stati/uscite correlati.

## Domande flash
1. Quanti bit servono per 9 stati in binario? E in one-hot?
2. Perché su FPGA si preferisce spesso one-hot?
