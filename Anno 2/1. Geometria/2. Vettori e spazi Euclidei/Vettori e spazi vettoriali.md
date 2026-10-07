---
Materia:
  - Geometria
  - Algebra Lineare
tags:
Link risorse:
Libro:
Imparato: false
Ordine: 8
aliases:
---
## Vettori liberi
Un **vettore libero** è una [[Relazioni#^classeEquivalenza|classe di equivalenza]] di segmenti orientati aventi:
- stessa direzione;
- stesso verso;
- stessa lunghezza.

L'insieme di tutti i vettori liberi si indica con $V$


![[Vettori-1790939919483.webp]]

---
## Vettori applicati
Fisso con origine nello spazio

---
## Operazioni con i vettori
### Somma di vettori
L'addizione tra vettori è un'[[Operazioni|operazione interna]].

$$  
+\times V\to V  
$$

e può essere definita geometricamente mediante la **regola del parallelogramma**.
![[Operazioni-1790588572979.webp|right]]

La struttura $(V,+)$ è un **[[Strutture algebriche#^0826fd|gruppo abeliano]]**.

Questo significa che per ogni $u,v,w\in V$ valgono:
- Associatività: $(u+v)+w=u+(v+w)$
- Elemento neutro: $0\in V\qquad u+0=0+u=u$
- Elemento opposto: $\forall u\in V\exists-u\in V:u+(-u)=0$
- Commutatività: $u+v=v+u$

Poiché un vettore è una classe di equivalenza di segmenti orientati, **possiamo cambiare rappresentante, traslando il vettore, senza cambiare il vettore stesso**.

Questo permette di scegliere rappresentanti con lo stesso punto di applicazione e applicare la regola del parallelogramma.

### Moltiplicazione per uno scalare
Si definisce un'[[Operazioni|operazione esterna]]:

$$
\cdot:\mathbb R\times V\to V.
$$

Dato $\alpha\in\mathbb R$ e $v\in V$:

- se $\alpha>0$, $\alpha v$ ha stessa direzione e stesso verso di $v$, con lunghezza moltiplicata per $\alpha$;
- se $\alpha<0$, ha stessa direzione ma verso opposto;
- se $\alpha=0$, si ottiene il vettore nullo.

---
## Spazio vettoriale
>[!info] Definizione
Dato un [[Strutture algebriche#^1ed1df|campo]] $(K,+,\cdot)$, uno **spazio vettoriale** su $K$ è una [[Strutture algebriche|struttura]] (quaterna) $(V,K,\boxplus,\boxdot)$ tale che $V$ è un insieme non vuoto e sono definite:
>- $\boxplus:V\times V\to V$ tale che $(V,\boxplus)$ è un gruppo abeliano con $\underline{0}$ vettore nullo
>- $\boxdot:K\times V\to V$ tale che gode delle proprietà:
>	1. $\forall \alpha\in K,\ \forall u,v\in V,\ \alpha\boxdot(u\boxplus v)=(\alpha\boxdot u)\boxplus(\alpha\boxdot v)$: Distributività rispetto alla somma di vettori
>	2. $\forall \alpha \beta\in K,\ \forall u\in V,\ (\alpha+\beta)\boxdot u=(\alpha\boxdot u)\boxplus(\beta\boxdot u)$: Distributività rispetto alla somma degli scalari
>	3. $\forall \alpha \beta\in K,\ \forall u\in V,\ (\alpha \beta)\boxdot u=\alpha\boxdot(\beta\boxdot u)$
>	4. $1\in K, \forall u\in V,\ 1\boxdot u=u$: Elemento neutro


> [!example]- Esempio
> ##### Ipotesi
> Dimostriamo che la quaterna $(K^n,K,\boxplus,\boxdot)$ è uno spazio vettoriale.
> Dimostriamolo per $n=2\implies K^2$, ricordando che $K\neq\varnothing\implies K^2\neq\varnothing$.
> - $K^2\times K^2\to K^2$
>   $(a_1,a_2),(b_1,b_2)\rightsquigarrow(a_1,a_2)\boxplus(b_1,b_2)=(a_1+b_1,a_2+b_2)$
> - $K\times K^2\to K^2$
>   $\alpha,(a_1,a_2)\rightsquigarrow\alpha\boxdot(a_1,a_2)=(\alpha a_1,\alpha a_2)$
> Dimostriamo che:
> 1. $(K^2,\boxplus)$ è un gruppo abeliano, cioè valgono associatività, commutatività, elemento neutro e inversi.
> 2. Valgono le proprietà:
>    1. $\forall\alpha\in K,\ \forall u,v\in K^2,\ \alpha\boxdot(u\boxplus v)=(\alpha\boxdot u)\boxplus(\alpha\boxdot v)$
>    2. $\forall\alpha,\beta\in K,\ \forall u\in K^2,\ (\alpha+\beta)\boxdot u=(\alpha\boxdot u)\boxplus(\beta\boxdot u)$
>    3. $\forall\alpha,\beta\in K,\ \forall u\in K^2,\ (\alpha\beta)\boxdot u=\alpha\boxdot(\beta\boxdot u)$
>    4. $\forall u\in K^2,\ 1\boxdot u=u$
> 
> ##### Dimostrazioni
> ###### 1. $(K^2,\boxplus)$ è un gruppo abeliano
> **Associatività**
> Siano $(a_1,a_2),(b_1,b_2),(c_1,c_2)\in K^2$.
> $$
> \begin{aligned}
> (a_1,a_2)\boxplus\left((b_1,b_2)\boxplus(c_1,c_2)\right)
> &=(a_1,a_2)\boxplus(b_1+c_1,b_2+c_2)\\
> &=(a_1+b_1+c_1,a_2+b_2+c_2)
> \end{aligned}
> $$
> mentre
> $$
> \begin{aligned}
> \left((a_1,a_2)\boxplus(b_1,b_2)\right)\boxplus(c_1,c_2)
> &=(a_1+b_1,a_2+b_2)\boxplus(c_1,c_2)\\
> &=(a_1+b_1+c_1,a_2+b_2+c_2)
> \end{aligned}
> $$
> Quindi:
> $$
> (a_1,a_2)\boxplus\left((b_1,b_2)\boxplus(c_1,c_2)\right)
> =
> \left((a_1,a_2)\boxplus(b_1,b_2)\right)\boxplus(c_1,c_2)
> $$
> **Commutatività**
> Siano $(a_1,a_2),(b_1,b_2)\in K^2$.
> $$
> \begin{aligned}
> (a_1,a_2)\boxplus(b_1,b_2)
> &=(a_1+b_1,a_2+b_2)\\
> &=(b_1+a_1,b_2+a_2)\\
> &=(b_1,b_2)\boxplus(a_1,a_2)
> \end{aligned}
> $$
> poiché la somma in $K$ è commutativa.
> **Elemento neutro**
> Sia $0\in K$ l'elemento neutro di $(K,+)$. Allora l'elemento neutro in $K^2$ è $\underline 0=(0,0)$.
> $$
> \begin{aligned}
> (a_1,a_2)\boxplus(0,0)
> &=(a_1+0,a_2+0)\\
> &=(a_1,a_2)
> \end{aligned}
> $$
> **Inversi**
> Sia $(a_1,a_2)\in K^2$. Gli opposti di $a_1$ e $a_2$ in $(K,+)$ sono $-a_1$ e $-a_2$.
> $$
> \begin{aligned}
> (a_1,a_2)\boxplus(-a_1,-a_2)
> &=(a_1-a_1,a_2-a_2)\\
> &=(0,0)
> \end{aligned}
> $$
> Quindi l'opposto di $(a_1,a_2)$ è $(-a_1,-a_2)$.
> Pertanto $(K^2,\boxplus)$ è un gruppo abeliano.
> ###### 2. Proprietà della moltiplicazione per scalare
> **1.  Distributività rispetto alla somma di vettori**
> Siano $\alpha\in K$ e $(a_1,a_2),(b_1,b_2)\in K^2$.
> $$
> \begin{aligned}
> \alpha\boxdot\left((a_1,a_2)\boxplus(b_1,b_2)\right)
> &=\alpha\boxdot(a_1+b_1,a_2+b_2)\\
> &=(\alpha(a_1+b_1),\alpha(a_2+b_2))\\
> &=(\alpha a_1+\alpha b_1,\alpha a_2+\alpha b_2)\\
> &=(\alpha a_1,\alpha a_2)\boxplus(\alpha b_1,\alpha b_2)\\
> &=\left(\alpha\boxdot(a_1,a_2)\right)\boxplus\left(\alpha\boxdot(b_1,b_2)\right)
> \end{aligned}
> $$
> Quindi:
> $$
> \alpha\boxdot(u\boxplus v)=(\alpha\boxdot u)\boxplus(\alpha\boxdot v)
> $$
> **2. Distributività rispetto alla somma degli scalari**
> Siano $\alpha,\beta\in K$ e $(a_1,a_2)\in K^2$.
> $$
> \begin{aligned}
> (\alpha+\beta)\boxdot(a_1,a_2)
> &=((\alpha+\beta)a_1,(\alpha+\beta)a_2)\\
> &=(\alpha a_1+\beta a_1,\alpha a_2+\beta a_2)\\
> &=(\alpha a_1,\alpha a_2)\boxplus(\beta a_1,\beta a_2)\\
> &=\left(\alpha\boxdot(a_1,a_2)\right)\boxplus\left(\beta\boxdot(a_1,a_2)\right)
> \end{aligned}
> $$
> Quindi:
> $$
> (\alpha+\beta)\boxdot u=(\alpha\boxdot u)\boxplus(\beta\boxdot u)
> $$
> **3. Associatività della moltiplicazione per scalare**
> Siano $\alpha,\beta\in K$ e $(a_1,a_2)\in K^2$.
> $$
> \begin{aligned}
> (\alpha\beta)\boxdot(a_1,a_2)
> &=((\alpha\beta)a_1,(\alpha\beta)a_2)\\
> &=(\alpha(\beta a_1),\alpha(\beta a_2))\\
> &=\alpha\boxdot(\beta a_1,\beta a_2)\\
> &=\alpha\boxdot\left(\beta\boxdot(a_1,a_2)\right)
> \end{aligned}
> $$
> Quindi:
> $$
> (\alpha\beta)\boxdot u=\alpha\boxdot(\beta\boxdot u)
> $$
> **4. Elemento neutro della moltiplicazione per scalare**
> Poiché $1\in K$ è l'elemento neutro della moltiplicazione in $K$:
> $$
> \begin{aligned}
> 1\boxdot(a_1,a_2)
> &=(1\cdot a_1,1\cdot a_2)\\
> &=(a_1,a_2)
> \end{aligned}
> $$
> Quindi:
> $$
> 1\boxdot u=u
> $$
> ##### Tesi
> Abbiamo verificato tutti gli assiomi di spazio vettoriale.
> Pertanto:
> $$
> \boxed{(K^2,K,\boxplus,\boxdot)\text{ è uno spazio vettoriale}}
> $$
> La dimostrazione si generalizza analogamente a $K^n$.



---
## Proprietà elementari degli spazi vettoriali

Le seguenti proprietà derivano direttamente dalla definizione di spazio vettoriale.

### Legge di annullamento del prodotto

Per ogni $u\in V$ e per ogni $\alpha\in K$:

$$
\boxed{\alpha\boxdot u=0\iff \alpha=0\text{ oppure }u=0}
$$

> [!tip]- Dimostrazione
> Dimostriamo prima che, se $\alpha=0$, allora:\
> $0\boxdot u=0$
>
> Infatti:
> $$
> 0\boxdot u=(0+0)\boxdot u
> $$
>
> e, per la distributività rispetto alla somma di scalari:
> $$
> 0\boxdot u=(0\boxdot u)\boxplus(0\boxdot u)
> $$
>
> Sommiamo a entrambi i membri l'opposto di $0\boxdot u$:
> $$
> 0=(0\boxdot u)\boxplus(-(0\boxdot u))
> $$
>
> $$
> =[(0\boxdot u)\boxplus(0\boxdot u)]\boxplus(-(0\boxdot u))
> $$
>
> Per associatività:
> $$
> 0=(0\boxdot u)\boxplus[(0\boxdot u)\boxplus(-(0\boxdot u))]
> $$
>
> $$
> =(0\boxdot u)\boxplus0
> $$
>
> quindi:
> $$
> \boxed{0\boxdot u=0}
> $$
>
> Dimostriamo ora che, se $u=0$, allora:\
> $\alpha\boxdot0=0$
>
> Infatti:
> $$
> \alpha\boxdot0=\alpha\boxdot(0\boxplus0)
> $$
>
> e, per la distributività rispetto alla somma di vettori:
> $$
> \alpha\boxdot0=(\alpha\boxdot0)\boxplus(\alpha\boxdot0)
> $$
>
> Con lo stesso ragionamento precedente, sommando l'opposto di $\alpha\boxdot0$, otteniamo:
> $$
> \boxed{\alpha\boxdot0=0}
> $$
>
> Abbiamo quindi dimostrato che:
> $$
> \alpha=0\text{ oppure }u=0\implies\alpha\boxdot u=0
> $$
>
> Dimostriamo ora l'implicazione opposta.\
> Supponiamo:
> $$
> \alpha\boxdot u=0
> $$
>
> Se $\alpha=0$, abbiamo finito.
>
> Se invece $\alpha\neq0$, poiché $K$ è un campo esiste $\alpha^{-1}$. Allora:
> $$
> \alpha^{-1}\boxdot(\alpha\boxdot u)=\alpha^{-1}\boxdot0
> $$
>
> Da quanto dimostrato prima:
> $$
> \alpha^{-1}\boxdot0=0
> $$
>
> mentre, per la compatibilità con il prodotto degli scalari:
> $$
> \alpha^{-1}\boxdot(\alpha\boxdot u)
> =
> (\alpha^{-1}\alpha)\boxdot u
> =
> 1\boxdot u
> =
> u
> $$
>
> quindi:
> $$
> u=0
> $$
>
> Pertanto:
> $$
> \boxed{\alpha\boxdot u=0\iff \alpha=0\text{ oppure }u=0}
> $$


### Opposto di un prodotto per scalare

Per ogni $\alpha\in K$ e per ogni $u\in V$:

$$
\boxed{-(\alpha\boxdot u)=(-\alpha)\boxdot u=\alpha\boxdot(-u)}
$$

> [!tip]- Dimostrazione
> Dimostriamo prima che:
> $$
> (-\alpha)\boxdot u=-(\alpha\boxdot u)
> $$
>
> Infatti:
> $$
> (\alpha\boxdot u)\boxplus((-\alpha)\boxdot u)
> $$
>
> per la distributività rispetto alla somma di scalari:
> $$
> =(\alpha+(-\alpha))\boxdot u
> $$
>
> $$
> =0\boxdot u
> $$
>
> $$
> =0
> $$
>
> Quindi $(-\alpha)\boxdot u$ è l'opposto di $\alpha\boxdot u$, perciò:
> $$
> (-\alpha)\boxdot u=-(\alpha\boxdot u)
> $$
>
> Dimostriamo ora che:
> $$
> \alpha\boxdot(-u)=-(\alpha\boxdot u)
> $$
>
> Infatti:
> $$
> (\alpha\boxdot u)\boxplus(\alpha\boxdot(-u))
> $$
>
> per la distributività rispetto alla somma di vettori:
> $$
> =\alpha\boxdot(u\boxplus(-u))
> $$
>
> $$
> =\alpha\boxdot0
> $$
>
> $$
> =0
> $$
>
> Quindi $\alpha\boxdot(-u)$ è l'opposto di $\alpha\boxdot u$, perciò:
> $$
> \alpha\boxdot(-u)=-(\alpha\boxdot u)
> $$
>
> Pertanto:
> $$
> \boxed{-(\alpha\boxdot u)=(-\alpha)\boxdot u=\alpha\boxdot(-u)}
> $$


### Legge di cancellazione rispetto al vettore

Per ogni $\alpha,\beta\in K$ e per ogni $u\in V\setminus\{0\}$:

$$
\boxed{\alpha\boxdot u=\beta\boxdot u\implies\alpha=\beta}
$$

> [!tip]- Dimostrazione
> Supponiamo:
> $$
> \alpha\boxdot u=\beta\boxdot u
> $$
>
> Sommiamo a entrambi i membri l'opposto di $\beta\boxdot u$:
> $$
> (\alpha\boxdot u)\boxplus(-(\beta\boxdot u))=0
> $$
>
> Per la proprietà precedente:
> $$
> -(\beta\boxdot u)=(-\beta)\boxdot u
> $$
>
> quindi:
> $$
> (\alpha\boxdot u)\boxplus((-\beta)\boxdot u)=0
> $$
>
> Per la distributività rispetto alla somma di scalari:
> $$
> (\alpha-\beta)\boxdot u=0
> $$
>
> Per la legge di annullamento del prodotto:
> $$
> \alpha-\beta=0
> \quad\text{oppure}\quad
> u=0
> $$
>
> Ma $u\neq0$, quindi:
> $$
> \alpha-\beta=0
> $$
>
> e dunque:
> $$
> \boxed{\alpha=\beta}
> $$



### Legge di cancellazione rispetto allo scalare

Per ogni $\alpha\in K\setminus\{0\}$ e per ogni $u,v\in V$:

$$
\boxed{\alpha\boxdot u=\alpha\boxdot v\implies u=v}
$$

> [!tip]- Dimostrazione
> Supponiamo:
> $$
> \alpha\boxdot u=\alpha\boxdot v
> $$
>
> Sommiamo a entrambi i membri l'opposto di $\alpha\boxdot v$:
> $$
> (\alpha\boxdot u)\boxplus(-(\alpha\boxdot v))=0
> $$
>
> Per la proprietà precedente:
> $$
> -(\alpha\boxdot v)=\alpha\boxdot(-v)
> $$
>
> quindi:
> $$
> (\alpha\boxdot u)\boxplus(\alpha\boxdot(-v))=0
> $$
>
> Per la distributività rispetto alla somma di vettori:
> $$
> \alpha\boxdot(u\boxplus(-v))=0
> $$
>
> ossia:
> $$
> \alpha\boxdot(u-v)=0
> $$
>
> Per la legge di annullamento del prodotto:
> $$
> \alpha=0
> \quad\text{oppure}\quad
> u-v=0
> $$
>
> Ma $\alpha\neq0$, quindi:
> $$
> u-v=0
> $$
>
> e pertanto:
> $$
> \boxed{u=v}
> $$


---
## Sottospazi vettoriali

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

