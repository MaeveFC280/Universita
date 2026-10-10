---
Materia:
  - Analisi
Imparato:
tags:
---
## Successione numerica

>[!info] Definizione
>Una **successione numerica reale** è una funzione che associa a ogni numero naturale $n$ un numero reale $a_n$:
>$$
>a:\mathbb N\longrightarrow\mathbb R,\qquad n\longmapsto a_n.
>$$
>Si indica con $(a_n)_{n\in\mathbb N}$ oppure, più semplicemente, con $(a_n)$.

Il numero $n$ è l'**indice**; $a_n$ è il **termine di indice $n$**. L'insieme dei valori assunti è $\{a_n\mid n\in\mathbb N\}$.

Una successione può anche essere definita soltanto per gli indici $n\ge n_0$ (per esempio $1/n$ richiede $n\ge1$). Nel limite per $n\to+\infty$ il valore dei primi termini non influisce sul risultato.

>[!example] Esempi
>- $a_n=2n$: $0,2,4,6,\ldots$ (se partiamo da $n=0$).
>- $b_n=\frac1n$: $1,\frac12,\frac13,\ldots$ (se partiamo da $n=1$).
>- $c_n=(-1)^n$: $1,-1,1,-1,\ldots$ (se partiamo da $n=0$).
>- $d_n=\frac{n}{n+1}$: $0,\frac12,\frac23,\frac34,\ldots$ (se partiamo da $n=0$).

## Proprietà vere definitivamente e frequentemente

Queste espressioni riguardano una proprietà $P_n$ che, al variare dell'indice $n$, può essere vera oppure falsa.

>[!info] Vera definitivamente
>$P_n$ è **vera definitivamente** quando esiste un indice $n_0\in\mathbb N$ tale che la proprietà vale per **tutti** gli indici successivi:
>$$
>\boxed{\exists n_0\in\mathbb N\ \forall n\ge n_0:\ P_n\ \text{è vera}.}
>$$
>In altre parole, possono esserci eccezioni fra i primi termini, ma non oltre un certo indice.

>[!info] Vera frequentemente
>$P_n$ è **vera frequentemente** quando vale per **infiniti** indici, cioè comunque lontano si scelga di iniziare a guardare, si trova un indice successivo che la soddisfa:
>$$
>\boxed{\forall n_0\in\mathbb N\ \exists n\ge n_0:\ P_n\ \text{è vera}.}
>$$

>[!example] Esempi
>- La proprietà $n\ge5$ è vera **definitivamente**: basta prendere $n_0=5$.
>- La proprietà $(-1)^n=1$ è vera **frequentemente**, perché vale per tutti gli indici pari, ma **non definitivamente**, perché non vale per quelli dispari.
>- Una proprietà vera definitivamente è anche vera frequentemente; il contrario non è necessariamente vero.

## Significato di limite di una successione

Studiare il limite significa chiedersi come si comportano i termini $a_n$ quando l'indice $n$ cresce senza limite, **non** quale sia il valore di un ultimo termine (che non esiste).

Una successione può:
- avvicinarsi a un numero reale $\ell$ (**limite finito**);
- crescere oltre ogni numero reale (**limite $+\infty$**);
- diminuire al di sotto di ogni numero reale (**limite $-\infty$**);
- non avere nessuno di questi comportamenti (per esempio perché oscilla).

## Limite finito

>[!info] Definizione
>Una successione $(a_n)$ **converge** a $\ell\in\mathbb R$ se, per ogni precisione $\varepsilon>0$, esiste un indice $n_0$ tale che, per tutti gli $n\ge n_0$, $a_n$ dista da $\ell$ meno di $\varepsilon$:
>$$
>\boxed{\forall\varepsilon>0\ \exists n_0\in\mathbb N\ \forall n\ge n_0:\ |a_n-\ell|<\varepsilon.}
>$$
>In questo caso si scrive:
>$$
>\boxed{\lim_{n\to+\infty}a_n=\ell.}
>$$

Per ricordare il significato del **valore assoluto** (richiamato nel registro della lezione), usiamo:
$$
|x|=\begin{cases}x&\text{se }x\ge0,\\-x&\text{se }x<0.\end{cases}
$$
Il valore assoluto $|a_n-\ell|$ rappresenta la **distanza** tra $a_n$ e $\ell$. La condizione equivale a:
$$
\ell-\varepsilon<a_n<\ell+\varepsilon\qquad\forall n\ge n_0.
$$

Quindi, fissato un intervallo anche piccolissimo intorno a $\ell$, **tutti i termini sufficientemente avanti** devono appartenervi. L'indice $n_0$ può dipendere da $\varepsilon$.

>[!example]- Esempio: $\displaystyle\lim_{n\to+\infty}\frac1n=0$
>I termini $1,\frac12,\frac13,\ldots$ sono positivi e diventano sempre più piccoli.
>Per usare la definizione vogliamo verificare:
>$$
>\left|\frac1n-0\right|=\frac1n<\varepsilon.
>$$
>Questa disuguaglianza vale quando:
>$$
>n>\frac1\varepsilon.
>$$
>Scegliendo un intero $n_0>\frac1\varepsilon$, per ogni $n\ge n_0$ la disuguaglianza è verificata.

>[!tip] Dimostrazione
>Dimostriamo formalmente che $\lim_{n\to+\infty}\frac1n=0$.
>Dato un qualsiasi $\varepsilon>0$, scegliamo $n_0\in\mathbb N$ tale che $n_0>\frac1\varepsilon$ (e $n_0\ge1$).
>Per ogni $n\ge n_0$ abbiamo:
>$$
>0<\left|\frac1n-0\right|=\frac1n\le\frac1{n_0}<\varepsilon.
>$$
>È dunque soddisfatta la definizione di limite finito:
>$$
>\boxed{\lim_{n\to+\infty}\frac1n=0.}
>$$

>[!example]- Un limite diverso da zero
>Consideriamo $a_n=2+\frac3n$ ($n\ge1$). Sottraendo il limite candidato $2$:
>$$
>|a_n-2|=\frac3n.
>$$
>Dato $\varepsilon>0$, basta scegliere $n_0>\frac3\varepsilon$.
>Per ogni $n\ge n_0$ risulta $|a_n-2|<\varepsilon$, quindi:
>$$
>\boxed{\lim_{n\to+\infty}\left(2+\frac3n\right)=2.}
>$$

## Limite uguale a $+\infty$

>[!info] Definizione
>Si dice che $(a_n)$ **tende a $+\infty$** se, fissato un qualsiasi numero reale $M$, tutti i termini successivi a un certo indice sono maggiori di $M$:
>$$
>\boxed{\forall M\in\mathbb R\ \exists n_0\in\mathbb N\ \forall n\ge n_0:\ a_n>M.}
>$$
>Si scrive:
>$$
>\boxed{\lim_{n\to+\infty}a_n=+\infty.}
>$$

>[!example] Esempio
>Per $a_n=n$ e per ogni $M\in\mathbb R$ possiamo scegliere $n_0>M$. Allora $n\ge n_0$ implica $n>M$.
>$$
>\boxed{\lim_{n\to+\infty}n=+\infty.}
>$$

## Limite uguale a $-\infty$

>[!info] Definizione
>Si dice che $(a_n)$ **tende a $-\infty$** se, fissato un qualsiasi numero reale $M$, tutti i termini successivi a un certo indice sono minori di $M$:
>$$
>\boxed{\forall M\in\mathbb R\ \exists n_0\in\mathbb N\ \forall n\ge n_0:\ a_n<M.}
>$$
>Si scrive:
>$$
>\boxed{\lim_{n\to+\infty}a_n=-\infty.}
>$$

>[!example] Esempio
>Se $a_n=-n$, scegliendo $n_0>-M$ abbiamo $-n\le-n_0<M$ per tutti gli $n\ge n_0$.
>$$
>\boxed{\lim_{n\to+\infty}(-n)=-\infty.}
>$$

## Successioni senza limite

Non tutte le successioni convergono o tendono a un infinito.

>[!example] Successione oscillante
>Consideriamo:
>$$
>a_n=(-1)^n.
>$$
>I termini continuano ad alternarsi tra $1$ e $-1$. Non si avvicinano definitivamente a un unico numero e non diventano arbitrariamente grandi o piccoli.
>Quindi la successione **non ha limite**, né finito né infinito.

>[!warning] Terminologia
>Una successione **convergente** ha limite finito. Una successione che tende a $+\infty$ o $-\infty$ non converge a un numero reale; talvolta si dice che diverge rispettivamente a $+\infty$ o $-\infty$.
>Una successione oscillante come $(-1)^n$ non ha alcun limite, neppure infinito: è importante distinguere i casi.

## Come affrontare i primi esercizi

1. Scrivi esplicitamente i primi termini per capire l'andamento, ma ricorda che **pochi termini non costituiscono una dimostrazione**.
2. Chiediti se i termini si avvicinano a un numero, crescono senza limite, diminuiscono senza limite oppure oscillano.
3. Se il limite candidato è finito $\ell$, calcola $|a_n-\ell|$ e cerca un indice oltre il quale è minore di ogni $\varepsilon>0$.
4. Se il limite candidato è $+\infty$ o $-\infty$, verifica la condizione con un qualunque $M$.

>[!example]- Riepilogo
>$$
>\begin{aligned}
>\lim_{n\to+\infty}\frac{n}{n+1}&=1,\\
>\lim_{n\to+\infty}n&=+\infty,\\
>\lim_{n\to+\infty}(-n)&=-\infty.
>\end{aligned}
>$$
>La successione $(-1)^n$ invece non ha limite. Nel primo caso $\left|\frac{n}{n+1}-1\right|=\frac1{n+1}\to0$.

>[!info] Collegamenti
>Il registro indica anche **valore assoluto e proprietà**: qui lo richiamiamo soltanto per comprendere la definizione di limite. La sua trattazione completa andrà aggiunta in una nota dedicata. Gli estremi superiori e inferiori sono discussi in [[Minimo, massimo, minorante, maggiorante e limiti]]: sono concetti distinti dal limite di una successione.
