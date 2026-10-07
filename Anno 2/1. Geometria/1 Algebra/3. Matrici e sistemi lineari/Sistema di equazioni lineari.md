---
Materia:
  - Algebra Lineare
  - Geometria
tags:
Link risorse:
Libro:
Imparato: true
Ordine: 10
aliases:
---
>[!info] Definizione
>Considerando il [[Strutture algebriche#^1ed1df|campo]] $(K,+,\cdot)$ e $m,n\in \mathbb{N}$
>Un **sistema lineare** di $m$ equazioni su $K$ in $n$ incognite è una [[n-upla]] di equazioni lineari su $K$.
$$ \Sigma:\begin{cases}a_{11}x_1+a_{12}x_2+\dots+a_{1n}x_n=0\\a_{21}x_1+a_{22}x_2+\dots+a_{2n}x_n=0\\\vdots\\a_{m1}x_1+a_{m2}x_2+\dots+a_{mn}x_n=0\end{cases} $$
> Una soluzione di $\Sigma$ è una [[n-upla]] che risulta essere soluzione di tutte le equazioni di $\Sigma$ .

- $\Sigma$ è **compatibile** quando ammette almeno una soluzione ($S\ne\oslash$).
- Due sistemi $\Sigma_{1},\Sigma_{2}$ sono **equivalenti** e hanno le stesso soluzioni $S_{1}=S_{2}$.
- Un sistema lineare è **omogeneo** quando tutti i termini noti sono uguali a zero.

>[!example]-
>$n=4\qquad K=\mathbb{Q}\qquad m=1\qquad 2x_{2}-x_{3}+3x_{4}=1\Leftrightarrow x_{3}=2x_{1}+3x_{4}-1$
>$$S=\{(\overline x_{1},\overline x_{2},2\overline x_{2}+3\overline x_{4},-1,\overline x_{4}|\overline x_{1},\overline x_{2},\overline x_{4}\in \mathbb{Q}\})$$
>Modo alternativo per risolverlo: $2x_{2}=x_{3}-3x_{4}+1\to x_{2}=\frac{1}{2}x_{3}-\frac{3}{2}x_{4}+\frac{1}{2}$
>$$S=\left\{ (\overline x_{1}, \frac{1}{2}x_{3}-\frac{3}{2}x_{4}+\frac{1}{2},\overline x_{3},\overline x_{4}|\overline x_{1},\overline x_{3},\overline x_{4}\in \mathbb{Q} \right\})$$

---
## Matrice associata a un sistema
Consideriamo il sistema:

$$
\Sigma:
\begin{cases}
a_{11}x_1+\dots+a_{1n}x_n=b_1\\
a_{21}x_1+\dots+a_{2n}x_n=b_2\\
\vdots\\
a_{m1}x_1+\dots+a_{mn}x_n=b_m
\end{cases}
$$

I coefficienti delle incognite possono essere raccolti nella **[[Matrici|matrice]] dei coefficienti**:

$$
A=
\begin{pmatrix}
a_{11}&a_{12}&\dots&a_{1n}\\
a_{21}&a_{22}&\dots&a_{2n}\\
\vdots&\vdots&&\vdots\\
a_{m1}&a_{m2}&\dots&a_{mn}
\end{pmatrix}.
$$

Se aggiungiamo anche i termini noti otteniamo la **[[Matrici|matrice]] completa** del sistema:

$$
A|b=
\left(
\begin{array}{cccc|c}
a_{11}&a_{12}&\dots&a_{1n}&b_1\\
a_{21}&a_{22}&\dots&a_{2n}&b_2\\
\vdots&\vdots&&\vdots&\vdots\\
a_{m1}&a_{m2}&\dots&a_{mn}&b_m
\end{array}
\right).
$$

Quindi **ogni riga della matrice completa corrisponde a un'equazione del sistema** e **ogni colonna, esclusa l'ultima, corrisponde a un'incognita**. L'ultima colonna contiene invece i termini noti.


L'obiettivo è **trasformare il sistema in uno equivalente** ma più semplice da risolvere.

$$
\text{matrice iniziale}
\longrightarrow
\text{matrice a gradini}
\longrightarrow
\text{eventuale matrice completamente ridotta}.
$$

Se $\Sigma'$ viene ottenuto da $\Sigma$ applicando un numero finito di [[Matrici#^119330|operazioni elementari]] alle righe della sua matrice completa, allora:$\boxed{S_\Sigma=S_{\Sigma'}}$ e quindi i due sistemi sono equivalenti, per questo motivo possiamo modificare la matrice.

---
## Metodo Gauss

Questo procedimento è alla base del **metodo di eliminazione di Gauss**:
1. si scrive la **matrice completa** del sistema;
2. si applicano **[[Matrici#^119330|operazioni elementari]] sulle righe**;
3. si porta la matrice in **[[Matrici#^5ed966|forma a gradini]]**;
4. si torna al sistema corrispondente;
5. si risolvono le incognite procedendo **dal basso verso l'alto**.

Se ci sono colonne senza pivot, le corrispondenti incognite sono **variabili libere**.

> [!example]- Metodo di Gauss
> Consideriamo il sistema:
> $$
> \begin{cases}
> x+y=3\\
> 2x+y=4
> \end{cases}
> $$
>
> Scriviamo la matrice completa:
> $$
> \left(
> \begin{array}{cc|c}
> 1&1&3\\
> 2&1&4
> \end{array}
> \right)
> $$
>
> Eliminiamo il $2$ sotto il primo pivot:
> $$
> \underline{a}_2\to \underline{a}_2-2\underline{a}_1
> $$
>
> Otteniamo:
> $$
> \left(
> \begin{array}{cc|c}
> 1&1&3\\
> 0&-1&-2
> \end{array}
> \right)
> $$
>
> La matrice è ora a gradini e corrisponde al sistema:
> $$
> \begin{cases}
> x+y=3\\
> -y=-2
> \end{cases}
> $$
>
> Dalla seconda equazione:
> $$
> y=2
> $$
>
> Sostituendo nella prima:
> $$
> x+2=3
> $$
> quindi:
> $$
> x=1
> $$
>
> Pertanto:
> $$
> \boxed{S=\{(1,2)\}}
> $$

>[!tip]- Dimostrazione che si ottiene sistema equivalente
>$\underline{x}=(x_{1},x_{2},\dots)$ e $e_{1}(x)=a_{1}^1$ e altre e sono i polinomi. quindi si può scrivere
>$$\Sigma=
>\begin{cases}
>e_{1}(\underline{x})=0 \\
>e_{2}(\underline{x})=0 \\ \\
>\dots \\
>e_{m}(\underline{x})=0 \\
>\end{cases}
>$$
>$$
>S=S_{1}\cap S_{2}\cap\dots S_{m}=S_{2}\cap S_{1}\cap\dots S_{m}
>$$
>poi operiamo su matrice tipo $a^2\to a^2+\lambda a^1$
>$$\Sigma=
>\begin{cases}
>e_{1}(\underline{x})=0 \\
>e_{2}(\underline{x})+\lambda_{1}(\underline{x})=0 \\ \\
>\dots \\
>e_{m}(\underline{x})=0 \\
>\end{cases}
>$$
>$$
>y\in S |Leftrightarrow e_{1}(\underline{y})=0,e_{2}(\underline{y})=0\dots
>$$
>quindi soluzione primo sistema anche del primo
>
>poi proviamolo per il prodotto $\beta \underline{\alpha}^\text{->beta^{-1}(beta undalpha)}=\underline{ \alpha_{2}}$ $b \underline{e_{2}}(\underline{y})=\beta_{0}=0$

Non scegliamo noi di quali $x$ trovare la soluzione è quella che è già decisa dal destino.

---
## Metodo Gauss-Jordan

Il metodo di Gauss-Jordan prosegue il metodo di Gauss fino a ottenere una matrice a gradini ridotta.

Dopo aver portato la matrice in forma a gradini:

1. si rendono i [[Matrici#^b83cec|pivot]] uguali a $1$;
2. si annullano anche gli elementi sopra ciascun pivot.

Si ottiene così una matrice in **[[Matrici#^f4edcd|forma a gradini ridotta]]**.

A differenza del metodo di Gauss, non è necessario tornare al sistema e procedere per sostituzione: le soluzioni si leggono direttamente dalla matrice finale.

> [!example]- Metodo di Gauss-Jordan
> Consideriamo il sistema:
> $$
> \begin{cases}
> y+2z=-1\\
> 2x-y-z=1 \\
> y+3z=-1
> \end{cases}
> $$
>
> Scriviamo la matrice completa:
> $$
> \left(
> \begin{array}{ccc|c}
> 0 & 1 & 2 & -1\\
> 2 & -1 & -1 & 1 \\
> 0 & 1 & 3 & -1
> \end{array}
> \right)
> $$
>
> Otteniamo dopo un paio di operazioni la matrice a gradini:
> $$
> \left(
> \begin{array}{ccc|c}
> 2 & -1 & -1 & 1\\
> 0 & 1 & 2  & -1\\
> 0 & 0 & 1 & 0
> \end{array}
> \right)
> $$
>
> La matrice ora va portata in forma ridotta, prima facendo $\underline{a}_{2}=a\underline{a}_{2}-3\underline{a}_{3}$ e $\underline{a}_{1}=\underline{a}_{1}+\underline{a}_{3}$:
> $$
> \left(
> \begin{array}{ccc|c}
> 2 & -1 & 0 & 1 \\
> 0 & 1 & 0 & -1 \\
> 0 & 0 & 1 & 0
> \end{array}
> \right)
> $$
> 
> Per ridurre completamente la matrice fai $\underline{a}_{1}=\underline{a}_{1}+\underline{a}2$ e $\underline{a}_{1}=\frac{1}{2}\underline{a}_{1}$:
> $$
> \left(
> \begin{array}{ccc|c}
> 1 & 0 & 0 & 0 \\
> 0 & 1 & 0 & -1 \\
> 0 & 0 & 1 & 0
> \end{array}
> \right)
> $$
>
>Quindi
>$$ \boxed{x=0\qquad y=-1 \qquad z=0} $$

---
## Teorema di Rouché-Capelli

>[!tip] Teorema di Rouché-Capelli
>Un sistema lineare $\Sigma$ è compatibile se e solo se
>$$
>\operatorname{rg}(A)=\operatorname{rg}(A|b).
>$$

Quindi:

$$
\boxed{
\Sigma \text{ compatibile}
\iff
\operatorname{rg}(A)=\operatorname{rg}(A|b)
}
$$

Se invece $\operatorname{rg}(A)\neq\operatorname{rg}(A|b)$ il sistema è incompatibile.

Se aggiungendo la colonna dei termini noti il rango aumenta, significa che compare una nuova condizione indipendente che non può essere soddisfatta dalle incognite. Quindi il sistema non ha soluzioni. Se invece il rango non cambia, il sistema è compatibile.

### Numero di soluzioni

Supponiamo che

$$
\operatorname{rg}(A)=\operatorname{rg}(A|b)=r.
$$

Allora il sistema è compatibile.

Bisogna confrontare $r$ con il numero $n$ delle incognite.

#### Caso $r=n$

Se

$$
r=n,
$$

il sistema ha **una sola soluzione**.

Quindi:

$$
\boxed{
\operatorname{rg}(A)=\operatorname{rg}(A|b)=n
\Rightarrow
\text{soluzione unica}
}
$$

#### Caso $r<n$

Se

$$
r<n,
$$

il sistema ha **infinite soluzioni**.

Il numero di variabili libere è

$$
n-r.
$$

Quindi:

$$
\boxed{
\operatorname{rg}(A)=\operatorname{rg}(A|b)<n
\Rightarrow
\text{infinite soluzioni}
}
$$

#### Caso ranghi diversi

Se

$$
\operatorname{rg}(A)\neq\operatorname{rg}(A|b),
$$

il sistema non ha soluzioni.

$$
\boxed{
\operatorname{rg}(A)\neq\operatorname{rg}(A|b)
\Rightarrow
\text{nessuna soluzione}
}
$$


### Schema riassuntivo

Sia

$$
r=\operatorname{rg}(A),
\qquad
r'=\operatorname{rg}(A|b).
$$

Allora:

$$
\begin{array}{c|c}
\text{Condizione} & \text{Conclusione}\\
\hline
r\neq r' & \text{nessuna soluzione}\\
r=r'=n & \text{una sola soluzione}\\
r=r'<n & \text{infinite soluzioni}
\end{array}
$$



>[!example] Esempio
>Consideriamo
>$$
>\begin{cases}
>x+y=2\\
>2x+2y=4
>\end{cases}
>$$
>
>La matrice dei coefficienti è
>$$
>A=
>\begin{pmatrix}
>1 & 1\\
>2 & 2
>\end{pmatrix}
>$$
>
>e la matrice completa è
>$$
>(A|b)=
>\begin{pmatrix}
>1 & 1 & 2\\
>2 & 2 & 4
>\end{pmatrix}.
>$$
>
>La seconda riga è multipla della prima, quindi
>$$
>\operatorname{rg}(A)=1
>$$
>e
>$$
>\operatorname{rg}(A|b)=1.
>$$
>
>I ranghi sono uguali, quindi il sistema è compatibile.
>
>Poiché
>$$
>1<2=n,
>$$
>il sistema ha infinite soluzioni.

