---
Materia: Architettura degli elaboratori
tags:
  - memoria_virtuale
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 8.4.2-8.4.4'
Imparato: false
Ordine: 808
aliases:
  - page table
  - TLB
  - tabella delle pagine
---

# Page table, TLB e processi multipli

## La page table
Il processore usa una **page table** (tabella delle pagine) per tradurre gli indirizzi
virtuali in fisici.

Struttura logica:
- **una voce** (*page table entry*, **PTE**) per **ogni pagina virtuale**;
- la voce è indicizzata dal **VPN** (numero di pagina virtuale);
- ogni voce contiene:
  - un **bit di validità** ($V$): la pagina è presente in memoria fisica?
  - il **PPN** (numero di pagina fisica) corrispondente;
  - bit di **protezione** e di stato (lettura/scrittura/esecuzione, dirty, accessed).

### Procedura di traduzione
1. Estrai il **VPN** dall'indirizzo virtuale.
2. Usa il VPN come **indice** nella page table.
3. Se $V = 1$: prendi il **PPN** dalla voce e concatenalo all'**offset** → indirizzo fisico.
4. Se $V = 0$: **page fault** — il sistema operativo carica la pagina dal disco.

### Dove sta la page table
> La page table **può essere memorizzata in qualunque punto della memoria fisica**, a
> discrezione del sistema operativo.

Il processore usa in genere un registro dedicato, il **page table register**, che contiene
l'**indirizzo base** della page table.

## Il problema delle prestazioni
> [!warning] Il costo nascosto
> La memoria virtuale avrebbe un **impatto severo sulle prestazioni** se ogni accesso alla
> memoria richiedesse un **accesso alla page table** (che sta in memoria!).
>
> Significherebbe **due** accessi in DRAM per **ogni** accesso del programma: uno per
> tradurre e uno per il dato. Le prestazioni si dimezzerebbero.

### Il problema della dimensione
Con indirizzi a 32 bit e pagine di 4 KB, la page table ha $2^{20}$ = **circa un milione
di voci**. A 4 byte per voce sono **4 MB per processo** — inaccettabile. Da qui le
**page table multilivello** (gerarchiche), in cui solo le porzioni effettivamente usate
sono materializzate.

## Il TLB
La soluzione al problema delle prestazioni è il **TLB** (*translation lookaside
buffer*): una **cache delle traduzioni più recenti**.

Caratteristiche:
- **piccolo** (tipicamente 16–512 voci) e quindi **veloce**;
- di norma **completamente associativo**, per non avere conflitti;
- ogni voce contiene un **VPN** (il tag) e il **PPN** corrispondente.

### Funzionamento
1. Il processore presenta il VPN al TLB.
2. **TLB hit** → la traduzione arriva in **un ciclo**, senza accedere alla memoria.
3. **TLB miss** → si consulta la page table in memoria (e si aggiorna il TLB).

Il TLB funziona **grazie alla località**: un programma accede ripetutamente a poche
pagine, quindi poche traduzioni coprono la grande maggioranza degli accessi. Gli hit rate
tipici sono superiori al **99%**.

> [!important] Perché il TLB è così efficace
> Ogni voce del TLB copre un'intera **pagina** (4 KB = 1024 word). Quindi anche un TLB da
> 64 voci copre 256 KB di dati attivi. È il rapporto tra dimensione della pagina e
> dimensione della voce a rendere il TLB sproporzionatamente efficace rispetto alla sua
> dimensione.

## Processi multipli
> I calcolatori moderni eseguono tipicamente **più programmi o processi
> contemporaneamente**.

Ogni processo ha il **proprio spazio di indirizzamento virtuale** e la **propria page
table**. Il sistema operativo:
- mantiene una page table distinta per ciascun processo;
- al **cambio di contesto** aggiorna il **page table register** con la tabella del nuovo
  processo;
- **invalida** (o marca con un identificatore di processo, **ASID**) le voci del TLB, che
  altrimenti conterrebbero traduzioni del processo precedente.

Questo è il meccanismo che realizza la **protezione**: un processo non può accedere alle
pagine fisiche di un altro, perché la sua page table semplicemente non le mappa.

## Memoria virtuale e cache insieme
L'ordine delle operazioni conta:
- **PIPT** (*physically indexed, physically tagged*): prima la traduzione, poi la cache.
  Semplice ma serializza TLB e cache.
- **VIPT** (*virtually indexed, physically tagged*): si indicizza la cache con i bit
  dell'offset (non tradotti) **in parallelo** all'accesso al TLB, e si confronta il tag
  fisico dopo. È la soluzione usata nelle cache L1 reali, perché nasconde la latenza del
  TLB.

## Da ricordare
- **PTE** = bit V + **PPN** + bit di protezione; indicizzata dal **VPN**.
- La page table sta in **memoria fisica**; il **page table register** ne contiene la base.
- Senza TLB servirebbero **due accessi in memoria** per ogni accesso del programma.
- Il **TLB** è una cache delle traduzioni, piccola e **fully associative**.
- **Un processo = una page table**; il cambio di contesto richiede di invalidare il TLB.

## Domande flash
1. Cosa contiene una voce della page table?
2. Quanti accessi in memoria costa un accesso a dato con TLB hit? E con TLB miss?
3. Perché il TLB da poche decine di voci ha un hit rate superiore al 99%?
4. Come garantisce la memoria virtuale la protezione tra processi?
