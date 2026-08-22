---
Materia: Architettura degli elaboratori
tags:
  - cache
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 8.3.4-8.3.6'
Imparato: false
Ordine: 806
aliases:
  - LRU
  - write-through
  - write-back
  - block size
---
## La dimensione del blocco
> Il vantaggio di una dimensione di blocco **maggiore di una parola** è che, quando si
> verifica un miss, si caricano in cache **più parole contigue** in un solo trasferimento.

Questo sfrutta la **località spaziale**: gli accessi successivi alle parole vicine
saranno hit "gratuiti".

### Il compromesso
| Blocco grande | |
|---|---|
| ✅ meno miss **compulsory** (sfrutta la località spaziale) | |
| ✅ trasferimenti dalla memoria più efficienti (il costo è dominato dalla latenza, non dalla quantità) | |
| ❌ a parità di capacità, **meno blocchi** → **più conflict miss** | |
| ❌ **spreco di banda** se il programma non ha località spaziale | |
| ❌ maggiore **penalità di miss** (più tempo a riempire il blocco) | |

Esiste quindi una dimensione **ottima** (tipicamente 32–128 byte nelle cache reali): il
miss rate scende con $b$, poi risale.

## Politica di sostituzione
In una cache con $N > 1$ vie, in caso di miss bisogna **espellere** (*evict*) uno dei
blocchi dell'insieme.

> [!important] La scelta guidata dalla località temporale
> **Il principio di località temporale suggerisce che la scelta migliore sia espellere il
> blocco usato meno recentemente**, perché è quello con minore probabilità di essere
> riusato presto.
>
> Questa politica si chiama **LRU** (*least recently used*).

### Realizzazione
- Con $N = 2$ basta **un bit** per insieme (`U`), che indica quale delle due vie è stata
  usata meno recentemente. Semplice ed economico.
- Con $N$ grande, l'LRU esatto richiede di mantenere un **ordinamento completo** delle $N$
  vie: costoso. Si usano quindi **approssimazioni**:
  - **pseudo-LRU** (albero di bit),
  - **NMRU** (*not most recently used*),
  - **random**: si sceglie a caso. Sorprendentemente, con associatività alta le
    prestazioni sono vicine a LRU, a costo quasi nullo.

## Politiche di scrittura
Cosa fare quando il processore **scrive** un dato che sta in cache?

### Write-through (scrittura passante)
Il dato viene scritto **contemporaneamente** in cache **e** in memoria principale.
- ✅ semplice; la memoria è **sempre coerente** con la cache;
- ✅ nessun lavoro extra all'espulsione di un blocco;
- ❌ **ogni** scrittura genera traffico verso la memoria → banda consumata.

Si mitiga con un **write buffer**, che accoda le scritture verso la memoria e permette al
processore di proseguire.

### Write-back (scrittura differita)
Il dato viene scritto **solo in cache**. La memoria principale viene aggiornata **solo
quando il blocco viene espulso**.

Serve un **dirty bit** ($D$) per blocco:
- $D = 0$ → il blocco non è stato modificato: all'espulsione si può **scartare**;
- $D = 1$ → il blocco è stato modificato: all'espulsione va **riscritto** in memoria.

- ✅ scritture ripetute sullo stesso blocco costano **un solo** accesso alla memoria;
- ✅ **molto meno traffico**: è la politica dominante nelle cache moderne;
- ❌ più complessa; la memoria è temporaneamente **incoerente** (problema nei sistemi
  multiprocessore → protocolli di coerenza).

### Write allocation
In caso di **miss in scrittura**:
- **write-allocate**: si carica il blocco in cache e poi si scrive (tipico del write-back);
- **no-write-allocate**: si scrive direttamente in memoria senza caricare il blocco
  (tipico del write-through).

## Cache multilivello (cenno)
Le architetture reali usano più livelli:
- **L1** piccola e velocissima (spesso separata in L1-I e L1-D, come richiede il
  processore pipelined);
- **L2** più grande e più lenta;
- **L3** condivisa tra i core.

Ogni livello riduce il numero di accessi a quello successivo, e l'AMAT si calcola in modo
**ricorsivo** (→ [[Metriche di prestazione - miss rate e AMAT]]).


