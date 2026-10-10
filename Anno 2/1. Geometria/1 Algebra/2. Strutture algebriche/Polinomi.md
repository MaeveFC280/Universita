---
Materia:
  - Geometria
  - Algebra Lineare
tags:
Link risorse:
Libro:
Imparato: true
Ordine: 7
aliases:
---
Sia $(K,+,\cdot)$ un [[Strutture algebriche#^1ed1df|campo]] e siano $x_1,\dots,x_n$ delle variabili. Indichiamo con $\mathbb N_0=\{0,1,2,\dots\}$ l'insieme degli interi non negativi.

## Termini, monomi e polinomi
>[!info] Definizioni
>Un **termine** in $n$ variabili è un prodotto di potenze delle variabili:
>$$
>\tau=x_1^{\alpha_1}x_2^{\alpha_2}\cdots x_n^{\alpha_n},\qquad \alpha_1,\dots,\alpha_n\in\mathbb N_0.
>$$
>Un **monomio** è un termine moltiplicato per un coefficiente $\gamma\in K$:
>$$
>\boxed{\gamma\,x_1^{\alpha_1}x_2^{\alpha_2}\cdots x_n^{\alpha_n}}
>$$
>Un **polinomio** su $K$ nelle variabili $x_1,\dots,x_n$ è una **somma finita di monomi**:
>$$
>\boxed{p(x_1,\dots,x_n)=\sum_{j=1}^{r}\gamma_j\tau_j,\qquad \gamma_j\in K.}
>$$
>Per definizione, $\tau_j$ sono termini nelle variabili considerate; per il polinomio nullo tutti i coefficienti sono zero (si può anche usare la somma vuota).

I monomi che hanno **lo stesso termine** (le stesse variabili con gli stessi esponenti) sono *simili* e si possono raccogliere sommando i coefficienti. Per determinare il grado di un polinomio bisogna considerarlo dopo avere raccolto i monomi simili.

## Grado
- Il **grado di un termine** è la somma dei suoi esponenti:
  $$\deg(\tau)=\alpha_1+\dots+\alpha_n.$$
- Il **grado di un monomio non nullo** è il grado del suo termine.
- Il **grado di un polinomio non nullo** è il massimo dei gradi dei termini che compaiono con coefficiente non nullo, dopo avere raccolto i monomi simili:
  $$\boxed{\deg(p)=\max\{\deg(\tau_j)\mid\gamma_j\ne0\}.}$$

Un polinomio costante non nullo ha grado $0$. Il polinomio nullo non ha un grado definito; in alcune convenzioni si pone $\deg(0)=-\infty$.

>[!example]- Esempio: grado in più variabili
>Consideriamo $K=\mathbb R$ e il polinomio in cinque variabili:
>$$
>p=-3x_1^2x_5^4x_4+\pi x_2x_3-\sqrt5\,x_2x_4.
>$$
>- Il primo monomio ha grado $2+4+1=7$.
>- Il secondo monomio ha grado $1+1=2$.
>- Il terzo monomio ha grado $1+1=2$.
>Quindi:
>$$
>\boxed{\deg(p)=7}
>$$

## Polinomi in una sola variabile
Sia $t$ una sola variabile. L'insieme dei polinomi in $t$ con coefficienti nel campo $K$ si indica con **$K[t]$**:
$$
\boxed{K[t]=\left\{\sum_{i=0}^{d}a_it^i\ \middle|\ d\in\mathbb N_0,\ a_i\in K\right\}.}
$$
Qui $t^0=1$, quindi il coefficiente $a_0$ rappresenta il **termine costante**. Un polinomio può essere scritto nella forma:
$$
p(t)=a_0+a_1t+a_2t^2+\dots+a_dt^d.
$$
Se $a_d\ne0$, il grado è $d$ e $a_d$ è detto **coefficiente direttore**.

>[!example]- Esempio
>In $\mathbb R[t]$ consideriamo:
>$$
>p(t)=7-t^2+t^8+0\cdot t^{10}.
>$$
>Il termine di grado $10$ ha coefficiente nullo, quindi non conta ai fini del grado:
>$$
>\boxed{\deg(p)=8}
>$$

## Operazioni con i polinomi
Siano:
$$
p(t)=\sum_{i=0}^{d}a_it^i,\qquad q(t)=\sum_{j=0}^{e}b_jt^j.
$$

### Addizione
L'addizione è un'operazione interna:
$$
+:K[t]\times K[t]\longrightarrow K[t].
$$
Si sommano i coefficienti dei termini con la **stessa potenza** di $t$. Se una potenza manca in uno dei due polinomi, il suo coefficiente è considerato zero:
$$
p(t)+q(t)=\sum_{k=0}^{\max(d,e)}(a_k+b_k)t^k.
$$

>[!example]- Esempio: somma
>$$
>\begin{aligned}
>&(5t-\sqrt2\,t^3+11t^{14})+(-2+6t+t^2-7t^5)\\
>&=-2+11t+t^2-\sqrt2\,t^3-7t^5+11t^{14}.
>\end{aligned}
>$$

L'opposto di $p(t)$ è il polinomio $-p(t)$ ottenuto cambiando segno a tutti i coefficienti. Lo zero è il polinomio con tutti i coefficienti nulli. Perciò $(K[t],+)$ è un **gruppo abeliano**.

### Moltiplicazione tra polinomi
La moltiplicazione è un'altra operazione interna:
$$
\cdot:K[t]\times K[t]\longrightarrow K[t].
$$
Si applica la proprietà distributiva e si usa $t^it^j=t^{i+j}$. Raccogliendo i termini dello stesso grado otteniamo:
$$
\boxed{p(t)q(t)=\sum_{k=0}^{d+e}\left(\sum_{\substack{i+j=k\\0\le i\le d,\;0\le j\le e}}a_ib_j\right)t^k.}
$$
In pratica, **il coefficiente di $t^k$ è la somma dei prodotti $a_ib_j$ per tutti gli indici con $i+j=k$**.

>[!example]- Esempio: prodotto
>$$
>\begin{aligned}
>(1+2t)(3-t+t^2)
>&=3-t+t^2+6t-2t^2+2t^3\\
>&=\boxed{3+5t-t^2+2t^3}
>\end{aligned}
>$$

### Struttura algebrica e prodotto per scalare
- $(K[t],+,\cdot)$ è un **[[Strutture algebriche|anello commutativo unitario]]**: l'elemento neutro della moltiplicazione è il polinomio costante $1$.
- In generale $K[t]$ **non è un campo**: per esempio il polinomio $t$ non ammette inverso in $K[t]$.
- Possiamo anche moltiplicare un polinomio per uno **scalare** $\lambda\in K$, moltiplicando tutti i coefficienti:
  $$
  \lambda p(t)=\sum_{i=0}^{d}(\lambda a_i)t^i.
  $$
  Con l'addizione e questa moltiplicazione per scalare, $K[t]$ è uno [[Spazi e sottospazi vettoriali|spazio vettoriale]] su $K$.

## Collegamento alle equazioni lineari
Un'equazione lineare in $n$ incognite può essere scritta come:
$$
a_1x_1+\dots+a_nx_n-b=0,\qquad a_1,\dots,a_n,b\in K.
$$
È un'equazione polinomiale il cui polinomio ha **grado al più $1$** (quando non è nullo). Il suo studio, insieme ai sistemi di equazioni, prosegue in [[Sistema di equazioni lineari]].

>[!example]- Esempio: una soluzione
>Consideriamo:
>$$
>3x_1-x_2+2x_4-2=0.
>$$
>È un'equazione in **quattro incognite**, anche se $x_3$ non compare (ha coefficiente zero). La $4$-upla $(1,3,0,1)$ è una soluzione, perché:
>$$
>3\cdot1-3+2\cdot1-2=0.
>$$
