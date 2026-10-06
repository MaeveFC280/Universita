---
Materia:
  - Geometria
  - Algebra Lineare
tags:
  - Insiemi
Link risorse:
Libro:
Imparato: true
Ordine: 0
aliases:
---
Un insieme è una collezione di oggetti, che sono elementi dell’insieme e appartengono all'insieme.
Può essere definito:
- enumerando i suoi elementi: $A=\{1,2,3\}$ 
- tramite una sua proprietà: $A=\{x\in B:P(x)\}$

Due insiemi sono uguali se hanno gli stessi elementi.

Un insieme definito tramite una proprietà sempre falsa è l'insieme vuoto $\varnothing$.
> [!example]
>
$$
\{x\in\mathbb{R}\mid x^2<0\}=\varnothing
$$
 
 Siano $A,B$ insiemi. Diciamo:
-   $A$ è **sottoinsieme** di $B$, e scriviamo  $A \underline{\subset}B$, se **ogni elemento di  $A$ è anche in**  $B$: $A\underline\subset B\leftrightarrow \forall x \in A,\ x\in B$
-   $A$ è **sottoinsieme proprio** di $B$ se esiste un elemento di $B$ che non è in $A$: $A\subsetneq B\Leftrightarrow A\subseteq B\text{ e }\exists x\in B:x\notin A$
-   $A$ e $B$  sono **disgiunti** se $A\cap B=\varnothing$


> [!example]
>
> $\mathbb{N}=\{1,2,3,\dots\}=\{x\mid x\ \text{è un numero naturale}\}$
>
> $\mathbb{Z}=\{0,+1,-1,+2,-2,\dots\}=\{x\mid x\ \text{è un numero relativo}\}$
>
> $\mathbb{Q}=\left\{\frac{m}{n}\mid m\in\mathbb{Z},n\in\mathbb{Z},n\neq0\right\}$

---
## Implicazione
**contronominale**

$$
P(x)\Rightarrow Q(x)\Leftrightarrow \neg Q(x)\Rightarrow \neg P(x)
$$

---
## Proprietà

$$
A=\{1,2,5\}\quad 5\in A\Rightarrow\{5\}\underline{\subset}A
$$

**Singleton**

Un singleton è un insieme formato da un solo elemento.

$$
5\in A\Rightarrow\{5\}\subseteq A
$$

Quindi:

$$
\{5\}\in\mathcal{P}(A)
$$

Il singleton di 5 appartiene all'insieme delle parti di $A$.

---
## Paradosso

$$
S=\{x|x\notin x\}

S\in S\Rightarrow S\notin S

S\notin S\Rightarrow S\in S
$$

Se $S$ appartiene a sé stesso, per la proprietà che definisce $S$ allora non appartiene a sé stesso.

Se invece $S$ non appartiene a sé stesso, allora soddisfa la proprietà che definisce $S$ e quindi deve appartenere a sé stesso.


$$
A\underline{\subset}B\Leftrightarrow\text{ogni elemento di A è anche elemento di B}
$$

$$
A=B\Leftrightarrow A\underline{\subset}B\text{ e }B\underline{\subset}A
$$

---
## Unione e intersezione

$$
A\cup B=\{x|x\in A\text{ oppure }x\in B\}
$$
$$

A\cap B=\{x|x\in A\text{ e }x\in B\}
$$

---
## Differenza

$$
A-B=\{x|x\in A\text{ e }x\notin B\}
$$

---
## Complemento

$$
B\underline{\subset}X\Rightarrow X-B=C_X(B)
$$

$C_X(B)$ si dice **complemento di B rispetto a X**.

---
## Coppie ordinate

Negli insiemi **l'ordine degli elementi non conta** e gli elementi ripetuti vengono considerati una sola volta.

Ad esempio:

$$
\{3,5\}=\{5,3\}
$$

e

$$
\{3,3\}=\{3\}.
$$

Nelle **coppie ordinate**, invece, l'ordine degli elementi è importante.

Ad esempio:

$$
(3,5)\neq(5,3).
$$

Gli elementi possono anche ripetersi:

$$
(3,3).
$$

Una coppia ordinata può essere rappresentata insiemisticamente come:

$$
(3,5)=\{\{3\},\{3,5\}\}
$$

mentre

$$
(5,3)=\{\{5\},\{5,3\}\}.
$$

Lo stesso concetto si estende a terne, quaterne e, più in generale, a $n$-uple.

Ad esempio:

$$
(3,5,7)
$$

è una terna ordinata.

---
## Prodotto cartesiano
Siano $A$ e $B$ due insiemi non vuoti.

Il **prodotto cartesiano** di $A$ e $B$ è l'insieme di tutte le coppie ordinate il cui primo elemento appartiene ad $A$ e il secondo appartiene a $B$:

$$
A\times B=\{(a,b)\mid a\in A,\ b\in B\}.
$$

>[!example] Esempio
>Siano
>$$
>A=\{x,y,z\}
>$$
>e
>$$
>B=\{1,2,3\}.
>$$
>
>Allora
>$$
>A\times B=
>\{
>(x,1),(x,2),(x,3),
>(y,1),(y,2),(y,3),
>(z,1),(z,2),(z,3)
>\}.
>$$

Se prendiamo come insieme $\mathbb R$, otteniamo:

$$
\mathbb R^2=\mathbb R\times\mathbb R.
$$

Quindi $\mathbb R^2$ è l'insieme di tutte le coppie ordinate di numeri reali:

$$
\mathbb R^2=
\{(x,y)\mid x,y\in\mathbb R\}.
$$

Analogamente:

$$
\mathbb R^3=
\mathbb R\times\mathbb R\times\mathbb R
$$

è l'insieme di tutte le terne ordinate di numeri reali:

$$
\mathbb R^3=
\{(x,y,z)\mid x,y,z\in\mathbb R\}.
$$

Più in generale:

$$
\mathbb R^n=
\underbrace{
\mathbb R\times\cdots\times\mathbb R
}_{n\text{ volte}}
$$

ed è l'insieme di tutte le $n$-uple di numeri reali:

$$
\mathbb R^n=
\{(x_1,\dots,x_n)\mid x_i\in\mathbb R\}.
$$

---

## Definizione di sottoinsieme

Si dice che $A$ è un sottoinsieme di $B$ se ogni elemento di $A$ appartiene anche a $B$:

$$
A\subseteq B
\iff
\forall x\,(x\in A\Rightarrow x\in B).
$$
---
## Relazioni

Una relazione $R$ tra $A$ e $B$ è un sottoinsieme del prodotto cartesiano:

$R\underline{\subset}A\times B$

Esempio:

$R=\{(x,3),(y,2)\}$

$xR3\Leftrightarrow(x,3)\in R$

$y\not R3\Leftrightarrow(y,3)\notin R$

Se $A,B$ sono non vuoti e:

$R\underline{\subset}A\times B$

allora:

$R^{-1}=\{(b,a)|(a,b)\in R\}\underline{\subset}B\times A$

si dice **relazione inversa di R**.

---
## Applicazioni

Una applicazione da $A$ in $B$ è una relazione tra $A$ e $B$ tale che per ogni $a\in A$ esiste uno e un solo $b\in B$ associato ad a.

$\forall a\in A\ \exists!b\in B:(a,b)\in f$

Non è una applicazione:

$A\times B=\{(x,1),(x,2),(x,3),(y,1),(y,2),\dots\}$

perché lo stesso elemento x è associato a più elementi.

Esempio di applicazione:

$f=\{(x,7),(y,5),(z,3)\}$

$f(a)=b$

$b$ è l'immagine di a mediante $f$.

$f:A\rightarrow B$

$A$ è il **dominio** e $B$ è il **codominio**.

$Se X\underline{\subset}A:$

$f(X)=\{b\in B|\exists a\in X:f(a)=b\}$

equivalentemente:

$f(X)=\{f(a)|a\in X\}$

---
## Sottoinsieme codominio

Se $Y\underline{\subset}B:$

$$
f^{-1}(Y)=\{a\in A|f(a)\in Y\}
$$

si chiama **controimmagine** o **immagine inversa di Y mediante f**.

La freccia (quando a penna freccia ondulata):

$$
a\mapsto b
$$

significa che $a$ viene associato a $b$.

---
## Comporre applicazioni

Se:

$f:A\rightarrow B$

$g:B\rightarrow C$

allora:

$$
g\circ f:A\rightarrow C
$$

e:

$$
(g\circ f)(x)=g(f(x))
$$

Quindi si applica prima $f$ e poi $g$:

$$
x\rightarrow f(x)\rightarrow g(f(x))
$$