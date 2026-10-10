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
## Prodotto scalare numerico
Sia $(K,+,\cdot)$ un [[Strutture algebriche#^1ed1df|campo]]. Consideriamo due vettori di $K^n$:
$$
u=(a_1,\ldots,a_n),\qquad v=(b_1,\ldots,b_n).
$$
> [!info] Definizione
> Il **prodotto scalare numerico** (o *standard*, *canonico*) è l'applicazione
> $$
> \cdot:K^n\times K^n\to K
> $$
> definita da:
> $$
> \boxed{u\cdot v=a_1b_1+\dots+a_nb_n=\sum_{i=1}^{n}a_ib_i.}
> $$
> Si moltiplicano le componenti corrispondenti dei due vettori e si sommano i prodotti. Il risultato è uno **scalare** di $K$, non un vettore.


> [!example]- Esempio
> In $\mathbb R^3$ consideriamo $u=(3,-2,\pi)$ e $v=(4,1,2)$. Allora:
> $$
> u\cdot v=3\cdot4+(-2)\cdot1+\pi\cdot2=\boxed{10+2\pi}.
> $$

### Proprietà del prodotto scalare
Per ogni $u,v,w\in K^n$ e $\lambda\in K$ valgono:
1. **Simmetria:** $u\cdot v=v\cdot u$.
2. **Distributività:** $u\cdot(v+w)=u\cdot v+u\cdot w$.
3. **Compatibilità con gli scalari:** $(\lambda u)\cdot v=\lambda(u\cdot v)=u\cdot(\lambda v)$.
Per $K=\mathbb R$ vale inoltre la **positività**:
$$
u\cdot u\geq0,\qquad u\cdot u=0\iff u=\underline 0.
$$
> [!note] Osservazione
> La positività è enunciata qui per $\mathbb R^n$: non va attribuita a un campo $K$ qualsiasi, nel quale la relazione d'ordine $\geq$ potrebbe non essere definita.


---
## Matrici conformabili
Siano:
$$
A\in M_{m\times n}(K),\qquad B\in M_{n\times p}(K).
$$
> [!info] Definizione
> La coppia $(A,B)$ è detta **conformabile** per il prodotto righe per colonne quando il **numero delle colonne di $A$** è uguale al **numero delle righe di $B$**.
> Il prodotto $AB$ è allora definito e ha dimensione $m\times p$:
> $$
> \boxed{\underbrace{A}_{m\times n}\underbrace{B}_{n\times p}=\underbrace{AB}_{m\times p}.}
> $$
La conformabilità dipende dall'**ordine** delle matrici: se $AB$ è definito, non è detto che lo sia anche $BA$.

## Prodotto righe per colonne
Le [[Matrici#Righe e colonne come vettori|righe e colonne]] possono essere considerate come vettori numerici. Indichiamo con:
- $\underline{a}^{\,i}=(a_1^i,\ldots,a_n^i)\in K^n$ la **riga $i$-esima** di $A$;
- $\underline{b}_j=(b_j^1,\ldots,b_j^n)\in K^n$ la **colonna $j$-esima** di $B$, identificata con le sue $n$ componenti.
> [!info] Definizione
> Il **prodotto righe per colonne** è la matrice $C=AB\in M_{m\times p}(K)$ il cui elemento nella riga $i$ e nella colonna $j$ è il prodotto scalare tra la riga $i$-esima di $A$ e la colonna $j$-esima di $B$:
> $$
> \boxed{c_j^i=\underline{a}^{\,i}\cdot\underline{b}_j=\sum_{k=1}^{n}a_k^i b_j^k.}
> $$
> In particolare:
> $$
> AB=\begin{pmatrix}
> \underline{a}^{\,1}\cdot\underline{b}_1&\cdots&\underline{a}^{\,1}\cdot\underline{b}_p\\
> \vdots&&\vdots\\
> \underline{a}^{\,m}\cdot\underline{b}_1&\cdots&\underline{a}^{\,m}\cdot\underline{b}_p
> \end{pmatrix}.
> $$
> Ogni elemento del risultato si ottiene incrociando **una riga della prima matrice** con **una colonna della seconda**.

> [!example]- Esempio: prodotto di una matrice $3\times2$ per una $2\times4$
> Consideriamo le matrici del tuo appunto:
> $$
> A=\begin{pmatrix}2&1\\0&3\\-4&6\end{pmatrix}\in M_{3\times2}(\mathbb R),\qquad
> B=\begin{pmatrix}5&-7&0&9\\2&3&1&0\end{pmatrix}\in M_{2\times4}(\mathbb R).
> $$
> Poiché $A$ ha $2$ colonne e $B$ ha $2$ righe, la coppia $(A,B)$ è conformabile e $AB$ avrà $3$ righe e $4$ colonne.
> Per ottenere il primo elemento della prima riga:
> $$
> c_1^1=(2,1)\cdot(5,2)=2\cdot5+1\cdot2=12.
> $$
> Per ottenere il secondo elemento della prima riga:
> $$
> c_2^1=(2,1)\cdot(-7,3)=2(-7)+1\cdot3=-11.
> $$
> Ripetiamo il procedimento per ogni coppia riga-colonna:
> $$
> AB=\begin{pmatrix}
> 2\cdot5+1\cdot2&2(-7)+1\cdot3&2\cdot0+1\cdot1&2\cdot9+1\cdot0\\
> 0\cdot5+3\cdot2&0(-7)+3\cdot3&0\cdot0+3\cdot1&0\cdot9+3\cdot0\\
> (-4)5+6\cdot2&(-4)(-7)+6\cdot3&(-4)\cdot0+6\cdot1&(-4)\cdot9+6\cdot0
> \end{pmatrix}
> $$
> quindi:
> $$
> \boxed{AB=\begin{pmatrix}
> 12&-11&1&18\\
> 6&9&3&0\\
> -8&46&6&-36
> \end{pmatrix}.}
> $$
> Invece $BA$ **non è definito**: $B$ ha $4$ colonne, mentre $A$ ha $3$ righe.

---
## Proprietà del prodotto righe per colonne
Le proprietà seguenti valgono quando le dimensioni delle matrici permettono di eseguire i prodotti e le somme indicati.
1. **Associatività.** Se $A\in M_{m\times n}(K)$, $B\in M_{n\times p}(K)$ e $C\in M_{p\times q}(K)$, allora
   $$
   \boxed{(AB)C=A(BC).}
   $$
2. **Distributività rispetto alla somma (a sinistra).** Se $A,B\in M_{m\times n}(K)$ e $C\in M_{n\times p}(K)$, allora
   $$
   \boxed{(A+B)C=AC+BC.}
   $$
3. **Distributività rispetto alla somma (a destra).** Se $A\in M_{m\times n}(K)$ e $B,C\in M_{n\times p}(K)$, allora
   $$
   \boxed{A(B+C)=AB+AC.}
   $$
4. **Compatibilità con la moltiplicazione per scalare.** Se $A\in M_{m\times n}(K)$, $B\in M_{n\times p}(K)$ e $\lambda\in K$, allora
   $$
   \boxed{(\lambda A)B=\lambda(AB)=A(\lambda B).}
   $$

### Il prodotto non è commutativo
Anche quando $AB$ e $BA$ sono entrambi definiti, in generale **$AB\neq BA$**.
> [!example]- Controesempio
> Siano
> $$
> A=\begin{pmatrix}0&1\\0&0\end{pmatrix},\qquad
> B=\begin{pmatrix}0&0\\1&0\end{pmatrix}.
> $$
> Si ottiene:
> $$
> AB=\begin{pmatrix}1&0\\0&0\end{pmatrix},\qquad
> BA=\begin{pmatrix}0&0\\0&1\end{pmatrix}.
> $$
> Dunque $AB\neq BA$.

---
## Matrici quadrate, matrice identità e invertibilità
Se $A\in M_{n\times n}(K)$, la matrice è detta **quadrata di ordine $n$** e si scrive anche $A\in M_n(K)$. In questo caso il prodotto di due matrici di ordine $n$ è sempre definito e restituisce una matrice di ordine $n$.

> [!info] Matrice identità
> La **matrice identità** (o *unità*) di ordine $n$ è la matrice quadrata $I_n$ che ha $1$ sulla diagonale principale e $0$ altrove:
> $$
> I_n=\begin{pmatrix}1&0&\cdots&0\\0&1&\cdots&0\\\vdots&\vdots&\ddots&\vdots\\0&0&\cdots&1\end{pmatrix}.
> $$
> Per ogni $A\in M_n(K)$:
> $$
> \boxed{AI_n=I_nA=A.}
> $$

> [!info] Matrice invertibile
> Una matrice $A\in M_n(K)$ si dice **invertibile** se esiste $B\in M_n(K)$ tale che:
> $$
> AB=BA=I_n.
> $$
> La matrice $B$ è unica e si indica con $A^{-1}$; quindi:
> $$
> \boxed{AA^{-1}=A^{-1}A=I_n.}
> $$
> **Non tutte le matrici quadrate sono invertibili.**

> [!example]- Esempio: matrice quadrata non invertibile
> Consideriamo
> $$
> A=\begin{pmatrix}1&0\\0&0\end{pmatrix}.
> $$
> Per qualsiasi matrice $B$ di ordine $2$, l'ultima riga di $AB$ è nulla; pertanto $AB$ non può essere $I_2$. Quindi $A$ non è invertibile.

### Gruppo generale lineare
L'insieme delle matrici invertibili di ordine $n$ su $K$ si indica con:
$$
\boxed{GL_n(K)=\{A\in M_n(K)\mid A\text{ è invertibile}\}.}
$$
Rispetto al prodotto righe per colonne, $(GL_n(K),\cdot)$ è un **gruppo**, detto **gruppo generale lineare** di ordine $n$ su $K$.
L'insieme di *tutte* le matrici quadrate $M_n(K)$, invece, **non** è un gruppo rispetto al prodotto: contiene matrici non invertibili.
L'insieme $M_n(K)$, con la somma e il prodotto righe per colonne, è un **anello unitario** (in generale non commutativo).

