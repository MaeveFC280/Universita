---
Materia:
  - Geometria
tags:
Link risorse:
Libro:
Imparato: false
Ordine: 6
aliases:
---
Siano $A_1,\dots,A_n$ insiemi non vuoti. Il loro prodotto cartesiano è
$$
A_1\times A_2\times\cdots\times A_n
=
\{(a_1,\dots,a_n)\mid a_i\in A_i\}.
$$
Gli elementi $(a_1,\dots,a_n)$ si chiamano **n-uple**.

Se $K$ è un campo, allora
$$
K^n=K\times\cdots\times K
$$
è l'insieme di tutte le n-uple di elementi di $K$.
Le n-uple di $K^n$ vengono anche chiamate **vettori numerici**.


---
## Operazioni con le n-uple

### Somma
La somma è definita componente per componente:

$$
+:K^n\times K^n\to K^n
$$

$$
(a_1,\dots,a_n)+(b_1,\dots,b_n)
=
(a_1+b_1,\dots,a_n+b_n).
$$

### Moltiplicazione per uno scalare
Sia $\alpha\in K$.

$$
\cdot:K\times K^n\to K^n
$$

$$
\alpha(a_1,\dots,a_n)
=
(\alpha a_1,\dots,\alpha a_n).
$$

> [!example]- Esempio
> In $\mathbb R^3$:
> $$
> (2,5,1)+(3,-1,7)=(5,4,8)
> $$
> e
> $$
> 2(2,5,1)=(4,10,2).
> $$

Inoltre
$$
(K^n,+)
$$

è un **[[Strutture algebriche|gruppo abeliano]]**.
