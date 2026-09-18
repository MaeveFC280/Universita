---
Materia: Geometria
tags:
  - Insiemi
Link risorse:
Libro: "Casali, Gagliardi, Grasselli: Geometria (Esculapio)"
Imparato: false
Ordine: 0
aliases:
---
L'[[Anno 1/2 Algebra/Logica rudimentale ed insiemi/Insiemi|insieme]] come definito in algebra è una collezione di oggetti.

>![EXAMPLE]
>$\mathbb{N}=\{1,2,3,\dots\}=\{x|x\ \text{è un numero naturale}\}$
>$\mathbb{Z}=\{0,\+1,-1,\dots}=\{x|x\ \text{è un numero relativo}\}$
>$\mathbb{Q}=\left\{ \frac{m}{n}|m \in \mathbb{Z}, n \in \mathbb{N} \right\}$
>$\mathbb{N}=\{1,2,3,\dots\}=\{x|x\ \text{è un numero naturale}\}$

## Implicazione
$$
P(x)\Rightarrow Q(x)  = \not{Q(x)}\Rightarrow \not{P(x)}
$$
## Proprietà
$$
a\in A\ A=\{1,2,5\}\ 5\in A\Rightarrow\{5\}\underline{\subset} A
$$

**Singleton**

Singleton di 5 appartiene all'insieme delle parti

## Paradosso
$$
S=\{x|x\not\in x\}
$$
$$
S\in S\Rightarrow S\not\in S
$$
$$
S\not \in S\Rightarrow S\in S
$$
Se appartiene per proprietà non appartiene ma se non appartiene allora deve appartenere.

## Altro
$$
A \underline{\subset} B\Leftrightarrow\text{ogni elemento di A è anche elemento di B}
$$

$$
A=B\Leftrightarrow A \underline{\subset} B\Leftrightarrow\text{e} B \underline{\subset} A
$$

## Unione e intersezione
$$
A \cup B=\{x|x \in _{\text{opp }} x\in B\}
$$
$$
A\cap B=\{x|x\in A \text{ e } x\in B\}
$$

## Differenza
$$
A-B=\{x|x\in A \\text{ e } x\not\in B\}
$$
## Complemento
$$
B \underline{<} X, X-B=C_{x}(B) \text{ Complemento}
$$

## coppie vettiruaki
$$
\{3,5\}=\{5,3\}
$$
$$
\{3,3\}=\{3\}
$$

ordine e doppioni non c'è negli insiemi
$$
(3,5)\not=(5,3)
$$

$$
(3,5)\rightarrow\{3,\{3,5\}\}=\{3,\{5,3\}\}
$$
$$
(5,3)\rightarrow\{5,\{5,3\}\}=\{3,\{5,3\}\}
$$
nelle coppie gli elementi si possono ripetere
 terne quaterne...
$$
 \{3,\{3,5\},\{3,5,7\}\}\rightarrow (3,5,7)
$$

A,B non vuoti 
$$
A\times B=\{(a,b)|a\in A,b\in B\}
$$

$$
A=\{x,y,z\}\ B=\{1,2,3\}
$$
$$
A\times B=\{(x,1),(x,2),(x,3),(y,1),(y,2),\dots\}
$$
**definizione sottoinsieme**
## Relazioni
$R=\{(x,3),(y,2)\}$
$x\mathbb{R}3\ \ y\not R 3$
Se a,b non vuoti e $R \underline{\subset}A\times B\Rightarrow R^{-1}=\{(b,a)|a \in R\} \underline{\subset} B \times A$ si dice relazione inversa di R
## applicazioni
una applicazione da a in b è una relazione tra a e b tale che ogni a in a esiste un solo b in b coppia a e b in funzione

non una applicazione:  $A\times B=\{(x,1),(x,2),(x,3),(y,1),(y,2),\dots\}$

$$
f=\{(x,7),(y,5),(z,3)\}
$$
$f(a)=b$ immagine di a mediante f
$f:A\rightarrow B$ dominio e codominio

$$
f(x)=\{n \in B|\exists a \in X: f(a)=b\}=\{f(a)|r \in X\}
$$
## sottoinsieme codominio
$$
y \underline{\subset}B\ \ f^{-1}(y)=\{x \in A|f(a)\in y\}
$$
controiimagine o immagini inversa di y mediante f


freccia storta: relazione sul ingolo elemento

## comporre applicazioni