---
Materia:
  - Analisi
Imparato: false
tags:
Ordine: 11
---
## Funzione potenza
Consideriamo la funzione

$$
f:\mathbb R\to\mathbb R,\qquad f(x)=x^n,\qquad n\in\mathbb N.
$$

Il comportamento della funzione dipende dal fatto che $n$ sia **pari** oppure **dispari**.

### Caso $n=1$

$$
f(x)=x
$$

Il grafico è una retta passante per l'origine.

La funzione è:

- dispari;
- strettamente crescente;
- iniettiva;
- suriettiva su $\mathbb R$.


### Esponente pari

Se $n$ è pari:

$$
f(x)=x^n
$$

è una funzione **pari**, infatti

$$
f(-x)=(-x)^n=x^n=f(x).
$$

Il grafico è simmetrico rispetto all'asse $y$.

>[!example] Esempio
>Per $n=2$:
>$$
>f(x)=x^2
>$$
>il grafico è una parabola con vertice nell'origine.

Per $n$ pari:

- dominio:
$$
D_f=\mathbb R
$$

- immagine:
$$
\operatorname{Im}(f)=[0,+\infty)
$$

- è strettamente decrescente in
$$
(-\infty,0]
$$

- è strettamente crescente in
$$
[0,+\infty)
$$

La funzione non è iniettiva su tutto $\mathbb R$, perché

$$
f(x)=f(-x).
$$

Per renderla iniettiva possiamo restringere il dominio $f:[0,+\infty)\to[0,+\infty)$, rendendo la funzione biettiva ed invertibile.


### Esponente dispari

Se $n$ è dispari:

$$
f(x)=x^n
$$

è una funzione **dispari**, infatti

$$
f(-x)=(-x)^n=-x^n=-f(x).
$$

Il grafico è simmetrico rispetto all'origine.

Per $n$ dispari:

- dominio:
$$
D_f=\mathbb R
$$

- immagine:
$$
\operatorname{Im}(f)=\mathbb R
$$

- è strettamente crescente su tutto $\mathbb R$;
- è iniettiva;
- è suriettiva su $\mathbb R$.

>[!example] Esempio
>$$
>f(x)=x^3
>$$
>è dispari, strettamente crescente e biettiva da $\mathbb R$ in $\mathbb R$.

---
## Funzione radice

La funzione radice è legata alla funzione potenza.

### Radice con indice pari

Consideriamo $f(x)=\sqrt[n]{x}$ con $n$ pari.
- Il dominio è $D_f=[0,+\infty)$ perché nei numeri reali non possiamo calcolare una radice di indice pari di un numero negativo.
- L'immagine è $[0,+\infty)$
- La funzione è strettamente crescente.
- $f(x)=\sqrt[n]{x}$ è l'inversa della funzione $g(x)=x^n$ ristretta a $[0,+\infty)$

>[!warning] Attenzione
>In generale
>$$
>\sqrt{x^2}=|x|,
>$$
>quindi
>$$
>\sqrt{x^2}=
>\begin{cases}
>x & x\geq0\\
>-x & x<0.
>\end{cases}
>$$
>
>Per questo, se vogliamo che $\sqrt{x}$ sia l'inversa di $x^2$, dobbiamo restringere la funzione $x^2$ al dominio
>$$
>[0,+\infty).
>$$

### Radice con indice dispari

Se $n$ è dispari:

$$
f(x)=\sqrt[n]{x}
$$

è definita per ogni numero reale.

Quindi:

$$
D_f=\mathbb R
$$

e

$$
\operatorname{Im}(f)=\mathbb R.
$$

È strettamente crescente e rappresenta l'inversa di

$$
x\mapsto x^n.
$$

>[!example]- Caso $n=3$
>Consideriamo
>$$
>f:\mathbb R\to\mathbb R,\qquad f(x)=x^3.
>$$
>
>La funzione è strettamente crescente, iniettiva e suriettiva, quindi è biettiva.
>
>Ammette quindi funzione inversa:
>$$
>f^{-1}(x)=\sqrt[3]{x}.
>$$
>
>Infatti:
>$$
>\sqrt[3]{x^3}=x
>$$
>e
>$$
>(\sqrt[3]{x})^3=x
>$$
>per ogni $x\in\mathbb R$.

---

## Funzione esponenziale

Sia

$$
a>0,\qquad a\neq1.
$$

Si definisce funzione esponenziale

$$
f(x)=a^x.
$$

Il dominio è

$$
D_f=\mathbb R
$$

e l'immagine è

$$
\operatorname{Im}(f)=(0,+\infty).
$$

In particolare

$$
a^x>0
$$

per ogni $x\in\mathbb R$.

Inoltre:

$$
a^0=1.
$$

Quindi il grafico passa sempre per il punto

$$
(0,1).
$$

### Caso $a>1$

Se

$$
a>1
$$

la funzione esponenziale è **strettamente crescente**:

$$
x_1<x_2\implies a^{x_1}<a^{x_2}.
$$

### Caso $0<a<1$

Se

$$
0<a<1
$$

la funzione esponenziale è **strettamente decrescente**:

$$
x_1<x_2\implies a^{x_1}>a^{x_2}.
$$

---

## Funzione logaritmo

Sia $a>0,\ a\neq 1$, la funzione logaritmo in base $a$ è definita da
$$
f(x)=\log_a x.
$$

- Il dominio è $D_f=(0,+\infty)$
- L'immagine è $\operatorname{Im}(f)=\mathbb R$

Il logaritmo è la funzione **inversa** dell'esponenziale:

$$
y=\log_a x
\iff
a^y=x.
$$

In particolare $\log_a1=0$ perché $a^0=1.$

### Caso $a>1$

Se

$$
a>1
$$

la funzione logaritmo è [[Proprietà delle funzioni reali|strettamente crescente]].

### Caso $0<a<1$

Se

$$
0<a<1
$$

la funzione logaritmo è [[Proprietà delle funzioni reali|strettamente decrescente]].