---
Materia: Architettura degli elaboratori
tags:
  - cache
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 8.3.1'
Imparato: false
Ordine: 804
aliases:
  - direct mapped
  - mappatura diretta
  - tag
---

# Cache direct mapped

## Definizione
Una cache **direct mapped** (a mappatura diretta) ha **un solo blocco per insieme**,
quindi è organizzata in **$S = B$ insiemi**. È il caso $N = 1$.

Ogni indirizzo di memoria mappa su **esattamente un** blocco della cache.

## La mappatura
L'insieme di destinazione si ricava dai bit **meno significativi** dell'indirizzo
(esclusi i bit di offset). In pratica:

$$\text{set} = (\text{indirizzo del blocco}) \bmod S$$

Poiché $S$ è una potenza di 2, il modulo è semplicemente la lettura di alcuni bit
dell'indirizzo.

## La suddivisione dell'indirizzo
Un indirizzo a 32 bit si scompone in campi:

```
 31                        |          |       |      0
+--------------------------+----------+-------+------+
|           TAG            |   SET    | BLOCK | BYTE |
|                          |          | OFFSET| OFFS |
+--------------------------+----------+-------+------+
```

| Campo | Larghezza | Funzione |
|---|---|---|
| **byte offset** | 2 bit | seleziona il byte dentro la parola (memoria byte-addressable) |
| **block offset** | $\log_2 b$ | seleziona la **parola** dentro il blocco |
| **set** | $\log_2 S$ | seleziona **quale insieme** della cache |
| **tag** | il resto | identifica **quale** indirizzo è memorizzato |

## Il tag: perché serve
> Poiché **molti indirizzi mappano su un solo insieme**, la cache deve tenere traccia di
> **quale** di questi indirizzi è effettivamente memorizzato in quel momento.

Il **tag** è la parte alta dell'indirizzo, memorizzata insieme al dato. In caso di
accesso:
1. si usa il campo **set** per individuare la riga;
2. si **confronta** il tag dell'indirizzo richiesto con il tag memorizzato;
3. se coincidono **e** il blocco è valido → **hit**; altrimenti → **miss**.

## Il bit di validità (V)
> A volte, come **all'accensione** del calcolatore, gli insiemi della cache contengono
> dati **privi di significato**.

Serve quindi un **bit di validità** ($V$) per ogni blocco:
- $V = 1$ → il blocco contiene dati validi;
- $V = 0$ → il blocco è vuoto/non inizializzato, e qualunque accesso è un **miss**.

All'accensione tutti i bit $V$ sono azzerati.

### Condizione di hit
$$\text{hit} = V \ \text{AND}\ (\text{tag memorizzato} = \text{tag richiesto})$$

## I conflict miss
> [!warning] Il limite della direct mapped
> Quando **due indirizzi usati di recente mappano sullo stesso blocco** della cache, si
> verifica un **conflict miss** (miss di conflitto): il secondo accesso espelle il primo,
> e viceversa.
>
> Nel caso peggiore un ciclo che accede alternativamente a due indirizzi mappati sullo
> stesso set produce **il 100% di miss**, pur usando solo 2 parole su una cache
> capacissima. Questo fenomeno si chiama **thrashing**.

Rimedi: aumentare l'**associatività**
(→ [[Cache set associative e fully associative]]) oppure modificare il *layout* dei dati.

## Le tre categorie di miss
| Tipo | Causa |
|---|---|
| **compulsory** (o *cold start*) | il blocco non è **mai** stato caricato: primo accesso |
| **capacity** | la cache è **troppo piccola** per contenere tutti i dati attivi |
| **conflict** | più indirizzi si contendono lo **stesso insieme**, anche se la cache avrebbe spazio altrove |

## Esempio di calcolo
Cache direct mapped, $C = 8$ parole, $b = 1$ parola, indirizzi a 32 bit:
- $B = C/b = 8$ blocchi, $S = B = 8$ insiemi
- byte offset: 2 bit
- block offset: $\log_2 1 = 0$ bit
- set: $\log_2 8 = 3$ bit
- tag: $32 - 3 - 0 - 2 = 27$ bit

L'indirizzo `0x00000004` (parola 1) mappa sull'insieme 1; `0x00000024` (parola 9) mappa
**anch'esso** sull'insieme 1 → potenziale conflitto.

## Da ricordare
- Direct mapped: **1 blocco per set**, $S = B$.
- L'indirizzo si scompone in **tag | set | block offset | byte offset**.
- Il **tag** discrimina tra i molti indirizzi che mappano sullo stesso set.
- Il **bit V** gestisce i blocchi non inizializzati.
- Tre tipi di miss: **compulsory, capacity, conflict**.

## Domande flash
1. In una cache direct mapped da 16 blocchi di 4 parole, quanti bit di set e di block
   offset ci sono?
2. Che cos'è il thrashing e come si evita?
3. Perché serve il bit di validità e non basta il tag?
