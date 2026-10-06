---
Materia:
  - Analisi
tags:
  - Insiemi
  - funzioni
Link risorse:
Libro:
Imparato: false
Ordine: 3
aliases:
---
## Massimo e minimo
>[!info] Definizione di Massimo
>$A \underline{\subset}\mathbb R,\ A\ne\oslash$ Si dice che $M\in\mathbb R$ è in massimo di $A$ ($M=\text{max}A$) se $M \underline{>}a\ \ \forall a\in A,\ m\in A$.

>[!info] Definizione di Minimo
>$A \underline{\subset}\mathbb R,\ A\ne\oslash$ Si dice che $m\in\mathbb R$ è in massimo di $A$ ($m=\text{min}A$) se $m \underline{<}a\ \ \forall a\in A,\ m\in A$.


>[!example] Esempio con i  numeri naturali
>$A=\mathbb N=\{0,1,2,3,\dots\}$
>- Minimo: $0$
>- Massimo: $\text{non esiste}$

>[!example] Esempio con insieme di numeri reali
>$A=\{x\in \mathbb R:\ 3x+2<-8\}$
>Risolviamo primo l'equazione: $3x<-10\to x<-\frac{10}{3}$
>$A=\left\{  x\in \mathbb R:\ x<- \frac{10}{3}  \right\}=\left( -\infty,-\frac{10}{3} \right)$
>- Minimo: $\text{non esiste}$
>- Massimo: $\text{non esiste}$


---
## Maggiorante e minorante
>[!info] Definizione di Maggiorante
>$A \underline{\subset}\mathbb R,\ A\ne\oslash$ Si dice che $M\in\mathbb R$ è in maggiorante di $A$ ($M(A)=\{\dots\}$) se $M \underline{>}a\ \ \forall a\in A$

>[!info] Definizione di Minorante
>$A \underline{\subset}\mathbb R,\ A\ne\oslash$ Si dice che $m\in\mathbb R$ è in minorante di $A$ ($m(A)=\{\dots\}$) se $m \underline{<}a\ \ \forall a\in A$

Sono infiniti se presenti
>[!example] Esempio precedente dei numeri reali
>$A=\{x\in \mathbb R:\ 3x+2<-8\}$
>Risolviamo primo l'equazione: $3x<-10\to x<-\frac{10}{3}$
>$A=\left\{  x\in \mathbb R:\ x<- \frac{10}{3}  \right\}=\left( -\infty,-\frac{10}{3} \right)$
>- Minorante: $m(a)=\oslash$
>- Maggiorante: $M(A)=\left\{ x\in\mathbb R:\ x \underline{>}-\frac{10}{3} \right\}$

>[!info] Definizione di limitazione
>- $A$ si dice illimitato superiormente se $M(A)=\oslash$
>- $A$ si dice illimitato inferiormente se $m(A)=\oslash$

>[!info] Definizione di limitazione
>- $L$ è l'estremo superiore di $A$ ($L=\sup A$) se $L=\matrix{+\infty \text{ Se A è illimitato superiormente} && minM(A)\text{ se A è limitato superiormente}}$
>- $l$ è l'estremo inferiore di $A$ ($l=\inf A$) se $l=\matrix{-\infty \text{ Se A è illimitato inferiomente} && maxM(A)\text{ se A è limitato inferiormente}}$

## Teorema di esistenza dell'esterno inf e sup di un insieme
$$
A \underline{\subset}\mathbb R,A\ne 0\ \ \exists\sup A\text{ e }\inf A
$$
>[!tip] Dimostrazione
>**Tesi:**$\exists \sup A$
>Se $A$ è ill. sup. allora $\sup A=+\infty$.
>Se $A$ è ill. sup. $sup A=\min M(A)$. Dimostrare $\exists \min M(A)$
>Sono sicuramente separati per definizione del maggiorante, e allora per assioma di continuità: $\exists c\in\mathbb R:a \underline{<}c \underline{<}M(A)$.
>Per definizione $c$ è anche maggiorante dell'insieme, ed è dunque il minimo dell'insieme $A$.

## Caratterizzazione del sup e dell'inf
$$
\sup A=\matrix{+\infty && \text{se ill sup} || minM(A)&&\text{se A lim sup}}
$$


$$
\begin{matrix}
supA \underline{>}a && \forall a\in A  \\
\matrix{\forall \epsilon>0 & L-\epsilon \text{ non è un maggiorante}&\exists a\in A:a_{\epsilon}>L-\epsilon}
\end{matrix}
$$

### inferiorie
$$
infA= \begin{matrix}
- \infty&&\text{se A è ill inf}\Leftrightarrow m(A)=\oslash\ \ \forall m\in\mathbb R\text{ m non è minorante} \\
\max m(A)&&\text{se A è lim inf}
\end{matrix}
$$

$A$ limitato inferiormente $l=infA=maxm(A)$

$$
\begin{matrix}
l \underline{<}a\ &&\forall a\in A \\
\forall\epsilon>0&&l+\epsilon \text{ non è minorante}\to \exists a_{\epsilon}\in A:a_{\epsilon}<l+\epsilon
\end{matrix}
$$

