---
Materia:
  - Algebra Lineare
  - Geometria
tags:
Link risorse:
Libro:
Imparato: true
Ordine: 8
aliases:
---
>[!info] Definizione
>$X$ insieme non vuoto e $m,n\in \mathbb{N}$. Una **matrice** su $X$ di tipo $m\times n$ è un'[[Anno 2/1. Geometria/1 Algebra/1. Logica rudimentale ed insiemi/Funzioni|applicazione]]
$$A:\{1,\dots,m\}\times\{1,\dots ,n\}\to X$$
$$ (i,j)\rightsquigarrow A(i,j)=a^i_{j} $$

$$
\begin{array}{c@{\;}c}
 & \begin{array}{ccc}
1 & 2 & 3
\end{array}
\\[-2mm]
\begin{array}{c}
1\\
2
\end{array}
&
\begin{pmatrix}
a_{1}^1 & a_{2}^1 & a_{3}^1\\
a_{1}^2 & a_{2}^2 & a_{3}^2
\end{pmatrix}
\end{array}
$$

---
## Insieme delle matrici
$$
M_{mn}(X)=\{(a^i_{j})|a^i_{j}\in X,i\in\{1,\dots,m\} ,j\in\{1,\dots,n\} \}
$$

---
## Operazioni con le matrici
Sia $K$ un [[Strutture algebriche#^1ed1df|campo]].

L'insieme delle matrici di tipo $m\times n$ a coefficienti in $K$ si indica con

$$
M_{m\times n}(K).
$$

Su questo insieme possiamo definire due operazioni.

### Somma tra matrici
$$
+:M_{m\times n}(K)\times M_{m\times n}(K)\to M_{m\times n}(K)
$$

definita componente per componente:

$$
(a_j^i)+(b_j^i)=(a_j^i+b_j^i).
$$

In pratica, si sommano gli elementi che occupano la stessa posizione.

> [!example] Esempio
> $$
> \begin{pmatrix}
> -2 & 1\\
> \frac32 & 4\\
> 7 & 0
> \end{pmatrix}
> +
> \begin{pmatrix}
> 3 & -1\\
> -1 & -3\\
> 0 & 1
> \end{pmatrix}
> =
> \begin{pmatrix}
> 1 & 0\\
> \frac12 & 1\\
> 7 & 1
> \end{pmatrix}
> $$

### Moltiplicazione per uno scalare
$$
\cdot:K\times M_{m\times n}(K)\to M_{m\times n}(K)
$$

definita da

$$
(\alpha,A)\mapsto \alpha A.
$$

Se

$$
A=(a_j^i),
$$

allora

$$
\alpha A=(\alpha a_j^i).
$$

Quindi ogni elemento della matrice viene moltiplicato per $\alpha$.

> [!example] Esempio
> $$
> 5
> \begin{pmatrix}
> -\pi & 7\\
> 11 & -4
> \end{pmatrix}
> =
> \begin{pmatrix}
> -5\pi & 35\\
> 55 & -20
> \end{pmatrix}.
> $$

Si può dimostrare che

$$
\left(M_{m\times n}(K),+,\cdot\right)
$$

è uno **spazio vettoriale su $K$**.

---
### Matrice trasposta
Sia

$$
A=(a_j^i)\in M_{m\times n}(K).
$$

La **matrice trasposta** di $A$, indicata con

$$
{}^tA
$$

è la matrice

$$
{}^tA\in M_{n\times m}(K)
$$

ottenuta scambiando righe e colonne.

Se

$$
{}^tA=(b_j^i),
$$

allora

$$
b_j^i=a_i^j.
$$

> [!example] Esempio
> $$
> A=
> \begin{pmatrix}
> -2 & 1\\
> \frac32 & 4\\
> 7 & 0
> \end{pmatrix}
> $$
>
> allora
>
> $$
> {}^tA=
> \begin{pmatrix}
> -2 & \frac32 & 7\\
> 1 & 4 & 0
> \end{pmatrix}.
> $$

---
## Righe e colonne come vettori
Le righe di una matrice

$$
A\in M_{m\times n}(K)
$$

possono essere considerate come [[Vettori liberi ed operazioni|vettori]] di $K^n$.

La $i$-esima riga è

$$
a^i=(a_1^i,\dots,a_n^i)\in K^n.
$$

Le colonne possono invece essere considerate come vettori di $K^m$.

La $j$-esima colonna è

$$
a_j=
\begin{pmatrix}
a_j^1\\
\vdots\\
a_j^m
\end{pmatrix}
\in K^m.
$$


---
## Matrice a gradini

^5ed966

Una matrice si dice **ridotta a gradini per righe** se:
1. tutte le righe nulle si trovano sotto le righe non nulle;
2. il primo elemento non nullo di ogni riga si trova più a destra del primo elemento non nullo della riga precedente.

Il primo elemento non nullo di una riga prende il nome di **pivot**. ^b83cec

$$
\begin{pmatrix}
\boxed X & X & X & X \\
0 & \boxed X & X & X \\
0 & 0 & \boxed X & X \\
0 & 0 & 0 & \boxed X
\end{pmatrix}
$$

>[!example]- Esempio
>Ad esempio:
>$$\begin{pmatrix}\boxed{5}&7&1&4\\0&0&\boxed{1}&0\\0&0&0&0\end{pmatrix}$$
>è a gradini.
>Invece:
>$$\begin{pmatrix}5&7&1&4\\0&0&0&0\\0&0&1&0\end{pmatrix}$$
>non è a gradini, perché una riga nulla compare prima di una riga non nulla.


### Matrice completamente ridotta a gradini
Una matrice si dice **completamente ridotta a gradini** se: ^f4edcd
- è ridotta a gradini;
- ogni pivot è uguale a $1$;
- gli elementi sopra ogni pivot sono nulli.

$$
\begin{pmatrix}
\boxed1&0&0& X\\
0&\boxed1&0&X\\
0&0&\boxed1&X
\end{pmatrix}
$$
Ogni pivot è $1$ ed è **l'unico elemento non nullo della propria colonna**.

---
## Operazioni elementari sulle righe

^119330

Sia $A\in M_{m\times n}(K)$, le **operazioni elementari sulle righe** sono:

### Scambio di due righe

$$
R_i\leftrightarrow R_j
$$
>[!example]- Esempio
>Scambiamo tra di loro la prima e ultima riga: $R_{1} \leftrightarrow R_{3}$
>$$\begin{pmatrix}1 & 2 & 3 \\4 & 5 & 6 \\7 & 8 & 9\end{pmatrix}\to\begin{pmatrix}7 & 8 & 9 \\4 & 5 & 6 \\1 & 2 & 3 \\\end{pmatrix}$$


### Moltiplicazione di una riga per uno scalare non nullo

$$
R_i\to\beta R_i,
\qquad
\beta\in K\setminus\{0\}
$$

> [!example] Esempio
> Moltiplichiamo la seconda riga per $2$: $R_2\to2R_2$
>
> $$
> \begin{pmatrix}
> 1 & 2 & 3\\
> 4 & 5 & 6\\
> 7 & 8 & 9
> \end{pmatrix}
> \to
> \begin{pmatrix}
> 1 & 2 & 3\\
> 8 & 10 & 12\\
> 7 & 8 & 9
> \end{pmatrix}
> $$



### Somma a una riga di un multiplo di un'altra riga

$$
R_i\to R_i+\lambda R_j,
\qquad
\lambda\in K
$$



> [!example] Esempio
> Sommiamo alla seconda riga $-4$ volte la prima riga: $R_2\to R_2-4R_1$
>
> $$
> \begin{pmatrix}
> 1 & 2 & 3\\
> 4 & 5 & 6\\
> 7 & 8 & 9
> \end{pmatrix}
> \to
> \begin{pmatrix}
> 1 & 2 & 3\\
> 0 & -3 & -6\\
> 7 & 8 & 9
> \end{pmatrix}
> $$
