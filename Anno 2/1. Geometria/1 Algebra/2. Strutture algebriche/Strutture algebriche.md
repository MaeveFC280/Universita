---
Materia:
  - Algebra Lineare
  - Geometria
tags:
Link risorse:
Libro:
Imparato: false
Ordine: 5
aliases:
---
## Struttura algebrica
>[!info] Definizione
Una **struttura algebrica** è un insieme dotato di una o più operazioni che soddisfano determinate proprietà.

Ovvero una [[n-upla]] $n\in\mathbb N,\ \ n \underline>2$ costituita da un insieme di operazioni definita su essi



---
## Gruppo

>[!info] Definizione
>La struttura algebrica $(A,\perp)$ è un **gruppo** se possiede le seguenti proprietà:
>- $\perp$ è associativa
>- $(A,\perp)$ ammette un elemento neutro
>- Ogni elemento $x\in A$ è invertibile
>
>Se il gruppo possiede anche la proprietà commutativa allora esso è un **gruppo abeliano**.

^0826fd

La cosa importante è saper riconoscere una struttura **dalle proprietà delle sue operazioni**.
>[!example]
>$(\mathbb{Z}, +)$ è un gruppo abeliano; 0 ne è l'elemento neutro e l'opposto di $z$ è $-z$.

---
## Anello
>[!info] Definizione
>Un **anello** è un insieme $A$ dotato di due operazioni: somma e prodotto ($+$ e $\cdot$) che soddisfano le seguenti proprietà:
>- $(A,+)$ è un gruppo abeliano;
>- il prodotto gode di proprietà associativa
>- Il prodotto è distributivo rispetto alla somma:
>$$  a(b+c)=ab+ac  \qquad (a+b)c=ac+bc$$

Un anello si dice **unitario** se la moltiplicazione possiede un elemento neutro $\exists 1\in A:\forall a\in A$ tale che $1a=a1=a$

Un anello si dice **commutativo** se la moltiplicazione è commutativa $ab=ba$ per ogni $a,b\in A$.

---
## Campo
>[!info] Definizione
>Un **campo** è un insieme $A$ dotato di due operazioni: somma e prodotto ($+$ e $\cdot$) che soddisfano le seguenti proprietà:
>- $(A,+,\cdot)$ è un anello unitario e commutativo;
>- ogni elemento diverso da 0 possiede un inverso rispetto al prodotto (0 escluso):
>$$\forall a\in A\setminus{0},  \quad  \exists a^{-1}\in A:aa^{-1}=a^{-1}a=1$$

^1ed1df

