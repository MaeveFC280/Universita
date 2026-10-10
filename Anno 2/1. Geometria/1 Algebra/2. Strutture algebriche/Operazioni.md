---
Materia:
  - Geometria
  - Algebra Lineare
tags:
Link risorse:
Libro:
Imparato: true
Ordine: 4
aliases:
---
## Operazioni binarie
>[!info] Definizione
>Siano $A,B,C$ insiemi non vuoti. Un'**operazione binaria** è un'applicazione:
>$$
>\perp:A\times B\to C
>$$
>che associa a ogni coppia $(a,b)\in A\times B$ un unico elemento $c\in C$:
>$$
>(a,b)\longmapsto c=a\perp b=\perp(a,b)
>$$
>Se $A=B=C$, l'operazione $\perp:A\times A\to A$ si dice **interna** su $A$.
>Una **operazione esterna** su $B$ con operatori in $A$ ha invece forma $\perp:A\times B\to B$, con il primo operando che agisce sugli elementi di $B$ (ad esempio, il prodotto di uno scalare per un vettore).

^5c4388

>[!example]- Esempi
>La somma su $\mathbb N$ è un'operazione interna:
>$$
>+:\mathbb N\times\mathbb N\to\mathbb N
>$$
>La sottrazione tra numeri naturali **non è interna su $\mathbb N$**, perché il risultato può essere negativo. Possiamo però definirla come applicazione:
>$$
>-:\mathbb N\times\mathbb N\to\mathbb Z
>$$
>Il prodotto per uno scalare è un esempio di operazione esterna su uno spazio vettoriale $V$ su un campo $K$:
>$$
>\cdot:K\times V\to V,\qquad (\lambda,v)\longmapsto\lambda v
>$$

---
## Proprietà di un'operazione interna
Sia $\perp:A\times A\to A$ un'operazione interna su $A$.

### Associatività
L'operazione è **associativa** se, per ogni $x,y,z\in A$:
$$
\boxed{(x\perp y)\perp z=x\perp(y\perp z)}
$$
In questo caso il modo in cui si raggruppano gli operandi non cambia il risultato.

### Commutatività
L'operazione è **commutativa** se, per ogni $x,y\in A$:
$$
\boxed{x\perp y=y\perp x}
$$
L'ordine degli operandi non cambia il risultato.

### Elemento neutro
L'operazione ammette un **elemento neutro** $e\in A$ se:
$$
\exists e\in A:\ \forall x\in A,\quad e\perp x=x\perp e=x
$$
Se esiste, l'elemento neutro è **unico**.

>[!tip] Dimostrazione
>Supponiamo che $e$ ed $e'$ siano entrambi elementi neutri.
>Poiché $e$ è neutro, applicandolo a $e'$ otteniamo:
>$$
>e\perp e'=e'
>$$
>Poiché anche $e'$ è neutro, si ha:
>$$
>e\perp e'=e
>$$
>Pertanto:
>$$
>\boxed{e=e'}
>$$

### Elemento inverso
Supponiamo che $\perp$ ammetta un elemento neutro $e$. Un elemento $x\in A$ si dice **invertibile** se esiste $y\in A$ tale che:
$$
\boxed{x\perp y=y\perp x=e}
$$
L'elemento $y$ si dice **inverso** di $x$.

- Per l'addizione, l'inverso è detto **opposto**: $x+(-x)=(-x)+x=0$.
- Per la moltiplicazione, l'inverso è detto **reciproco**: $x\cdot x^{-1}=x^{-1}\cdot x=1$, quando esiste.

>[!info] Proposizione — Unicità dell'inverso
>Se $\perp$ è **associativa** e ammette un elemento neutro, l'inverso di un elemento, quando esiste, è unico.

>[!tip] Dimostrazione
>Supponiamo che $y,z\in A$ siano entrambi inversi di $x\in A$. Allora:
>$$
>x\perp y=y\perp x=e,\qquad x\perp z=z\perp x=e
>$$
>Usando l'elemento neutro e l'associatività:
>$$
>\begin{aligned}
>y&=y\perp e\\
>&=y\perp(x\perp z)\\
>&=(y\perp x)\perp z\\
>&=e\perp z=z
>\end{aligned}
>$$
>Dunque $\boxed{y=z}$.

>[!info] Proposizione — Inverso di un prodotto
>Se $\perp$ è associativa, ammette un elemento neutro e $x,y\in A$ sono invertibili, allora anche $x\perp y$ è invertibile e:
>$$
>\boxed{(x\perp y)^{-1}=y^{-1}\perp x^{-1}}
>$$
>**Attenzione:** nell'inverso di un prodotto, l'ordine dei fattori si inverte.

>[!tip] Dimostrazione
>Verifichiamo che $y^{-1}\perp x^{-1}$ è inverso di $x\perp y$ da entrambi i lati.
>Per associatività:
>$$
>\begin{aligned}
>(x\perp y)\perp(y^{-1}\perp x^{-1})
>&=x\perp(y\perp y^{-1})\perp x^{-1}\\
>&=x\perp e\perp x^{-1}=e
>\end{aligned}
>$$
>Analogamente:
>$$
>\begin{aligned}
>(y^{-1}\perp x^{-1})\perp(x\perp y)
>&=y^{-1}\perp(x^{-1}\perp x)\perp y\\
>&=y^{-1}\perp e\perp y=e
>\end{aligned}
>$$
>Quindi $y^{-1}\perp x^{-1}$ è l'inverso di $x\perp y$.

Le proprietà appena viste serviranno a definire le [[Strutture algebriche|strutture algebriche]], in particolare i gruppi.

---
## Operazioni sulle classi di equivalenza
Quando definiamo un'operazione sulle [[Relazioni|classi di equivalenza]], dobbiamo verificare che il risultato **non dipenda dai rappresentanti scelti**.

Supponiamo che $\sim$ sia una relazione di equivalenza su $A$ e che $\perp:A\times A\to A$ sia un'operazione interna. Vorremmo definire sulle classi:
$$
[a]\perp[b]:=[a\perp b]
$$
La definizione è **ben posta** (o **ben definita**) se, ogni volta che:
$$
[a]=[a'],\qquad[b]=[b']
$$
si ha:
$$
\boxed{[a\perp b]=[a'\perp b']}
$$
Equivalentemente:
$$
a\sim a'\ \land\ b\sim b'\quad\Longrightarrow\quad a\perp b\sim a'\perp b'
$$
In tal caso si dice che la relazione di equivalenza è una **congruenza rispetto all'operazione**.

>[!example]- Esempio: addizione delle classi modulo 3
>Su $\mathbb Z$ consideriamo la congruenza modulo $3$:
>$$
>a\sim b\iff 3\mid(a-b)
>$$
>Definiamo l'addizione sulle classi mediante:
>$$
>[a]+[b]=[a+b]
>$$
>Se $[a]=[a']$ e $[b]=[b']$, allora $3$ divide sia $a-a'$ sia $b-b'$. Di conseguenza divide anche:
>$$
>(a+b)-(a'+b')=(a-a')+(b-b')
>$$
>Pertanto $[a+b]=[a'+b']$: il risultato è indipendente dai rappresentanti scelti e l'operazione è ben definita.
