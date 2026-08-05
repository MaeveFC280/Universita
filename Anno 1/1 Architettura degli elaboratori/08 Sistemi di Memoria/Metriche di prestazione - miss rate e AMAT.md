---
Materia: Architettura degli elaboratori
tags:
  - memoria
  - prestazioni
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 8.2'
Imparato: false
Ordine: 802
aliases:
  - miss rate
  - hit rate
  - AMAT
---

# Metriche di prestazione: miss rate, hit rate e AMAT

## Le metriche
Le prestazioni del sistema di memoria si misurano con il **miss rate** (o **hit rate**) e
con il **tempo medio di accesso alla memoria**.

- **hit** (successo): il dato cercato **è** presente nel livello considerato.
- **miss** (fallimento): il dato **non** è presente e va recuperato dal livello inferiore.

$$MR = \frac{\text{numero di miss}}{\text{numero totale di accessi}} = 1 - HR$$

$$HR = \frac{\text{numero di hit}}{\text{numero totale di accessi}} = 1 - MR$$

## AMAT
L'**AMAT** (*average memory access time*, tempo medio di accesso alla memoria) è il tempo
medio che il processore deve attendere per un accesso in lettura o scrittura.

Nel caso di una gerarchia a tre livelli (cache, memoria principale, memoria virtuale):

$$AMAT = t_{cache} + MR_{cache}\big(t_{MM} + MR_{MM}\, t_{VM}\big)$$

dove:
| Simbolo | Significato |
|---|---|
| $t_{cache}$, $t_{MM}$, $t_{VM}$ | tempi di accesso a cache, memoria principale, memoria virtuale (disco) |
| $MR_{cache}$, $MR_{MM}$ | miss rate della cache e della memoria principale |

### Come si legge la formula
Il tempo di accesso alla cache si paga **sempre**. Il tempo della memoria principale si
paga **solo** quando la cache fallisce (probabilità $MR_{cache}$). Il tempo del disco si
paga solo quando **entrambe** fallitcono.

La struttura è **ricorsiva**: si può estendere a più livelli di cache (L1, L2, L3)
annidando ulteriormente i termini.

## Esempio
Cache con $t_{cache} = 1$ ciclo e $MR = 10\%$; memoria principale con $t_{MM} = 100$
cicli. Ignorando la memoria virtuale:

$$AMAT = 1 + 0{,}10 \times 100 = 11\ \text{cicli}$$

Migliorando il miss rate al 2%:
$$AMAT = 1 + 0{,}02 \times 100 = 3\ \text{cicli}$$

> [!important] La lezione numerica
> Con una penalità di miss così alta, **una piccola variazione del miss rate ha un
> effetto enorme sull'AMAT**. È per questo che si investe tanta complessità
> (associatività, blocchi, politiche di sostituzione) per guadagnare pochi punti
> percentuali di miss rate.

## Impatto sulle prestazioni globali
L'AMAT entra direttamente nel CPI effettivo del processore:

$$CPI_{effettivo} = CPI_{ideale} + \text{cicli di stallo per memoria per istruzione}$$

→ [[Analisi delle prestazioni e CPI]]

## Da ricordare
- $MR = 1 - HR$.
- $AMAT = t_{cache} + MR_{cache}(t_{MM} + MR_{MM} t_{VM})$ — **formula da sapere**.
- Il tempo del livello superiore si paga sempre; quelli inferiori solo in caso di miss.
- Con penalità di miss grandi, pochi punti di miss rate cambiano tutto.

## Domande flash
1. Con $t_{cache}=1$, $MR=5\%$, $t_{MM}=80$: quanto vale l'AMAT?
2. Perché $t_{cache}$ non è moltiplicato per nulla nella formula?
