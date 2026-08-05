---
Materia: Architettura degli elaboratori
tags:
  - cache
  - memoria
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 8.3'
Imparato: false
Ordine: 803
aliases:
  - cache
  - capacità
  - associatività
---

# Cache: organizzazione e parametri

## Cosa fa una cache
Una **cache** conserva i dati di memoria usati più comunemente. Il numero di parole di
dati che può contenere è la sua **capacità** ($C$).

Quando il processore tenta di accedere a un dato, **controlla prima nella cache**:
- se il dato c'è → **hit**, l'accesso è rapidissimo;
- se non c'è → **miss**, il dato viene prelevato dalla memoria principale, **copiato in
  cache** e fornito al processore.

## I parametri fondamentali
Le cache si specificano con quattro parametri:

| Parametro | Simbolo | Significato |
|---|---|---|
| **capacità** | $C$ | numero totale di parole di dati contenute |
| **dimensione del blocco** | $b$ | numero di parole caricate insieme in una riga |
| **numero di blocchi** | $B = C/b$ | numero totale di blocchi nella cache |
| **numero di insiemi** | $S$ | numero di *set* in cui la cache è organizzata |
| **grado di associatività** | $N = B/S$ | numero di blocchi per insieme (*ways*) |

Relazioni chiave:
$$B = \frac{C}{b} \qquad\qquad N = \frac{B}{S}$$

## Come è organizzata
Una cache è organizzata in **$S$ insiemi** (*sets*), ognuno dei quali contiene **uno o più
blocchi** (*blocks*, o *lines*). Ogni blocco contiene $b$ parole di dati contigue, più
informazioni di controllo (tag e bit di validità).

## Il problema della cache ideale
> Una cache **ideale** anticiperebbe **tutti** i dati che il processore userà e li
> avrebbe già pronti. Ma questo richiederebbe di conoscere il futuro: è impossibile.

Le cache reali si affidano quindi ai **principi di località**
(→ [[Gerarchia di memoria e principi di localita]]):
- la **località temporale** giustifica il **conservare** i dati usati di recente;
- la **località spaziale** giustifica il **caricare blocchi** di più parole contigue:
  quando il processore accede a un dato, è probabile che acceda presto a quelli vicini.

## Come si categorizzano le cache
> Le cache si categorizzano in base al **numero di blocchi per insieme**.

| $N$ (blocchi per set) | Tipo di cache |
|---|---|
| $N = 1$ | **direct mapped** ($S = B$) |
| $1 < N < B$ | **$N$-way set associative** |
| $N = B$ ($S=1$) | **fully associative** |

→ [[Cache direct mapped]] · [[Cache set associative e fully associative]]

## Le tre domande di progetto
Per ogni cache bisogna decidere:
1. **Dove** può stare un dato (mappatura → direct mapped / set associative / fully
   associative)?
2. **Quale** blocco sostituire in caso di miss (politica di **sostituzione** → LRU)?
3. **Come** gestire le scritture (write-through / write-back)?

→ [[Blocchi politiche di sostituzione e scrittura]]

## Da ricordare
- $C$ capacità, $b$ dimensione blocco, $B = C/b$ blocchi, $S$ insiemi, $N = B/S$ vie.
- Le cache si classificano per **numero di blocchi per insieme**.
- La cache ideale è impossibile: si sfruttano i principi di località.

## Domande flash
1. Una cache di 8 KB con blocchi di 4 parole (32 bit): quanti blocchi ha?
2. Se $B=64$ e $S=16$, che tipo di cache è?
