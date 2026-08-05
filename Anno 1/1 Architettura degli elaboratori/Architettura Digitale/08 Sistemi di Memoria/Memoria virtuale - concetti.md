---
tags: [architettura, memoria, virtuale, cap8]
capitolo: 8
sezione: "8.4"
pagine_pdf: 524-528
---

# Memoria virtuale: concetti

## Perché esiste
La maggior parte dei calcolatori moderni ha un **disco** (magnetico o a stato solido)
come livello più basso della gerarchia. Rispetto alla DRAM il disco è **enormemente più
capiente** ed **enormemente più lento**.

La **memoria virtuale** usa la memoria principale (DRAM) come una **cache del disco**,
fornendo tre benefici:
1. l'**illusione di una memoria molto più grande** di quella fisicamente presente;
2. la **protezione** e l'isolamento tra programmi diversi;
3. la **rilocazione**: ogni programma può essere compilato per gli stessi indirizzi.

## Il disco fisico (per capire i tempi)
Un **hard disk** contiene uno o più **piatti** rigidi rivestiti di materiale magnetico,
che ruotano. Una **testina** si sposta nella posizione corretta sul disco e legge o
scrive i dati **magneticamente**.

I tempi di accesso (seek + rotazione) sono nell'ordine dei **millisecondi**: milioni di
cicli di clock. Gli **SSD** riducono questo tempo di ordini di grandezza ma restano
lentissimi rispetto alla DRAM.

## Indirizzi virtuali e fisici
> I programmi possono accedere a dati in qualunque punto della memoria virtuale, quindi
> devono usare **indirizzi virtuali**.

- **Indirizzo virtuale**: quello usato dal programma. Lo spazio virtuale è grande (es.
  $2^{32}$ o $2^{48}$ byte).
- **Indirizzo fisico**: quello effettivo della DRAM. Lo spazio fisico è più piccolo.

In un sistema con memoria virtuale, **i programmi usano indirizzi virtuali**, così che
programmi diversi possano essere compilati e caricati **senza conoscere** dove finiranno
in memoria fisica, e senza potersi pestare i piedi a vicenda.

## Pagine
La memoria virtuale è divisa in **pagine virtuali**, tipicamente di **4 KB**. La memoria
fisica è divisa in **pagine fisiche** (o *frame*) della **stessa dimensione**.

Una pagina è l'analogo del **blocco** in una cache — solo molto più grande, perché la
penalità di miss (accesso al disco) è enorme e conviene ammortizzarla su molti dati.

## Traduzione degli indirizzi
Il processo di determinare l'indirizzo fisico a partire da quello virtuale si chiama
**traduzione degli indirizzi** (*address translation*).

La chiave: **la dimensione della pagina è la stessa** in memoria virtuale e fisica, quindi
i bit **bassi** dell'indirizzo (l'**offset di pagina**) **non cambiano**:

```
indirizzo virtuale:   [ VPN (virtual page number) | page offset ]
                              |  traduzione            | invariato
                              v                        v
indirizzo fisico:     [ PPN (physical page number)| page offset ]
```

I bit **più significativi** dell'indirizzo virtuale o fisico specificano il **numero di
pagina**; i bit meno significativi specificano l'**offset** dentro la pagina.

Con pagine di 4 KB, l'offset è di **12 bit** ($2^{12} = 4096$).

## Mappatura completamente associativa
> Per **evitare i page fault causati da conflitti**, **qualunque** pagina virtuale può
> mappare su **qualunque** pagina fisica.

Cioè la memoria virtuale si comporta come una cache **fully associative**
(→ [[Cache set associative e fully associative]]). È una scelta obbligata: un page fault
costa milioni di cicli, quindi ogni conflitto evitabile va evitato.

## Page fault
Se la pagina virtuale richiesta **non è presente** in memoria fisica, si ha un **page
fault**: il sistema operativo la carica dal disco in una pagina fisica libera (o ne
espelle una, con politica **LRU** approssimata) e riprende l'esecuzione.

## Analogia cache ↔ memoria virtuale
| Cache | Memoria virtuale |
|---|---|
| blocco | **pagina** |
| miss | **page fault** |
| tag | numero di pagina virtuale (**VPN**) |
| block offset | **page offset** |
| dimensione blocco (~64 B) | dimensione pagina (~4 KB) |
| gestita dall'**hardware** | gestita dal **sistema operativo** |

## Da ricordare
- La memoria virtuale usa la DRAM come **cache del disco**; benefici: capacità apparente,
  **protezione**, rilocazione.
- Pagine tipicamente di **4 KB**; l'**offset di pagina non viene tradotto**.
- Traduzione: VPN → PPN, offset invariato.
- Mappatura **completamente associativa** per evitare i conflitti.

## Domande flash
1. Con pagine di 4 KB e indirizzi a 32 bit: quanti bit di VPN e quanti di offset?
2. Perché l'offset di pagina non cambia nella traduzione?
3. Perché la memoria virtuale è fully associative e non direct mapped?

Collegato a: [[Page table e TLB]]
