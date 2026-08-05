---
tags: [architettura, fondamenti, elettronica, cap1]
capitolo: 1
sezione: "1.6"
pagine_pdf: 39-43
---

# Sotto l'astrazione digitale: livelli logici e margini di rumore

L'astrazione digitale funziona solo se il circuito reale rispetta certe convenzioni
elettriche. Qui si guarda "sotto" l'astrazione.

## Il problema
Le tensioni sono continue. Occorre decidere quali tensioni contano come `0` e quali
come `1`, tenendo conto che il **rumore** (accoppiamenti, alimentazione instabile,
radiazione elettromagnetica) altera i segnali durante il transito.

## Livelli logici
Si definiscono soglie distinte per chi **riceve** e per chi **trasmette**:

| Simbolo | Significato |
|---|---|
| $V_{DD}$ | tensione di alimentazione |
| $V_{IL}$ | massima tensione che il **ricevitore** interpreta come 0 |
| $V_{IH}$ | minima tensione che il **ricevitore** interpreta come 1 |
| $V_{OL}$ | massima tensione che il **trasmettitore** produce per uno 0 |
| $V_{OH}$ | minima tensione che il **trasmettitore** produce per un 1 |

La banda tra $V_{IL}$ e $V_{IH}$ è la **zona proibita** (*forbidden zone*): un ingresso
che cade lì ha comportamento non definito.

## Margini di rumore
$$NM_H = V_{OH} - V_{IH} \qquad NM_L = V_{IL} - V_{OL}$$

Sono il "cuscinetto" di tensione che il rumore può consumare senza che il segnale
venga interpretato male. Devono essere **positivi** perché il sistema sia affidabile.

> [!info] Regola di progetto
> Il trasmettitore deve essere più "generoso" di quanto il ricevitore pretenda:
> $V_{OH} > V_{IH}$ e $V_{OL} < V_{IL}$.

## Caratteristica di trasferimento DC
È il grafico di $V(Y)$ in funzione di $V(A)$. Un **buffer ideale** ha transizione
verticale sul punto medio $V_{DD}/2$; un buffer reale ha una pendenza finita.
Convenzionalmente si scelgono $V_{IL}$ e $V_{IH}$ nei punti in cui la pendenza vale $-1$,
perché è lì che il guadagno del circuito cessa di attenuare il rumore.

## Alimentazioni e famiglie logiche
Storicamente $V_{DD} = 5\ V$; la tensione è poi scesa (3.3 V, 2.5 V, 1.8 V, 1.2 V…) per
ridurre il consumo e per compatibilità con transistor più piccoli. Componenti di
famiglie diverse (TTL, CMOS, LVTTL…) hanno soglie diverse e non sempre sono
interoperabili: bisogna verificare i margini di rumore sui data sheet.

## Da ricordare
- 5 grandezze: $V_{DD}$, $V_{IL}$, $V_{IH}$, $V_{OL}$, $V_{OH}$.
- $NM_H = V_{OH}-V_{IH}$, $NM_L = V_{IL}-V_{OL}$; entrambi > 0.
- Zona proibita = comportamento indefinito.

## Domande flash
1. Con $V_{OH}=2{,}4$ V e $V_{IH}=2{,}0$ V, quanto vale $NM_H$?
2. Cosa succede se un ingresso resta nella zona proibita?

Collegato a: [[X e Z - don t care contention e nodi flottanti]]
