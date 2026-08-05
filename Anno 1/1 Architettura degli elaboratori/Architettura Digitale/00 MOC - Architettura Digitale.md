---
tags: [MOC, architettura]
libro: "Harris & Harris - Digital Design and Computer Architecture, ARM Edition"
---

# 🗺️ MOC — Architettura Digitale

Mappa dei contenuti (*Map of Content*) di questo vault. Le note seguono la traccia delle
parti **evidenziate nel PDF**: capitoli 1, 2, 3, 5, 6, 7 (fino al multiciclo) e 8.
Il capitolo 4 (Verilog/HDL), il capitolo 9 (I/O) e le appendici non risultano annotati.

> [!tip] Come usare queste note
> Segui l'ordine dell'indice: ogni nota è autoconclusiva ma i wikilink collegano i
> concetti che si richiamano tra capitoli. Ogni nota termina con **Da ricordare**
> (sintesi) e **Domande flash** (autoverifica). Il formulario è in
> [[99 Formulario e sigle]].

---

## 📘 1 — Fondamenti (*From Zero to One*)
1. [[Astrazione e gestione della complessita]]
2. [[Astrazione digitale e quantita di informazione]]
3. [[Sistemi di numerazione binario e esadecimale]]
4. [[Byte nibble word e prefissi binari]]
5. [[Addizione binaria e overflow]]
6. [[Numeri con segno - segno-modulo e complemento a due]]
7. [[Porte logiche]]
8. [[Livelli logici e margini di rumore]]

## 📗 2 — Logica combinatoria
1. [[Circuiti combinatori e sequenziali]]
2. [[Terminologia booleana - letterali mintermini maxtermini]]
3. [[Forme canoniche SOP e POS]]
4. [[Assiomi e teoremi dell algebra di Boole]]
5. [[Teorema di De Morgan e bubble pushing]]
6. [[Da equazioni a schemi - logica a due livelli]]
7. [[X e Z - don t care contention e nodi flottanti]]
8. [[Mappe di Karnaugh]]
9. [[Multiplexer]]
10. [[Decoder]]
11. [[Timing combinatorio - ritardo di propagazione e cammino critico]]
12. [[Glitch]]

## 📙 3 — Logica sequenziale
1. [[Elementi bistabili]]
2. [[Latch SR]]
3. [[Latch D]]
4. [[Flip-flop D e registri]]
5. [[Flip-flop con enable e reset]]
6. [[Progetto sincrono e race condition]]
7. [[Macchine a stati finiti - Moore e Mealy]]
8. [[Procedura di progetto di una FSM]]
9. [[Codifica degli stati - binaria e one-hot]]
10. [[Timing sequenziale - setup hold e clock skew]]
11. [[Parallelismo latenza e throughput]]

## 📕 5 — Blocchi digitali
1. [[Half adder e full adder]]
2. [[Ripple carry adder]]
3. [[Carry lookahead adder]]
4. [[Sottrattori comparatori e ALU]]
5. [[Shifter e rotatori]]
6. [[Notazione a virgola fissa]]
7. [[Virgola mobile IEEE 754]]
8. [[Contatori e shift register]]
9. [[Array di memoria - organizzazione]]
10. [[DRAM SRAM e ROM]]
11. [[Register file ROM e logic array]]

## 📓 6 — Architettura ARM
1. [[Linguaggio assembly - principi di progetto]]
2. [[Registri ARM]]
3. [[Operandi - registri immediati e memoria]]
4. [[Istruzioni LDR e STR]]
5. [[Istruzioni logiche e di shift]]
6. [[Flag di condizione e istruzione CMP]]
7. [[Branch ed esecuzione condizionale]]
8. [[Costrutti condizionali in assembly]]
9. [[Cicli in assembly]]
10. [[Array e modalita di indirizzamento]]
11. [[Byte caratteri ASCII e stringhe]]
12. [[Funzioni e convenzioni di chiamata]]
13. [[Lo stack]]
14. [[Linguaggio macchina - formati istruzione]]

## 📔 7 — Microarchitettura
1. [[Microarchitettura - datapath e unita di controllo]]
2. [[Analisi delle prestazioni e CPI]]
3. [[Processore single-cycle - datapath]]
4. [[Processore single-cycle - unita di controllo]]
5. [[Processore single-cycle - prestazioni]]
6. [[Processore multiciclo - datapath]]
7. [[Processore multiciclo - controllo a FSM]]
8. [[Processore multiciclo - prestazioni]]

## 📒 8 — Sistemi di memoria
1. [[Gerarchia di memoria e principi di localita]]
2. [[Metriche di prestazione - miss rate e AMAT]]
3. [[Cache - organizzazione e parametri]]
4. [[Cache direct mapped]]
5. [[Cache set associative e fully associative]]
6. [[Blocchi politiche di sostituzione e scrittura]]
7. [[Memoria virtuale - concetti]]
8. [[Page table e TLB]]

---

## 🔗 I fili conduttori del libro
Sono i temi che ritornano in ogni capitolo. Vale la pena seguirli trasversalmente:

**Astrazione, gerarchia, modularità, regolarità**
[[Astrazione e gestione della complessita]] → [[Latch SR]] (il simbolo come astrazione) →
[[Multiplexer]] (mux grandi da mux 2:1) → [[Linguaggio assembly - principi di progetto]] →
[[Microarchitettura - datapath e unita di controllo]]

**Il compromesso velocità / area / potenza**
[[Da equazioni a schemi - logica a due livelli]] → [[Carry lookahead adder]] →
[[Codifica degli stati - binaria e one-hot]] →
[[Processore single-cycle - prestazioni]] → [[Processore multiciclo - prestazioni]] →
[[Cache set associative e fully associative]]

**Il timing come vincolo dominante**
[[Timing combinatorio - ritardo di propagazione e cammino critico]] →
[[Timing sequenziale - setup hold e clock skew]] →
[[Parallelismo latenza e throughput]] → [[Analisi delle prestazioni e CPI]]

**Il complemento a due, scelta che si propaga in tutto il libro**
[[Numeri con segno - segno-modulo e complemento a due]] →
[[Sottrattori comparatori e ALU]] → [[Shifter e rotatori]] (ASR) →
[[Flag di condizione e istruzione CMP]] (flag V, condizioni con/senza segno)

**La località, principio che regge tutta la gerarchia**
[[Gerarchia di memoria e principi di localita]] → [[Cache direct mapped]] →
[[Blocchi politiche di sostituzione e scrittura]] (LRU) → [[Memoria virtuale - concetti]] →
[[Page table e TLB]]
