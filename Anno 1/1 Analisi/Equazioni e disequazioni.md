---
Materia:
  - Analisi
tags:
Link risorse:
Libro:
Imparato: false
Ordine: 20
aliases:
---
## Equazioni polinomiali

Un'equazione polinomiale è un'equazione del tipo

$$
P(x)=0
$$

dove $P(x)$ è un polinomio.

>[!example]
>$$
>x^2-5x+6=0
>$$
>
>Scomponiamo:
>$$
>(x-2)(x-3)=0
>$$
>
>quindi:
>$$
>x=2\qquad\text{oppure}\qquad x=3.
>$$

---

## Disequazioni polinomiali

Una disequazione polinomiale è del tipo

$$
P(x)>0,
$$

oppure

$$
P(x)<0,
$$

e analogamente con $\geq$ e $\leq$.

Il metodo consiste generalmente in:

1. portare tutto a un membro;
2. scomporre il polinomio;
3. trovare gli zeri;
4. studiare il segno dei fattori;
5. scegliere gli intervalli che soddisfano la disequazione.

>[!example]
>Risolviamo
>$$
>x^2-5x+6>0.
>$$
>
>Scomponiamo:
>$$
>(x-2)(x-3)>0.
>$$
>
>Gli zeri sono
>$$
>x=2,\qquad x=3.
>$$
>
>Il prodotto è positivo quando i due fattori hanno lo stesso segno:
>$$
>x<2
>$$
>oppure
>$$
>x>3.
>$$
>
>Quindi
>$$
>\boxed{x\in(-\infty,2)\cup(3,+\infty)}.
>$$

---
## Disequazioni irrazionali

Una disequazione irrazionale contiene l'incognita sotto radice.

Prima di elevare al quadrato bisogna imporre le condizioni che garantiscono l'esistenza della radice.

### Caso $\sqrt{f(x)}<g(x)$

Affinché la disequazione possa essere verificata è necessario che

$$
f(x)\geq0
$$

e, poiché

$$
\sqrt{f(x)}\geq0,
$$

deve anche essere

$$
g(x)>0.
$$

In queste condizioni possiamo elevare al quadrato:

$$
\sqrt{f(x)}<g(x)
\iff
\begin{cases}
f(x)\geq0\\
g(x)>0\\
f(x)<g(x)^2
\end{cases}
$$

### Caso $\sqrt{f(x)}>g(x)$

Bisogna distinguere i casi in base al segno di $g(x)$.

Se

$$
g(x)<0,
$$

la disequazione è automaticamente verificata ogni volta che

$$
f(x)\geq0
$$

perché una radice quadrata è sempre non negativa.

Se invece

$$
g(x)\geq0,
$$

possiamo elevare al quadrato e confrontare

$$
f(x)>g(x)^2.
$$

---
## Disequazioni esponenziali

Consideriamo una disequazione del tipo

$$
a^{f(x)}>a^{g(x)}.
$$

Il procedimento dipende dal valore della base.

### Caso $a>1$

Poiché l'esponenziale è strettamente crescente:

$$
a^{f(x)}>a^{g(x)}
\iff
f(x)>g(x).
$$

>[!example]
>$$
>2^{x+1}>2^3
>$$
>
>Poiché $2>1$:
>$$
>x+1>3
>$$
>
>quindi
>$$
>\boxed{x>2}.
>$$

### Caso $0<a<1$

Poiché l'esponenziale è strettamente decrescente, il verso della disequazione si inverte:

$$
a^{f(x)}>a^{g(x)}
\iff
f(x)<g(x).
$$

>[!example]
>$$
>\left(\frac12\right)^{x+1}>
>\left(\frac12\right)^3
>$$
>
>Poiché
>$$
>0<\frac12<1,
>$$
>otteniamo
>$$
>x+1<3
>$$
>
>quindi
>$$
>\boxed{x<2}.
>$$


---
## Disequazioni logaritmiche

Consideriamo

$$
\log_a f(x)>\log_a g(x).
$$

Prima di tutto bisogna imporre le **condizioni di esistenza**:

$$
f(x)>0
$$

e

$$
g(x)>0.
$$

### Caso $a>1$

Poiché il logaritmo è strettamente crescente:

$$
\log_a f(x)>\log_a g(x)
\iff
f(x)>g(x).
$$

Sempre rispettando le condizioni di esistenza.

### Caso $0<a<1$

Poiché il logaritmo è strettamente decrescente, il verso si inverte:

$$
\log_a f(x)>\log_a g(x)
\iff
f(x)<g(x).
$$

>[!example]
>Risolviamo
>$$
>\log_2(x-1)>\log_2 3.
>$$
>
>Condizione di esistenza:
>$$
>x-1>0\implies x>1.
>$$
>
>Poiché $2>1$:
>$$
>x-1>3
>$$
>
>quindi
>$$
>x>4.
>$$
>
>La soluzione rispetta anche la condizione di esistenza:
>$$
>\boxed{x>4}.
>$$