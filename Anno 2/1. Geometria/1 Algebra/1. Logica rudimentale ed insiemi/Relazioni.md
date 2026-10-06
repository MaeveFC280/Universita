---
Materia:
  - Geometria
  - Algebra Lineare
tags:
  - funzioni
Link risorse:
Libro:
Imparato: false
Ordine: 3
aliases:
---
## Relazioni su un insieme
Una **relazione su un insieme** $A$ è un sottoinsieme del prodotto cartesiano $A\times A$.

$$  
R\subseteq A\times A=A^2  
$$

---
## Relazione riflessiva
$R$ è **riflessiva** se

$$  
\forall x\in A,\quad (x,x)\in R  
$$

ovvero

$$  
xRx  
$$

per ogni $x\in A$.


---
## Relazione simmetrica
$R$ è **simmetrica** se

$$  
\forall x,y\in A,\quad  
(x,y)\in R\implies(y,x)\in R  
$$

ovvero

$$  
xRy\implies yRx  
$$


---
## Relazione transitiva
$R$ è **transitiva** se

$$  
\forall x,y,z\in A,  
\quad  
(x,y)\in R\land(y,z)\in R  
\implies(x,z)\in R  
$$

ovvero

$$  
xRy\land yRz\implies xRz  
$$

---
## Relazione di equivalenza
>[!info] Relazione di equivalenza
>Una relazione
>$$  R\subseteq A\times A  $$
>si dice **relazione di equivalenza** se e solo se è:
>- riflessiva;
>- simmetrica;
>- transitiva.

Una relazione di equivalenza serve a stabilire quando due elementi di un insieme possono essere considerati **equivalenti**, cioè appartenenti allo stesso gruppo secondo una determinata proprietà.

>[!example] Esempio
>Sia
>$$  A={1,3,5,7}  $$
e
>$$  R={(1,1),(3,3),(5,5),(7,7)}  $$
Questa è una relazione di equivalenza. Infatti è riflessiva, simmetrica e transitiva.
Se, invece, aggiungiamo soltanto $(7,3)$ otteniamo
>$$  R'=R\cup{(7,3)}  $$
>Questa relazione **non è di equivalenza**, perché non è simmetrica: infatti $(7,3)\in R'$  
ma $(3,7)\notin R'$ 

### Congruenza modulo
Sia

$$  
R\subseteq\mathbb Z\times\mathbb Z  
$$

e sia $m\in\mathbb N$.

Per $x,y\in\mathbb Z$ definiamo

$$  
xRy  
\iff  
\exists n\in\mathbb Z:  
x-y=mn  
$$

Equivalentemente,

$$  
m\mid(x-y)  
$$

Questa è la relazione di **congruenza modulo $m$**:

$$  
x\equiv y\pmod m  
$$

Essa è una relazione di equivalenza.


---
## Classe di equivalenza
>[!info] Definizione
Sia $R$ una relazione di equivalenza su $A$. Per ogni $a\in A$, si definisce **classe di equivalenza di $a$**
$$  [a]_R={x\in A\mid xRa}  $$
^classeEquivalenza

La classe di equivalenza di $a$ raccoglie tutti gli elementi di $A$ che sono equivalenti ad $a$.
Ogni elemento appartenente alla classe può essere scelto come **rappresentante** della classe.

In particolare,

$$  
a\in[a]_R  
$$

perché, essendo $R$ riflessiva,

$$  
aRa  
$$

## Proprietà
### Prima proprietà

Se

$$  
b\in[a]_R  
$$

allora

$$  
\boxed{[a]_R=[b]_R}  
$$

>[!tip] Dimostrazione
>Da
>$$  b\in[a]_R  $$
segue, per definizione,
>$$  bRa  $$
>Poiché $R$ è simmetrica,
>$$  aRb  $$
>Consideriamo ora
>$$  x\in[a]_R  $$
>Allora
>$$  xRa  $$
>e, poiché
>$$  aRb  $$
>per transitività otteniamo
>$$  xRb  $$
>quindi
>$$  
>x\in[b]_R  
>$$
>Pertanto
>$$  [a]_R\subseteq[b]_R  $$
>Analogamente, prendendo $y\in[b]_R$, si dimostra che
>$$  [b]_R\subseteq[a]_R  $$
>e quindi
>$$  \boxed{[a]_R=[b]_R}  $$


### Seconda proprietà

Date due classi di equivalenza,

$$  
\boxed{[a]_R=[b]_R}  
$$

oppure

$$  
\boxed{[a]_R\cap[b]_R=\varnothing}  
$$

In altre parole, **due classi di equivalenza o coincidono oppure sono disgiunte**.


>[!info]
Supponiamo che
$$  [a]_R\cap[b]_R\neq\varnothing  $$
Allora esiste$$  x\in[a]_R\cap[b]_R  $$
quindi
$$  x\in[a]_R  \qquad\text{e}\qquad  x\in[b]_R  $$
Da cui
$$  xRa  \qquad\text{e}\qquad  xRb  $$
Per simmetria,
$$  aRx  $$
e quindi, per transitività,
$$  aRb  $$
Dalla prima proprietà segue
$$  [a]_R=[b]_R  $$
Pertanto:
$$  \boxed{  [a]_R\cap[b]_R\neq\varnothing  \implies  [a]_R=[b]_R  }  $$


---
## Partizione
> [!info] Partizione
>Sia $A$ un insieme e $P(A)$ il suo insieme delle parti. Si dice **partizione** di $A$ un insieme $\text{P}\underline{\subset}P(A)$ (cioè un insieme dei sottoinsiemi di $A$) tale da soddisfare tali condizioni:
>1. Ogni elemento della partizione è un insieme non vuoto: $\forall B\in P:B\not=0$ 
>2. Gli elementi della partizione sono a due a due disgiunti: $\forall B,C\in P:t\ \ \text{se}\ \  B\not=C\Rightarrow B\cap C=\oslash$
>3. L'unione di tutti gli elementi della partizione è uguale all'insieme di partenza: $\bigcup_{B \in P} B = A$

Un ricoprimento è una **partizione** se inoltre gli insiemi sono a due a due disgiunti:

$$  
\forall i,j\in I,\quad  
i\neq j\implies X_i\cap X_j=\varnothing  
$$

Una partizione divide quindi $A$ in sottoinsiemi **non sovrapposti**.

---
## Relazioni di equivalenza e partizioni

Le classi di equivalenza di una relazione di equivalenza costituiscono una **partizione di $A$**.

Infatti:

1. ogni elemento $a\in A$ appartiene alla propria classe $[a]_R$;
2. due classi o coincidono oppure sono disgiunte.

Quindi

$$  
A=\bigcup_{a\in A}[a]_R  
$$

eliminando naturalmente le classi ripetute.

---
## Insieme quoziente

L'insieme formato da tutte le classi di equivalenza di $A$ rispetto a $R$ si chiama **insieme quoziente** e si indica con

$$  
\boxed{\frac{A}{R}}  
$$

oppure

$$  
A/R  
$$

Formalmente:

$$  
A/R={[a]_R\mid a\in A}  
$$



### Esempio costruzione di $\mathbb Q$

Consideriamo

$$  
A=\mathbb Z\times(\mathbb Z\setminus{0})  
$$

Un elemento di $A$ è quindi una coppia

$$  
(m,n)  
$$

con

$$  
m\in\mathbb Z,\qquad n\in\mathbb Z\setminus{0}  
$$

Definiamo la relazione

$$  
(m,n)R(m',n')  
$$

se e solo se

$$  
mn'=m'n  
$$

Per esempio,

$$  
(1,2)R(2,4)  
$$

perché

$$  
1\cdot4=2\cdot2  
$$

Le due coppie rappresentano infatti lo stesso numero razionale:

$$  
\frac12=\frac24  
$$

La relazione è una relazione di equivalenza.

L'insieme quoziente

$$  
\frac{\mathbb Z\times(\mathbb Z\setminus{0})}{R}  
$$

permette di costruire l'insieme dei numeri razionali:

$$  
\boxed{  
\mathbb Q=  
\frac{\mathbb Z\times(\mathbb Z\setminus{0})}{R}  
}  
$$



### Esempio geometrico: vettori

$$  
\Sigma=  
{P\mid \text{punto dello spazio della geometria elementare}}  
$$

Consideriamo l'insieme dei segmenti orientati

$$  
V={(P,Q)\mid P,Q\in\Sigma}  
$$

che possiamo rappresentare come

$$  
P\longrightarrow Q  
$$

Due segmenti orientati vengono considerati equivalenti quando rappresentano lo **stesso spostamento**, cioè hanno stessa direzione, stesso verso e stessa lunghezza.

Possiamo quindi definire una relazione di equivalenza su $V$.

Le relative classi di equivalenza sono ciò che chiamiamo **vettori liberi** o **vettori geometrici**.

In pratica, cambiando il punto di applicazione del segmento orientato non cambia il vettore, purché direzione, verso e lunghezza rimangano gli stessi.


