---
Materia:
  - Geometria
tags:
Link risorse:
Libro:
Imparato: false
Ordine: 10
aliases:
---
Un sottoinsieme $W\subseteq V$ si dice **sottospazio vettoriale** di $V$ se, con le stesse operazioni $\boxplus$ e $\boxdot$ definite su $V$, è a sua volta uno spazio vettoriale su $K$.

>[!tip] Criterio di sottospazio
>Un sottoinsieme $W\subseteq V$ è un sottospazio vettoriale di $V$ se:
>
>$$
>W\neq\varnothing
>$$
>
>e $W$ è linearmente chiuso, cioè:
>
>$$
>\forall u,v\in W,\ \forall\alpha,\beta\in K,
>\qquad
>(\alpha\boxdot u)\boxplus(\beta\boxdot v)\in W.
>$$

>[!example]- Esempio
>Consideriamo lo spazio vettoriale
>$$
>\mathbb R^2
>$$
>e il sottoinsieme
>$$
>W=\{(x,0)\mid x\in\mathbb R\}.
>$$
>
>Prendiamo
>$$
>u=(x,0),\qquad v=(y,0)\in W
>$$
>e $\alpha,\beta\in\mathbb R$.
>
>Allora:
>$$
>\alpha u+\beta v
>=
>\alpha(x,0)+\beta(y,0)
>$$
>
>$$
>=
>(\alpha x,0)+(\beta y,0)
>$$
>
>$$
>=
>(\alpha x+\beta y,0).
>$$
>
>Poiché $\alpha x+\beta y\in\mathbb R$, si ha
>$$
>(\alpha x+\beta y,0)\in W.
>$$
>
>Quindi $W$ è linearmente chiuso e pertanto è un sottospazio vettoriale di $\mathbb R^2$.

$W$ si dice **linearmente chiuso** se è chiuso rispetto alla somma tra vettori e alla moltiplicazione per scalare.

Quindi devono valere:

$$
\forall u,v\in W,\qquad u\boxplus v\in W
$$

e

$$
\forall \alpha\in K,\ \forall u\in W,\qquad
\alpha\boxdot u\in W.
$$

In altre parole, applicando le operazioni dello spazio vettoriale ad elementi di $W$, il risultato deve appartenere ancora a $W$.

Le due condizioni possono essere scritte insieme tramite una **combinazione lineare**:

$$
\forall u,v\in W,\ \forall\alpha,\beta\in K,
\qquad
(\alpha\boxdot u)\boxplus(\beta\boxdot v)\in W.
$$


