---
tags:
  - formulario
  - ripasso
---

# 🧮 Formulario e sigle

Foglio di riepilogo trasversale. Ogni voce rimanda alla nota che la spiega.

## Numerazione e informazione
| Formula | Significato | Nota |
|---|---|---|
| $D = \log_2 N$ | bit di informazione di una variabile a $N$ stati | [[Astrazione digitale e quantita di informazione]] |
| $[0,\ 2^N-1]$ | range di $N$ bit **senza segno** | [[Sistemi di numerazione binario e esadecimale]] |
| $[-2^{N-1}+1,\ 2^{N-1}-1]$ | range **segno/modulo** | [[Numeri con segno - segno-modulo e complemento a due]] |
| $[-2^{N-1},\ 2^{N-1}-1]$ | range **complemento a due** | idem |
| inverti + 1 | negazione in complemento a due | idem |
| $2^{10}=1024$ | base dei prefissi K, M, G | [[Byte nibble word e prefissi binari]] |

## Livelli logici
| Formula | Significato |
|---|---|
| $NM_H = V_{OH} - V_{IH}$ | margine di rumore alto |
| $NM_L = V_{IL} - V_{OL}$ | margine di rumore basso |

→ [[Livelli logici e margini di rumore]]

## Logica combinatoria
| Formula | Nome |
|---|---|
| $\overline{AB} = \overline{A}+\overline{B}$ ; $\overline{A+B}=\overline{A}\,\overline{B}$ | **De Morgan** (T12) |
| $BC + B\overline{C} = B$ | **combinazione** (T10) — motore della minimizzazione |
| $B + BC = B$ | **copertura** (T9) |
| $BC + \overline{B}D + CD = BC + \overline{B}D$ | **consenso** (T11) |
| $2^k$ caselle cerchiate ⇒ $k$ letterali in meno | K-map |
| mux N:1 ⇒ $\log_2 N$ selettori | multiplexer |
| decoder: $N$ ingressi ⇒ $2^N$ uscite one-hot | decoder |

→ [[Assiomi e teoremi dell algebra di Boole]] · [[Mappe di Karnaugh]]

## Timing
| Formula | Significato |
|---|---|
| $t_{pd} = \sum$ cammino **critico** | ritardo di propagazione (max) |
| $t_{cd} = \sum$ cammino **breve** | ritardo di contaminazione (min) |
| $T_c \ge t_{pcq} + t_{pd} + t_{setup} (+t_{skew})$ | **vincolo di setup** — dipende dal clock |
| $t_{cd} \ge t_{hold} + t_{skew} - t_{ccq}$ | **vincolo di hold** — **NON** dipende dal clock |
| $t_{pcq} + t_{setup}$ | overhead di sequenziamento |
| apertura $= t_{setup} + t_{hold}$ | finestra di stabilità richiesta |

→ [[Timing sequenziale - setup hold e clock skew]]

## Aritmetica
| Formula | Significato |
|---|---|
| $S = A \oplus B \oplus C_{in}$ | somma del full adder (parità) |
| $C_{out} = AB + AC_{in} + BC_{in}$ | riporto del full adder (maggioranza) |
| $t_{ripple} = N\,t_{FA}$ | ritardo del ripple-carry adder |
| $G_i = A_iB_i$ ; $P_i = A_i + B_i$ | generate / propagate |
| $C_i = G_i + P_i C_{i-1}$ | equazione del riporto (CLA) |
| $A - B = A + \overline{B} + 1$ | sottrazione |
| $V = (-1)^S \times 1.F \times 2^{E-127}$ | IEEE 754 singola precisione (bias **127**) |
| bias 1023, campi 1/11/52 | IEEE 754 doppia precisione |

→ [[Carry lookahead adder]] · [[Virgola mobile IEEE 754]]

## Prestazioni
| Formula | Significato |
|---|---|
| $T_{exec} = N_{istr} \times CPI \times T_c$ | **equazione delle prestazioni** |
| $CPI = \sum_i f_i CPI_i$ | CPI medio pesato |
| throughput $= P/L$ | con parallelismo di grado $P$ |

CPI del multiciclo: **LDR 5, STR 4, data-processing 4, B 3**.

→ [[Analisi delle prestazioni e CPI]] · [[Processore multiciclo - prestazioni]]

## Memoria
| Formula | Significato |
|---|---|
| $MR = 1 - HR$ | miss rate / hit rate |
| $AMAT = t_{cache} + MR_{cache}(t_{MM} + MR_{MM}t_{VM})$ | tempo medio di accesso |
| $B = C/b$ | numero di blocchi |
| $N = B/S$ | grado di associatività |
| tag \| set \| block offset \| byte offset | scomposizione dell'indirizzo |
| VPN \| page offset → PPN \| page offset | traduzione virtuale→fisica |

→ [[Metriche di prestazione - miss rate e AMAT]] · [[Cache direct mapped]] ·
[[Memoria virtuale - concetti]]

## ARM: registri
| Registro | Nome | Uso |
|---|---|---|
| R0–R3 | — | argomenti e valore di ritorno (**R0**) |
| R4–R11 | — | variabili locali, **callee-saved** |
| R12 | IP | scratch |
| R13 | **SP** | stack pointer (cresce **verso il basso**) |
| R14 | **LR** | indirizzo di ritorno |
| R15 | **PC** | leggerlo restituisce **PC + 8** |

## ARM: formati istruzione
| `op` (bit 27:26) | Formato | `funct` |
|---|---|---|
| **00** | data-processing | `I`, `cmd`(4), `S` |
| **01** | memoria | `I,P,U,B,W,L` (**L=1 → LDR**) |
| **10** | branch | `1L` (**L=1 → BL**) |

`cond` sta nei bit **31:28** di **tutte** le istruzioni.
$BTA = (PC+8) + 4 \times imm24$.

→ [[Linguaggio macchina - formati istruzione]]

## ARM: flag e condizioni
**N** negativo · **Z** zero · **C** carry · **V** overflow

| con segno | senza segno |
|---|---|
| `GE`, `LT`, `GT`, `LE` | `HS/CS`, `LO/CC`, `HI`, `LS` |

→ [[Flag di condizione e istruzione CMP]]

## ASCII utili
| Carattere | Hex |
|---|---|
| `'0'` | 0x30 |
| `'A'` | 0x41 |
| `'a'` | 0x61 |
| differenza maiuscola/minuscola | **0x20** |
| NUL (fine stringa C) | 0x00 |

→ [[Byte caratteri ASCII e stringhe]]

## Sigle
| Sigla | Sciolta |
|---|---|
| **SOP / POS** | sum-of-products / product-of-sums |
| **FSM** | finite state machine |
| **CPA / CLA** | carry propagate adder / carry-lookahead adder |
| **ALU** | arithmetic/logical unit |
| **LUT** | lookup table |
| **PLA / FPGA** | programmable logic array / field programmable gate array |
| **CPI / IPC** | cycles per instruction / instructions per cycle |
| **AMAT** | average memory access time |
| **LRU** | least recently used |
| **VPN / PPN** | virtual / physical page number |
| **PTE** | page table entry |
| **TLB** | translation lookaside buffer |
| **lsb / msb** | least / most significant **bit** |
| **LSB / MSB** | least / most significant **byte** |
