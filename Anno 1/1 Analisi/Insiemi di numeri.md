---
Materia:
  - Analisi
tags:
  - Insiemi
Link risorse:
Libro:
Imparato: false
Ordine: -35
aliases:
---
Numeri naturali $\mathbb{N}$
$$
\mathbb{N}=\{0,1,2,3,4\dots\}
$$
Numeri interi relativi
$$
\mathbb{Z}=\{-2,-1,0,1,2\dots\}
$$
Numeri interi relativi
$$
\mathbb{Q}=\{\frac mn,m,n\in\mathbb{Z},n\ne 0\}
$$

Numeri reali

I gruppi includono l'altro con inclusione stretta.
$$
\mathbb{N}\subset\mathbb{Z}\subset\mathbb{Q}\subset\mathbb{R}
$$
>[!tip] Dimostrazione per assurdo
***Proposizione***
>$$\sqrt{ 2 }\not\in \mathbb Q$$
***Dimostrazione***
Ragiono per assurdo e nego la tesi $\sqrt{ 2 }\in \mathbb Q\implies \sqrt{ 2 }=\frac mn$
-$m,n \in \mathbb N\ \ n \ne 0$
-$m,n$ sono **primi tra loro** e non hanno divisori in comune
$$\sqrt{ 2 }=\frac mn\implies 2=\frac {m^2}{n^2}\implies m^2=2n^2\implies m^2 \text{ è un numero pari}\implies $$
$$\implies m \text{ è pari}$$
Dimostriamo che il quadrato di un numero dispari è dispari:
$$n=2k+1\implies(2k+1)^2=4k^2+1+4k=4k^2+4k+1$$
primo e secondo elemento elemento sempre pari, +1 sempre dispari. quadrati dei numeri dispari quindi +1 rimane sempre quindi si ottiene sempre numero dispari.
-Quadrato di un numero dispari è dispari
$$m=2k\implies 4k=2n^2\implies 2k^2=n^2\implies n^2\text{ è pari}\implies n \text{ è pari}$$
Sia $n$ che $m$ sono pari, ma ciò è **impossibile** poiché abbiamo definito che sono primi tra di loro, ciò è assurdo e dimostra che $\sqrt{ 2 }\not\in\mathbb Q$

---
## Proprietà algebriche
Su $\mathbb R$ sono definite due operazioni: **somma** e **prodotto** (in funzioni # Proprietà di un'operazione interna)
### Somma
- $a+b=b+a\ \ \forall a,b\in\mathbb R$ commutativa
- $a+(b+c)=(a+b)+c\ \ \forall a,b,c\in\mathbb R$ associativa
- $\exists 0\in\mathbb R,\ \ 0+a=a\ \forall a\in A$ elemento neutro
- $\forall a\in\mathbb R\ \ \exists b\in\mathbb R:a+b=0\ b=-a$ elemento inverso
### Prodotto
- $a\cdot b=b\cdot a\ \ \forall a,b\in\mathbb R$ commutativa
- $a\cdot(b\cdot c)=(a\cdot b)\cdot c\ \ \forall a,b,c\in\mathbb R$ associativa
- $\exists 1\in\mathbb R,\ \ 0\cdot a=a\ \forall a\in A$ elemento neutro
- $\forall a\in\mathbb R\ \ \exists b\in\mathbb R:  a\cdot b=1\ b=\frac{1}{a}$ elemento inverso
### Legame
- $a\cdot(b+c)=a\cdot b+a\cdot c$ distributiva

---
## Proprietà ordinamento
$$
a,b\in\mathbb R,a\underline<b\text{ oppure } b\underline<a
$$
- $a \underline{<}a\ \forall a\in A$
- $\text{Se }a \underline{<}b \text{ e se }\ b \underline{<}a\implies a=b$
- $\text{Se }a \underline{<}b \text{ e }\ b \underline{<}c\implies a \underline{<}c$

1. $\text{Se }a \underline{<}b\implies a+c \underline{<}b+c\ \ \forall a,b,c\in\mathbb R$
2.  $\text{Se }a \underline{<}b\implies a\cdot c \underline{<}b\cdot c\ \ \forall a,b\in\mathbb R\ \ \forall c\in\mathbb R,\ c \underline{>}0$
3.  $\text{Se }a \underline{<}b\implies a\cdot c \underline{>}b\cdot c\ \ \forall a,b\in\mathbb R\ \ \forall c\in\mathbb R,\ c \underline{<}0$

---
## Assioma di continuità
Siano $A,B$ sottoinsiemi di $\mathbb R$, separati
$$
A \underline{\subset}\mathbb R,\ \ B\underline{\subset}\mathbb R,\ \ \forall a\in A,\ \ a \underline{<}b\ \ \forall b\in B
$$
esiste un numero reale $c$ tale che 
$$
\exists c\in\mathbb R: a \underline{<}c \underline{<}b\ \ \forall a\in A\text{ e }\forall b\in B
$$

Esiste sempre l'elemento di separazione

>[!example] Esempio
$$A=\{a\in\mathbb Q;a>0,a^2 \underline{<}2\}$$
$$B=\{a\in\mathbb Q;a>0,a^2 \underline{>}2\}$$
$$\exists c\in\mathbb Q:a \underline{<}c \underline{<}b\ \ \forall a\in A\text{ e }\forall b\in B$$
$$\boxed{c=\sqrt{ 2 }}$$

