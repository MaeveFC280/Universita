---
tags: [architettura, memoria, cache, cap8]
capitolo: 8
sezione: "8.3.2 - 8.3.3"
pagine_pdf: 514-516
---

# Cache set associative e fully associative

## Cache N-way set associative
Una cache **$N$-way set associative** riduce i conflitti fornendo **$N$ blocchi in ogni
insieme**, tra i quali il dato può essere collocato.

- Numero di insiemi: $S = B/N$
- Un indirizzo mappa su **un solo insieme**, ma può stare in **una qualunque delle $N$
  vie** di quell'insieme.

### Funzionamento dell'accesso
1. Il campo **set** dell'indirizzo seleziona l'insieme.
2. **Tutti gli $N$ tag** dell'insieme vengono confrontati **in parallelo** con il tag
   richiesto.
3. Se uno coincide (e il blocco è valido) → **hit**; un **multiplexer** seleziona il dato
   della via corretta.

Serve quindi $N$ comparatori in parallelo: **più associatività = più hardware e più
consumo**, ma meno miss.

### Relazione con la direct mapped
> Una cache **direct mapped** è un altro nome per una cache **one-way set associative**:
> $N = 1$.

## Cache fully associative
Una cache **fully associative** contiene **un unico insieme** con $B$ vie, dove $B$ è il
numero totale di blocchi. Cioè $S = 1$, $N = B$.

Un dato può stare in **qualunque** blocco della cache: la mappatura è completamente
libera, quindi **non esistono conflict miss**.

- Non c'è campo **set** nell'indirizzo: tutti i bit non di offset sono **tag**.
- L'accesso richiede di confrontare il tag con **tutti** i $B$ tag simultaneamente; un
  multiplexer seleziona il dato in caso di hit.
- Le cache fully associative hanno il **miss rate più basso** a parità di capacità, ma
  sono **costosissime** in hardware (un comparatore per blocco): si usano solo per cache
  **piccole**, tipicamente i **TLB** (→ [[Page table e TLB]]).

## Confronto complessivo
| | direct mapped | $N$-way | fully associative |
|---|---|---|---|
| $S$ (insiemi) | $B$ | $B/N$ | **1** |
| $N$ (vie) | **1** | $N$ | $B$ |
| comparatori | 1 | $N$ | $B$ |
| conflict miss | **molti** | pochi | **nessuno** |
| costo/consumo | **minimo** | medio | **massimo** |
| tempo di accesso | **minimo** | medio | massimo |
| serve politica di sostituzione? | **no** (una sola scelta) | sì | sì |

> [!important] Il compromesso
> **Le cache set associative hanno in generale un miss rate più basso delle direct
> mapped** di pari capacità. Ma l'associatività costa: più comparatori, un multiplexer
> più grande, un tempo di hit più lungo, più energia per accesso.
>
> In pratica: le cache L1 usano associatività bassa (2-8 vie) perché la **velocità** è
> critica; le cache L2/L3 usano associatività più alta perché conta il **miss rate**.
> Oltre le 8 vie il guadagno in miss rate è marginale (legge dei ritorni decrescenti).

## Politica di sostituzione
Con $N > 1$ bisogna decidere **quale** dei blocchi dell'insieme espellere in caso di miss:
è la politica di sostituzione. → [[Blocchi politiche di sostituzione e scrittura]]

## Da ricordare
- $N$-way: $S = B/N$; $N$ comparatori in parallelo + mux di selezione.
- Direct mapped = **one-way** set associative.
- Fully associative: $S = 1$, nessun conflict miss, costo massimo.
- Più associatività → meno miss, ma più hardware e hit più lento.

## Domande flash
1. Una cache 4-way con 32 blocchi: quanti insiemi ha? Quanti bit di set?
2. Perché una fully associative non ha conflict miss?
3. Perché la direct mapped non richiede una politica di sostituzione?
