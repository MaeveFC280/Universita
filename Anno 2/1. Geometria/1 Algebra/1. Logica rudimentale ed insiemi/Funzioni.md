---
Materia:
  - Algebra Lineare
  - Geometria
  - Analisi
tags:
  - funzioni
Link risorse:
Libro:
Imparato: true
Ordine: 2
aliases:
---
>[!info] Funzione
>Dati due insiemi $A$ a un insieme $B$ una funzione/applicazione è una [[Relazioni|relazione]] $f\subseteq A\times B$  tale che $\forall a\in A,\ \exists! b\in B \text{ tale che } (a,b)\in f$  dove $\exists!$ significa **esiste ed è unico**.
>Si scrive $f\to B$ e, se all'elemento $a\in A$ viene associato $b\in B$, $f(a)=b$  

---
## Composizione di funzioni
Siano $A,B,C\neq\varnothing$ e siano

$$  
f:A\to B  
$$

$$  
g:B\to C  
$$

La **composizione** di $f$ e $g$ è la funzione
$$  
g\circ f:A\to C  
$$

definita da
$$  
(g\circ f)(a)=g(f(a))  
$$
La composizione di funzioni è **associativa**:

$$  
h\circ(g\circ f)=(h\circ g)\circ f  
$$

quando le composizioni sono definite.

---
## Tipi di funzioni
### Iniettiva
Ad elementi distinti di $A$ corrispondono elementi distinti di $B$
$$
x_{1}\ne x_{2}\implies f(x_{1})\ne f(x_{2})
$$
Ogni retta parallela all'asse delle $x$ incontra il grafico in un solo punto o nessuno.
![[Funzioni-1790522978215.webp|381x294]]![[Funzioni-1790522438510.webp|262x262]]



### Suriettiva
Il codominio corrisponde con l'insieme $B$. Ogni elemento di $B$ ha almeno un elemento in $A$.
$$
\forall x_{1}\in A,\exists x_{2}\in B\implies f(x_{1})=x_{2}
$$
Ogni retta parallela all'asse delle $x$ incontra il grafico almeno un punto.
![[Funzioni-1790522897994.webp|402x253]]![[Funzioni-1790522804003.webp|246x246]]


### Biettiva
Agli elementi distinti di $A$ corrispondono altrettanti elementi distinti di $B$ e il codominio corrisponde con l'insieme $B$. È sia **iniettiva** sia **suriettiva**.
$$
\forall x_{1}\in A,\exists! x_{2}\in B\implies f(x_{1})=x_{2}
$$
Ogni retta parallela all'asse delle $x$ incontra il grafico in un solo
punto.

![[Drawing 2026-09-24 14.07.58.excalidraw]]
### Crescenti e decrescenti
Sia $f(x)$ una funzione di dominio $D$, diciamo che la funzione è
- **Monotona crescente in senso stretto** se due valori $x_{1},x_{2}$ tali che $x_{1}<x_{2}$ allora $f(x_{1})<f(x_{2})$
- **Monotona crescente in senso lato** se due valori $x_{1},x_{2}$ tali che $x_{1}<x_{2}$ allora $f(x_{1})\underline<f(x_{2})$
- **Monotona decrescente in senso stretto** se due valori $x_{1},x_{2}$ tali che $x_{1}<x_{2}$ allora $f(x_{1})>f(x_{2})$
- **Monotona decrescente in senso lato** se due valori $x_{1},x_{2}$ tali che $x_{1}<x_{2}$ allora $f(x_{1})\underline>f(x_{2})$
![[Funzioni-1790523395983.webp|502x222]]

---
## Funzione identità
La funzione identità su $A$ è

$$  
id_A\to A  
$$

definita da

$$  
id_A(a)=a  
\qquad \forall a\in A  
$$
---
## Funzione inversa
Una funzione

$$  
f\to B  
$$

si dice **invertibile** se esiste una funzione

$$  
f^{-1}\to A  
$$

tale che

$$  
f^{-1}\circ f=id_A  
$$

e
$$  
f\circ f^{-1}=id_B  
$$

La funzione $f^{-1}$ viene detta **funzione inversa** di $f$.

Vale la proprietà fondamentale:

$$  
\boxed{f \text{ è invertibile }\iff f\text{ è biiettiva}}  
$$

cioè $f$ deve essere contemporaneamente **iniettiva e suriettiva**.
$$
\exists g:B\to A\ \ g\circ f:A\to A\ \ a\to(g\circ f)(a)=g(f(a))=a
$$
$$
g\circ f:B\to B\ \ b\to f(g(b))=b
$$

>[!EXAMPLE] Esempio
>Siano $A=\{x,y,z\}$ $B=\{a,b,c\}$ e $f\to B$ con, ad esempio,
>$$  x\mapsto a,\qquad y\mapsto b,\qquad z\mapsto c  $$
>Allora
>$$  f^{-1}\to A  $$
>e
>$$  a\mapsto x,\qquad b\mapsto y,\qquad c\mapsto z  $$






