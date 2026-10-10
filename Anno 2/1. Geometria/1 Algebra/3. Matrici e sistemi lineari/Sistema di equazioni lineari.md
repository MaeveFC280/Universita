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
## Sistema lineare
>[!info] Definizione
>Dato un [[Strutture algebriche#^1ed1df|campo]] $(K,+,\cdot)$ e due numeri naturali $m,n\geq1$, un **sistema lineare** di $m$ equazioni in $n$ incognite è una **m-upla di equazioni lineari** su $K$.
>Un sistema lineare generico si scrive:
>$$
>\Sigma:\begin{cases}
>a_{11}x_1+a_{12}x_2+\dots+a_{1n}x_n=b_1\\
>a_{21}x_1+a_{22}x_2+\dots+a_{2n}x_n=b_2\\
>\vdots\\
>a_{m1}x_1+a_{m2}x_2+\dots+a_{mn}x_n=b_m
>\end{cases}
>$$
>dove:
>- $x_1,\dots,x_n$ sono le **incognite**;
>- $a_{ij}\in K$ sono i **coefficienti**;
>- $b_1,\dots,b_m\in K$ sono i **termini noti**.
>Una **soluzione** del sistema $\Sigma$ è una [[n-upla]] $(s_1,\dots,s_n)\in K^n$ che, sostituita alle incognite, soddisfa contemporaneamente tutte le $m$ equazioni.
>L'insieme di tutte le soluzioni è indicato con $S_\Sigma\subseteq K^n$.

- Un sistema $\Sigma$ è **compatibile** quando ammette almeno una soluzione, cioè $S_\Sigma\neq\varnothing$.
- Un sistema è **incompatibile** quando non ammette soluzioni, cioè $S_\Sigma=\varnothing$.
- Due sistemi $\Sigma_1$ e $\Sigma_2$, nelle stesse incognite e sullo stesso campo, sono **equivalenti** quando hanno lo stesso insieme delle soluzioni: $S_{\Sigma_1}=S_{\Sigma_2}$.
- Un sistema è **omogeneo** quando tutti i termini noti sono nulli, cioè $b_1=\dots=b_m=0$. Un sistema omogeneo è sempre compatibile, perché ammette almeno la soluzione nulla $(0,\dots,0)$.

>[!example]- Esempio
>Consideriamo il sistema con $m=1$, $n=4$ e $K=\mathbb{Q}$:
>$$
>2x_2-x_3+3x_4=1
>$$
>Abbiamo una sola equazione in quattro incognite. Per descrivere tutte le soluzioni possiamo scegliere liberamente tre incognite e ricavare la quarta.
>**Primo metodo: ricaviamo $x_3$.**
>$$
>x_3=2x_2+3x_4-1
>$$
>Assegniamo valori arbitrari:
>$$
>x_1=s,\quad x_2=t,\quad x_4=u
>$$
>con $s,t,u\in\mathbb Q$. Di conseguenza:
>$$
>x_3=2t+3u-1
>$$
>L'insieme delle soluzioni è:
>$$
>\boxed{S_\Sigma=\{(s,t,2t+3u-1,u)\mid s,t,u\in\mathbb Q\}}
>$$
>**Secondo metodo: ricaviamo $x_2$.**
>Partiamo dalla stessa equazione:
>$$
>2x_2=x_3-3x_4+1
>$$
>quindi:
>$$
>x_2=\frac{x_3-3x_4+1}{2}
>$$
>Questa volta scegliamo liberamente $x_1=s$, $x_3=t$ e $x_4=u$, ottenendo:
>$$
>\boxed{S_\Sigma=\left\{\left(s,\frac{t-3u+1}{2},t,u\right)\mid s,t,u\in\mathbb Q\right\}}
>$$
>Le due rappresentazioni descrivono **lo stesso insieme di soluzioni**: abbiamo soltanto scelto incognite libere differenti.

---
## Matrice associata a un sistema
Consideriamo il sistema lineare:
$$
\Sigma:\begin{cases}
a_{11}x_1+\dots+a_{1n}x_n=b_1\\
a_{21}x_1+\dots+a_{2n}x_n=b_2\\
\vdots\\
a_{m1}x_1+\dots+a_{mn}x_n=b_m
\end{cases}
$$


I coefficienti delle incognite possono essere raccolti nella **[[Matrici|matrice dei coefficienti]]**:
$$
A=\begin{pmatrix}
a_{11}&a_{12}&\dots&a_{1n}\\
a_{21}&a_{22}&\dots&a_{2n}\\
\vdots&\vdots&&\vdots\\
a_{m1}&a_{m2}&\dots&a_{mn}
\end{pmatrix}\in M_{m\times n}(K)
$$

Se aggiungiamo anche i termini noti otteniamo la **[[Matrici|matrice]] completa** del sistema:

$$
C=(A|b)=
\left(\begin{array}{cccc|c}
a_{11}&a_{12}&\dots&a_{1n}&b_1\\
a_{21}&a_{22}&\dots&a_{2n}&b_2\\
\vdots&\vdots&&\vdots&\vdots\\
a_{m1}&a_{m2}&\dots&a_{mn}&b_m
\end{array}\right)
$$


Quindi:
- ogni **riga** della matrice completa corrisponde a un'equazione;
- ogni **colonna** di $A$ corrisponde a un'incognita;
- **l'ultima colonna** contiene i termini noti.




Indichiamo con:
$$
x=\begin{pmatrix}x_1\\\vdots\\x_n\end{pmatrix},
\qquad
b=\begin{pmatrix}b_1\\\vdots\\b_m\end{pmatrix}
$$
Allora il sistema può essere scritto nella forma compatta:
$$
\boxed{Ax=b}
$$
dove il prodotto è il [[Prodotto tra matrici|prodotto righe per colonne]].


L'obiettivo è **trasformare il sistema in uno equivalente** ma più semplice da risolvere.

$$
\text{matrice iniziale}
\longrightarrow
\text{matrice a gradini}
\longrightarrow
\text{eventuale matrice completamente ridotta}.
$$

Se $\Sigma'$ viene ottenuto da $\Sigma$ applicando un numero finito di [[Matrici#^119330|operazioni elementari]] alle righe della sua matrice completa, allora:$\boxed{S_\Sigma=S_{\Sigma'}}$ e quindi i due sistemi sono equivalenti, per questo motivo possiamo modificare la matrice.


### Metodo Gauss

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


>[!tip] Dimostrazione
>Vogliamo dimostrare che le operazioni elementari sulle righe conservano l'insieme delle soluzioni del sistema.
>**1. Scriviamo il sistema usando delle funzioni**
>Indichiamo con $x=(x_1,\dots,x_n)\in K^n$ il vettore delle incognite e definiamo:
>$$
>e_i(x)=a_{i1}x_1+\dots+a_{in}x_n-b_i
>$$
>Possiamo quindi riscrivere il sistema come:
>$$
>\Sigma:\begin{cases}
>e_1(x)=0\\
>e_2(x)=0\\
>\vdots\\
>e_m(x)=0
>\end{cases}
>$$
>Una n-upla $y\in K^n$ è soluzione del sistema se e solo se soddisfa tutte le equazioni:
>$$
>y\in S_\Sigma\iff e_1(y)=e_2(y)=\dots=e_m(y)=0
>$$
>**2. Scambio di due righe**
>Scambiare due righe significa cambiare l'ordine delle equazioni.
>Se $S_i=\{x\in K^n\mid e_i(x)=0\}$, allora:
>$$
>S_\Sigma=S_1\cap S_2\cap\dots\cap S_m
>$$
>Poiché l'intersezione è commutativa, scambiare due insiemi non modifica il risultato. Quindi lo scambio di due righe conserva le soluzioni.
>**3. Moltiplicazione di una riga per uno scalare non nullo**
>Consideriamo l'operazione:
>$$
>R_i\to\beta R_i,\qquad\beta\neq0
>$$
>La corrispondente equazione diventa:
>$$
>\beta e_i(x)=0
>$$
>Poiché $K$ è un campo e $\beta\neq0$, esiste $\beta^{-1}$ e quindi:
>$$
>\beta e_i(x)=0\iff e_i(x)=0
>$$
>Le due equazioni hanno esattamente le stesse soluzioni.
>**4. Somma a una riga di un multiplo di un'altra**
>Consideriamo l'operazione:
>$$
>R_i\to R_i+\lambda R_j,\qquad i\neq j
>$$
>La nuova equazione è:
>$$
>e_i(x)+\lambda e_j(x)=0
>$$
>La $j$-esima equazione rimane invariata: $e_j(x)=0$.
>Se $y$ è soluzione del sistema originale, allora:
>$$
>e_i(y)=0,\qquad e_j(y)=0
>$$
>Di conseguenza:
>$$
>e_i(y)+\lambda e_j(y)=0+\lambda\cdot0=0
>$$
>Quindi $y$ è soluzione anche del sistema trasformato.
>Viceversa, se $y$ è soluzione del sistema trasformato:
>$$
>e_i(y)+\lambda e_j(y)=0,\qquad e_j(y)=0
>$$
>Sostituendo $e_j(y)=0$ otteniamo:
>$$
>e_i(y)=0
>$$
>Quindi $y$ soddisfa anche il sistema originale.
>**Conclusione**
>Ogni operazione elementare è reversibile e conserva l'insieme delle soluzioni. Di conseguenza, anche una successione finita di tali operazioni produce un sistema equivalente:
>$$
>\boxed{S_\Sigma=S_{\Sigma'}}
>$$


Non scegliamo noi di quali $x$ trovare la soluzione è quella che è già decisa dal destino.


### Metodo Gauss-Jordan

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


