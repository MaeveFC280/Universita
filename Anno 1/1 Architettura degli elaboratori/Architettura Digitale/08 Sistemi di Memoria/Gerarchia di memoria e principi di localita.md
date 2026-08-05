---
tags: [architettura, memoria, gerarchia, cap8]
capitolo: 8
sezione: "8.1"
pagine_pdf: 503-507
---

# Gerarchia di memoria e principi di località

## Il problema
Le prestazioni di un calcolatore dipendono **tanto dal sistema di memoria quanto dal
processore**. Il processore ideale vorrebbe una memoria **grande, veloce ed economica**:
tre requisiti **incompatibili** tra loro.

- Le memorie **grandi** sono lente (più indirizzi da decodificare, fili più lunghi).
- Le memorie **veloci** sono costose (SRAM: 6 transistor per bit).
- Il **tempo di accesso alla DRAM è da 1 a 2 ordini di grandezza più lungo** del periodo
  di clock del processore.

Questo divario — il *memory wall* — è cresciuto nel tempo, perché la velocità dei
processori è aumentata più rapidamente di quella delle DRAM.

## La soluzione: la gerarchia
Si costruisce un sistema di memoria a **livelli**: memorie piccole e veloci vicino al
processore, memorie grandi e lente lontano.

> L'insieme dei livelli, se ben progettato, **fornisce l'illusione** di una memoria
> grande **e** veloce, **a un costo minore** di una singola memoria grande e veloce.

| Livello | Tecnologia | Dimensione tipica | Tempo di accesso |
|---|---|---|---|
| **registri** | flip-flop / SRAM | ~100 byte | 1 ciclo |
| **cache** | **SRAM** | KB – MB | pochi cicli |
| **memoria principale** | **DRAM** | GB | decine-centinaia di cicli |
| **disco** (memoria virtuale) | HDD magnetico / **SSD** flash | TB | milioni di cicli |

Le memorie dei calcolatori sono realizzate principalmente con **DRAM** e **SRAM**
(→ [[DRAM SRAM e ROM]]).

## I livelli in dettaglio
- La **memoria principale** è costruita con chip **DRAM**.
- La **cache** conserva i dati usati più di frequente; è realizzata in **SRAM**, quindi
  veloce. Può contenere sia istruzioni sia dati (nel testo si parla in generale del loro
  contenuto come "dati").
- Il **terzo livello** della gerarchia è il **disco**:
  - **hard disk drive (HDD)**, basato su memorizzazione **magnetica**;
  - **solid state drive (SSD)**, basato sulla tecnologia **flash**, alternativa cada
    volta più diffusa perché molto più veloce (pur restando lentissimo rispetto alla
    DRAM).
  - Il disco **fornisce l'illusione di una capacità maggiore di quella realmente
    disponibile** in memoria principale, tramite la **memoria virtuale**
    (→ [[Memoria virtuale - concetti]]).

## I due principi di località
Perché la gerarchia funzioni, gli accessi del programma devono essere **prevedibili**.
E lo sono, per due ragioni empiriche fondamentali:

### Località temporale
> Se un dato è stato usato **di recente**, è probabile che venga usato **ancora presto**.

Esempio: la variabile contatore di un ciclo, l'istruzione al centro di un loop.
Conseguenza: **conserva** in cache i dati appena usati.

### Località spaziale
> Se il processore accede a **un** dato, è probabile che accederà presto a dati con
> indirizzi **vicini**.

Esempio: la scansione sequenziale di un array, il flusso sequenziale delle istruzioni.
Conseguenza: quando si preleva un dato, **preleva anche i suoi vicini** (un intero
**blocco**).

> [!important] La sintesi
> La cache sfrutta la **località temporale** conservando i dati recenti, e la **località
> spaziale** caricando blocchi contigui. Sono queste due proprietà dei programmi reali —
> non un teorema, ma un fatto statistico — a rendere efficace tutta la gerarchia.

## Da ricordare
- La gerarchia dà **l'illusione** di una memoria grande e veloce a costo contenuto.
- Registri → cache (SRAM) → memoria principale (DRAM) → disco (HDD/SSD).
- L'accesso alla DRAM è **1-2 ordini di grandezza** più lento del ciclo di clock.
- **Località temporale** = riuso nel tempo. **Località spaziale** = riuso di indirizzi
  vicini.

## Domande flash
1. Perché non si costruisce tutta la memoria in SRAM?
2. Quale principio di località giustifica i blocchi di cache maggiori di una parola?
3. Che illusione fornisce il disco?
