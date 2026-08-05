---
tags:
  - MOC
  - indice
tipo: mappa-di-contenuti
fonte: Harris & Harris — Digital Design and Computer Architecture, ARM Edition
note_totali: 72
---

# 🗺️ MOC — Architettura Digitale

Indice generale degli appunti. Le note seguono **le parti evidenziate del PDF** del
libro di Harris & Harris: la selezione degli argomenti e il livello di dettaglio
rispecchiano le annotazioni, i contenuti sono riscritti in italiano.

> [!info] Come leggere i riferimenti di pagina
> Il campo `pagine_pdf` nel frontmatter di ogni nota indica le pagine **del file PDF**,
> che sono sfasate di **+20** rispetto alla numerazione stampata del libro.
> Esempio: `pagine_pdf: 26-30` → pagine 6-10 del libro.

> [!warning] Cosa non è coperto
> Non ci sono note per le parti senza evidenziazioni:
> - **Cap. 4 — Hardware Description Languages** (Verilog/VHDL): interamente escluso
> - **Cap. 7** — si ferma al **processore multiciclo**: *pipelining*, HDL del processore
>   e architetture avanzate (superscalare, out-of-order, multithreading) non trattati
> - **Cap. 9 — I/O Systems** e **Appendici A/B/C**
> - Sezioni minori: 1.7-1.8 (transistor CMOS, consumo), 6.5-6.8 (compilazione/loading, x86)

---

## 1 · Fondamenti — *From Zero to One*

Ordine di studio suggerito:

1. [[Astrazione e gestione della complessita]]
2. [[Astrazione digitale e quantita di informazione]]
3. [[Sistemi di numerazione binario e esadecimale]] ⭐ *sezione più evidenziata del capitolo*
4. [[Byte nibble word e prefissi binari]]
5. [[Addizione binaria e overflow]]
6. [[Numeri con segno - segno-modulo e complemento a due]]
7. [[Porte logiche]]
8. [[Livelli logici e margini di rumore]]

## 2 · Logica Combinatoria

1. [[Circuiti combinatori e sequenziali]]
2. [[Terminologia booleana - letterali mintermini maxtermini]]
3. [[Forme canoniche SOP e POS]]
4. [[Assiomi e teoremi dell algebra di Boole]] ⭐
5. [[Teorema di De Morgan e bubble pushing]]
6. [[Da equazioni a schemi - logica a due livelli]]
7. [[X e Z - don t care contention e nodi flottanti]]
8. [[Mappe di Karnaugh]] ⭐
9. [[Multiplexer]]
10. [[Decoder]]
11. [[Timing combinatorio - ritardo di propagazione e cammino critico]]
12. [[Glitch]]

## 3 · Logica Sequenziale

1. [[Elementi bistabili]]
2. [[Latch SR]]
3. [[Latch D]]
4. [[Flip-flop D e registri]]
5. [[Flip-flop con enable e reset]]
6. [[Progetto sincrono e race condition]]
7. [[Macchine a stati finiti - Moore e Mealy]] ⭐
8. [[Procedura di progetto di una FSM]]
9. [[Codifica degli stati - binaria e one-hot]]
10. [[Timing sequenziale - setup hold e clock skew]]
11. [[Parallelismo latenza e throughput]]

## 5 · Blocchi Digitali — *Digital Building Blocks*

**Circuiti aritmetici**
1. [[Half adder e full adder]]
2. [[Ripple carry adder]]
3. [[Carry lookahead adder]]
4. [[Sottrattori comparatori e ALU]]
5. [[Shifter e rotatori]]

**Rappresentazione dei numeri**
6. [[Notazione a virgola fissa]]
7. [[Virgola mobile IEEE 754]]

**Blocchi sequenziali e memorie**
8. [[Contatori e shift register]]
9. [[Array di memoria - organizzazione]] ⭐
10. [[DRAM SRAM e ROM]]
11. [[Register file ROM e logic array]]

## 6 · Architettura ARM

**Basi del linguaggio assembly**
1. [[Linguaggio assembly - principi di progetto]]
2. [[Registri ARM]]
3. [[Operandi - registri immediati e memoria]]
4. [[Istruzioni LDR e STR]]
5. [[Istruzioni logiche e di shift]]

**Programmazione** ⭐ *sezione più evidenziata di tutto il libro*
6. [[Flag di condizione e istruzione CMP]]
7. [[Branch ed esecuzione condizionale]]
8. [[Costrutti condizionali in assembly]]
9. [[Cicli in assembly]]
10. [[Array e modalita di indirizzamento]]
11. [[Byte caratteri ASCII e stringhe]]
12. [[Funzioni e convenzioni di chiamata]]
13. [[Lo stack]]

**Codifica**
14. [[Linguaggio macchina - formati istruzione]]

## 7 · Microarchitettura

1. [[Microarchitettura - datapath e unita di controllo]]
2. [[Analisi delle prestazioni e CPI]]
3. [[Processore single-cycle - datapath]]
4. [[Processore single-cycle - unita di controllo]]
5. [[Processore single-cycle - prestazioni]]
6. [[Processore multiciclo - datapath]] ⭐
7. [[Processore multiciclo - controllo a FSM]]
8. [[Processore multiciclo - prestazioni]]

## 8 · Sistemi di Memoria

1. [[Gerarchia di memoria e principi di localita]]
2. [[Metriche di prestazione - miss rate e AMAT]]
3. [[Cache - organizzazione e parametri]]
4. [[Cache direct mapped]]
5. [[Cache set associative e fully associative]]
6. [[Blocchi politiche di sostituzione e scrittura]]
7. [[Memoria virtuale - concetti]]
8. [[Page table e TLB]]

---

## Percorsi trasversali

Alcuni fili che attraversano più capitoli, utili per il ripasso:

| Filo conduttore | Note collegate |
|---|---|
| **Rappresentazione dei numeri** | [[Sistemi di numerazione binario e esadecimale]] → [[Numeri con segno - segno-modulo e complemento a due]] → [[Notazione a virgola fissa]] → [[Virgola mobile IEEE 754]] |
| **Timing e velocità del clock** | [[Timing combinatorio - ritardo di propagazione e cammino critico]] → [[Timing sequenziale - setup hold e clock skew]] → [[Processore single-cycle - prestazioni]] → [[Processore multiciclo - prestazioni]] |
| **Semplificazione della logica** | [[Forme canoniche SOP e POS]] → [[Assiomi e teoremi dell algebra di Boole]] → [[Teorema di De Morgan e bubble pushing]] → [[Mappe di Karnaugh]] |
| **Dal bit al processore** | [[Porte logiche]] → [[Half adder e full adder]] → [[Sottrattori comparatori e ALU]] → [[Processore single-cycle - datapath]] |
| **Memoria, dal circuito al sistema** | [[Array di memoria - organizzazione]] → [[DRAM SRAM e ROM]] → [[Cache - organizzazione e parametri]] → [[Memoria virtuale - concetti]] |
| **FSM come strumento di progetto** | [[Macchine a stati finiti - Moore e Mealy]] → [[Procedura di progetto di una FSM]] → [[Processore multiciclo - controllo a FSM]] |

---

## Struttura delle note

Ogni nota ha lo stesso schema:

- **Frontmatter YAML** con `tags`, `capitolo`, `sezione`, `pagine_pdf`
- Spiegazione discorsiva con tabelle e formule LaTeX (`$...$` inline, `$$...$$` in blocco)
- Callout Obsidian: `> [!info]`, `> [!tip]`, `> [!warning]`, `> [!important]`
- **Wikilink** `[[...]]` verso le note collegate
- **## Da ricordare** — sintesi dei punti chiave
- **## Domande flash** — autoverifica prima dell'esame

> [!tip] Suggerimento per Obsidian
> Attiva la vista **Graph** filtrando per tag (`#cap6`, `#memoria`…) per vedere come
> si collegano gli argomenti. Le "Domande flash" funzionano bene con il plugin
> *Spaced Repetition* se le converti in formato `domanda::risposta`.
