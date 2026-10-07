---
Materia:
  - Geometria
tags:
Link risorse:
Libro:
Imparato: false
Ordine: 8
aliases:
---
avendo campo $()K^n,+,\cdot)$
si può definire prodotto scalare tra due $K^n\times K^n\to K$
$$
(a_{1},a_{2},a_{3}\dots)(b_{1},b_{2},b_{3}\dots)\to a_{1}b_{1}+a_{2}b_{2}\dots
$$
prodotto scalare
- canonico
- standard

con K=R e operazioni usuali ($+,\cdot$)
$$
\mathbb{R}^3, s((3,-2,\pi),(4,1,2))=12-2+2\pi=10+2\pi
$$


si usa notazione che non mette nulla tra le due parantesi o pallino

ha proprietà commutativa, simmetria
1. $(a_{1},a_{2}\dots)(b_{1}\dotsb_{n})=(b_{1}\dots b_{n})(a_{1}\dots a_{n})$

$\forall u=(a_{1}\dots)\ \ v=(b_{1}\dots)\ \ w=(c_{1}\dots)$
2. $u\cdot(v+w)$=u**v+u**w
$u(\lambda v)=\lambda(u\cdot v)=(\lambda u)\cdot v$
$K=\mathbb{R}\ \ u\cdot u ≥ 0 \ \ 0\Leftrightarrow u= \underline{0}$

usiamo prodotto scalare per definire prodotto tra matrici

$$
A \in M_{\text{mn}} \qquad B\in M_{\text{np}}(K) \qquad (A,B)\text{conformabile} \Leftrightarrow \text{numero di colorre di }A \text{ è uguale al numero di righe di } B
$$

le righe sono vettori di K n $a^m \in K^n \qquad b_{p}\in K^n$

quindi uso prodotto scalare perchè stesso spazio vettoriale numerico.

$$
\dots=
\begin{pmatrix}
\underline{a^1}\cdot\underline{b}_{1} & \dots & \underline{a^1}\cdot\underline{b}_{p} \\
\dots  & \dots & \dots\\

\underline{a^n}\cdot\underline{b}_{1} & \dots & \underline{a^n}\cdot\underline{b}_{p} \\
\end{pmatrix}
$$


>[!example]
$$A= \begin{pmatrix}2 & 1 \\0 & 3 \\-4 & 6\end{pmatrix}\in M_{32}(\mathbb{R})\qquadB= \begin{pmatrix}5 & -7 & 0 & 9 \\2 & 3 & 1 & 0\end{pmatrix}\in M_{24}(\mathbb{R})\qquadAB=?$$
$$\underline{a^1}=(2,1)per (5,2),(-7,3)(0,1)(9,0)$$
vabbè qui metto impilati i vari a alla e affianco i b per incorciarli tra di loro
$$AB=\begin{pmatrix}12 & -11 & 1 & 18 \\6 & 9 & 3 & 0 \\-8 & 46 & 6 & -36\end{pmatrix}$$
BA invece non è confromabile perchè numero righe e colonne non compatibile

c'è elemento neutro pk la **matrice quadrata identica**/ **unitaria**
$$
I_{n}=\begin{pmatrix}
1 & 0 \\
0 & 1
\end{pmatrix}
$$

tutte matrici quadrate sono invertibili


## Roba in cui serve per sistema
Matrice A coefficienti per X delle variabili
$$
\begin{pmatrix}
a_{11}&a_{12}&\dots&a_{1n}\\
a_{21}&a_{22}&\dots&a_{2n}\\
\vdots&\vdots&&\vdots\\
a_{m1}&a_{m2}&\dots&a_{mn}
\end{pmatrix}

\begin{pmatrix}
x_{1} \\
\vdots \\
x_{n}
\end{pmatrix}
=
\begin{pmatrix}
a_{1}^1x_{1}+a_{2}^1x_{2}+\dots+a_{n}^1x_{n} \\
a_{1}^nx_{1}+a_{2}^nx_{2}+\dots+a_{n}^nx_{n} \\
\dots \\
a_{1}^nx_{1}+a_{2}^nx_{2}+\dots+a_{n}^nx_{n}
\end{pmatrix}
$$
$$
\Sigma:AX=\underline{b}
$$
forma matriciale

$$
Gl_{n}(K)=\{ A\in M_{n}(K)| a\text{ è invertibile ridpryyo al prodotto righe per colonne}   \}
$$
**gruppo generale lineare** d ordine $n$ su $K$.

### Proprietà
1. $A\in M,B\in M_{mp},\in M\ \ (AB)C\in M_{mp}=(BC)\in M_{nq}$
2. $A,B\in M_{mn}(K),C\in M_{np}(K)\ \ AC+BC\in M_{mp}=(A+B)C$ pure $A\in\dots A(C+B)=AB+AC$
3. $A\in M,B\in M_{mp\ }\lambda\in K\ \ (\lambda A)B=\lambda(AB)=A(\lambda B)$

dimostrare che lo spazio dei cosi omogenei è chiuso e quindi sottospaizo vettoriale.

sistema omogeneo $\Sigma_{0}:AX=0$
$$
S=\{ \underline{}y(y_{1}\dots)\in K^n|A\begin{pmatrix}
y_{1} \\
\dots \\
yn
\end{pmatrix} 
=0

\}
$$

$A(\begin{pmatrix}y \\  y\end{pmatrix})+\begin{pmatrix}z \\  z\end{pmatrix}=A(y\dots)+A(z)=0+0=0$

se moltiplico per uno scalare lambda us proprietà 3
$$
A(\lambda \begin{pmatrix}
y_{1} \\
\dots \\
y_{n}
\end{pmatrix})
=\lambda(A\begin{pmatrix}
y \\
\dots \\
y
\end{pmatrix})=\lambda_{0}=0\implies \lambda(y\dots)\in S_{0}
$$

quindi dimostrato sottoinsieme


un esempio con (1,-2,4) $0,1,3$ $lmabda_{1}=3\lambda_{2}=4$ credo

se sistema ha soluzione w combinazione lineare, altrimenti no.
$w=(-3,7,4w=\alpha_{1}v_{1}+\alpha_{2}v_{2})$
$\exists \alpha_{1},\alpha_{2}\in \mathbb{R}$


## proposizione
sottospazio vettoriale 
1. $L(x)$ è uno sottospazio vettoriale di $V$ (dimostrare che è linearmente chiusa?) (si dice x sistema geometrico di L(x))
2. $AW\underline \subset V$ W sottospazio di V $X\subset W\implies L(x)\subset W$