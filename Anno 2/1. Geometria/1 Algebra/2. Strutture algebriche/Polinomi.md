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
Un **termine** in $n$ variabili $x_1,\dots,x_n$ è un prodotto di potenze delle variabili:

$$
\tau=x_1^{\alpha_1}x_2^{\alpha_2}\cdots x_n^{\alpha_n},
\qquad \alpha_1,\dots,\alpha_n\in\mathbb N.
$$

Un **monomio** è un termine moltiplicato per un elemento di $K$:

$$
\gamma x_1^{\alpha_1}\gamma x_2^{\alpha_2}\cdots \gamma x_n^{\alpha_n},
\qquad \gamma\in K.
$$

Un **polinomio su $K$ in $n$ variabili** è una somma finita di monomi:

$$
p=\sum_{i=1}^{d}\gamma_{i}\tau_i,
$$
---
## Grado
- Il grado di un **termine** è la somma degli esponenti che in esso compaiono
- Il grado di un **monomio** è il grado del termine da cui è composto
- Il grado di un **polinomio** è il massimo dei gradi dei termini che in esso compaiono con coefficiente non nullo
>[!example]- Esempio
>Considerando $K=\mathbb{R}$ e $p=-3x_{1}^2x_{5}^4x_{4}^1+\pi x_{2}^1x_{3}^1-\sqrt{ 5 }x_{2}^1x_{4}^1$
>- Grado 7: $-3x_{1}^2x_{5}^4x_{4}^1$
>- Grado 2: $\pi x_{2}^1x_{3}^1$
>- Grado 6: $\sqrt{ 5 }x_{2}^1x_{4}^1$
>Il grado del polinomio è $fr(p)=7$


---
## Polinomi ad un'incognita
Sia $K$ un campo, l'insieme dei polinomi in una sola incognita $t$ con coefficienti in $K$ si indica con
$$
K[t].
$$

Un polinomio ha la forma
$$
p(t)=a_0+a_1t+a_2t^2+\dots+a_nt^n,
\qquad a_i\in K.
$$

Quindi $K[t]$ è l'insieme di tutti i polinomi in $t$ con coefficienti appartenenti a $K$.

$$
K[t]=\left\{   \sum^d_{i=1}\gamma_{i}t^i\ |\ d\in \mathbb{N}\{0\} , \gamma_{i}\in K,\forall i\in\{ 1,\dots,d \}   \right\}
$$
>[!example]- Esempio
$$>K=\mathbb{R}\qquad a\cdot t\qquad 7-t^2+t^8+0\cdot t^{10} \text{  grado 8}$$




---
## Operazioni con i Polinomi
Avendo 
- $p_{1}(t)=a_{0}+a_{1}t+\dots a_{n}t_{n}^k$
- $p_{2}(t)=b_{0}+b_{1}t+\dots b_{n}t^k$

La somma è
$$
+:K[t]\times K[t]\to K[t] \qquad (p_{1}(t),p_{2}(t))\rightsquigarrow p_{1}(t)+p_{2}(t)=a_{0}+b_{0}+(a_{1}+b_{1})t+\dots
$$

>[!example]- Esempio
$$(5t-\sqrt{ 2 }t^3+11t^{14})+(-2+6t+t^2-7t^5)=$$
$$-2+11t+t^2-\sqrt{ 2 }t^3-7t^5+11t^14$$

- $(K[t],+)$ è un gruppo abeliano.
- $(K[t],+,\cdot)$ è un anello commutativo unitario.

---
## Equazioni lineari

Sia $K$ un campo, un'equazione lineare in $n$ incognite $x_1,\dots,x_n$ è un'equazione del tipo

$$
a_1x_1+a_2x_2+\dots+a_nx_n=b,
\qquad a_1,\dots,a_n,b\in K.
$$

Una **soluzione** è una n-upla di scalari che sostituiti ordinatamente alle variabili rende l'equazione un'uguaglianza.
$$
(x_1,\dots,x_n)\in K^n
$$

>[!example]- Esempio
$$3x_{1}-x_{2}+2x_{4}-2=0$$
$$\text{Soluzioni: }(1,3,1)$$

---
## Sistema di equazioni
Un sistema lineare di $m$ equazioni su $K$ in $n$ incognite è una [[n-upla|n-upla]] di equazioni lineari su $K$.
$$
\sum:
\begin{cases}
a_{11}x_1+a_{12}x_2+\dots+a_{1n}x_n=0\\
a_{21}x_1+a_{22}x_2+\dots+a_{2n}x_n=0\\
\vdots\\
a_{m1}x_1+a_{m2}x_2+\dots+a_{mn}x_n=0
\end{cases}
$$
Una soluzione di $\Sigma$ è una n-upla che risulta essere soluzione di tutte le equazioni di $\Sigma$, ovvero se le soluzioni avendo$S_{1},\dots S_{n}$ allora $S=S_{1}\cap\dots\cap S_{n}$ (intersezione delle soluzioni del sistema).