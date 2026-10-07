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
>[!info] Definizione
>Siano $A,B,C$ insiemi. Diremo **operazione binaria** ogni applicazione $\perp=A\times B\to C$
Se, in particolare, $A=B=C$ allora diremo che $\perp:A\times A\to A$ è **un'operazione binaria interna** su $A$.
Se uno dei due insiemi da cui prendiamo gli operandi è diverso dall'insieme di arrivo, parliamo di **operazione esterna**.

^5c4388


Un'**operazione** è un'applicazione
$$  \perp=A\times B\to C  $$
che associa alla coppia
$$  (a,b)\rightsquigarrow c=a\perp b=\perp (a,b)  $$

>[!example] Esempio
>Una somma tra numeri naturali restituisce sempre un numero naturale.
$$  +:\mathbb N\times\mathbb N\to\mathbb N  $$
La differenza tra numeri naturali invece è un'operazione esterna.
$$  -:\mathbb N\times\mathbb N\to\mathbb Z  $$


---
## Proprietà di un'operazione interna
Sia $A,\ \perp:A\times A\to A$ un'operazione interna.

#### Associatività
L'operazione è **associativa** se
$$  
\forall x,y,z\in A  
$$
e
$$  
x\perp(y_z)=(x_y)\perp z  
$$


#### Elemento neutro
L'operazione ammette un **elemento neutro** $e\in A$ se
$$  
\exists e\in A:\forall x\in A  
$$
vale
$$  
e\perp x=x\perp e=x  
$$

Se un elemento neutro esiste, allora è **unico**.

>[!tip] Dimostrazione
>Supponiamo che $e$ ed $e'$ siano entrambi elementi neutri.
>Poiché $e$ è neutro, $e\perp e'=e'$.
ma poiché $e'$ è neutro, $e\perp e'=e$, quindi
$$  \boxed{e=e'}  $$

#### Elemento inverso
Supponiamo che esista un elemento neutro $e$.

Un elemento $x\in A$ ammette un **inverso** se esiste $y\in A$ tale che

$$  
x_y=y_x=e  
$$

Se l'operazione è l'addizione, l'inverso viene chiamato **opposto**:

$$  
x+(-x)=0  
$$

Se l'operazione è la moltiplicazione, l'inverso viene chiamato **reciproco**:

$$  
x\cdot x^{-1}=1  
$$


#### Commutatività
L'operazione è **commutativa** se

$$  
\forall a,b\in A  
$$

vale

$$  
a_b=b_a  
$$


---
## Operazioni sulle classi di equivalenza
Quando definiamo un'operazione sulle [[Relazioni|classi di equivalenza]] dobbiamo verificare che il risultato **non dipenda dal rappresentante scelto**.

Per esempio, se

$$  
[a]=[a']  
$$
e
$$  
[b]=[b']  
$$
vogliamo che
$$  
[a]\perp [b]  
$$

dia lo stesso risultato sia usando $a,b$ sia usando $a',b'$.
Cioè dobbiamo avere

$$  
[a\perp b]=[a'\perp b']  
$$

Quando ciò accade diciamo che l'operazione è **ben definita** o **ben posta** sulle classi di equivalenza.

Questa proprietà è legata alla nozione di **congruenza** rispetto all'operazione.

