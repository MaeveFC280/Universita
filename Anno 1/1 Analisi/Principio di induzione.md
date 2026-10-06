---
Materia:
  - Analisi
tags:
  - Logica
Link risorse:
Libro:
Imparato: false
Ordine: 7
aliases:
---
Sia $P_{n}$ una affermazione contenente un parametro $n\in\mathbb N$ e che a seconda dei suoi valori può essere vera o falsa.
Supponiamo che:
1. **Passo base:** $P_{0}$ è vera
2. **Passo induttivo:** Suppongo che $P_{n}$ sia vera per un $n\in\mathbb N$ e dimostro che $P_{n+1}$ è vera
Fatti questi due passi viene **dimostrato** che $P_{n}$ è vera $\forall n\in\mathbb N$


>[!example] Somma di Gauss
>$P_{n}:\frac{n(n+1)}2\ \forall n \underline{>}0$
>1. $n=0\ \ \ 0=0$: Vera
>2. HP: $0+1+2\dots+n=\frac{n(n+1)}2$ TH: $0+1+2\dots+n+n+1=\frac{(n+1)(n+2)}2=\frac{n(n+1)}2+n+1$ Somma di tutto in colonna scopro tutti n per tante volte quando 2S. $S=\frac{n(n+1)}2$


>[!example] Esempio
>$P_{n}:2^n \underline{>}n+1$
>1. $n=0\ \ \ 1 \underline{>}1$
>2. HP: $2^n \underline{>}n+1$ TH: $2^{n+1} \underline{>}n+2$   $2^{n+1}=2^n\cdot 2$
>Moltiplico la tesi per drfinire $2^2\cdot 2 \underline{>}2(n+1)\to 2^{n+1} \underline{>}2n+2 \underline{>}n+2$

