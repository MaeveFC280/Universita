---
tags: [architettura, sequenziale, latch, cap3]
capitolo: 3
sezione: "3.2.2"
pagine_pdf: 127-129
---

# Latch SR

## Struttura
Uno dei circuiti sequenziali più semplici. È composto da **due porte NOR incrociate**.
Ha due ingressi, $S$ e $R$, e due uscite, $Q$ e $\overline{Q}$.

È simile agli inverter incrociati, ma con la differenza cruciale che il suo stato
**può essere controllato** tramite $S$ e $R$.

## Significato degli ingressi
- $S$ = **Set**: "settare" un bit significa portarlo a TRUE (1).
- $R$ = **Reset**: "resettare" un bit significa portarlo a FALSE (0).

## Tabella di verità
| $S$ | $R$ | $Q$ | $\overline{Q}$ | Comportamento |
|---|---|---|---|---|
| 0 | 0 | $Q_{prev}$ | $\overline{Q_{prev}}$ | **memoria**: mantiene lo stato precedente |
| 0 | 1 | 0 | 1 | **reset** |
| 1 | 0 | 1 | 0 | **set** |
| 1 | 1 | 0 | 0 | **stato non valido** |

### I quattro casi
- **$R$ asserito** → $Q$ è resettato a 0, $\overline{Q}$ fa l'opposto.
- **$S$ asserito** → $Q$ è settato a 1, $\overline{Q}$ fa l'opposto.
- **Nessuno dei due asserito** → il latch **mantiene** il valore precedente, che
  chiamiamo $Q_{prev}$. È qui che risiede la memoria: $Q_{prev}$ è lo stato del latch.
- **Entrambi asseriti** → $Q$ e $\overline{Q}$ valgono **entrambi 0**: contraddittorio,
  perché dovrebbero essere complementari. Da evitare.

> [!tip] Cosa basta sapere per prevedere il futuro
> Per predire il comportamento futuro del latch SR è sufficiente sapere se è stato
> **più recentemente settato o resettato**. Tutta la storia precedente è irrilevante:
> questo è il senso concreto della parola "stato".

## Simbolo e astrazione
Il latch SR si rappresenta con un simbolo a scatola: è un'applicazione di
**astrazione e modularità**. Qualunque circuito che rispetti quella tabella di verità
**è** un latch SR, indipendentemente da come è costruito internamente.

Il latch SR è un elemento bistabile con **un bit di stato**, memorizzato in $Q$.

## I problemi del latch SR
1. Il comportamento con $S = R = 1$ è **anomalo** e va escluso a livello di sistema.
2. Gli ingressi $S$ e $R$ **confondono due questioni distinte**: *quale* valore
   memorizzare e *quando* memorizzarlo. Il latch D risolve questa confusione
   (→ [[Latch D]]).

## Da ricordare
- 2 NOR incrociati; $S$=set, $R$=reset.
- $S=R=0$ → memoria; $S=R=1$ → stato illegale.
- Difetto concettuale: mescola "cosa" e "quando".

## Domande flash
1. Cos'è $Q_{prev}$ e perché è il "vero" stato del latch?
2. Perché $S=R=1$ è inaccettabile?
