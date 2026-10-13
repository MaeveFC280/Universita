---
Materia:
  - Fisica
tags:
Link risorse:
Libro:
Imparato: true
Ordine: 4
aliases:
---
## Quiete
Un corpo è in **quiete** quando la sua posizione non varia nel tempo.

$$
x(t)=x_0
$$

dove $x_0$ è la posizione costante del corpo.

---
## Moto rettilineo uniforme
Il corpo si muove lungo una retta con **velocità costante**.

$$
x(t)=x_0+v(t-t_0)
$$

Se $t_0=0$:

$$
x(t)=x_0+vt
$$

dove:
- $x_0$ = posizione iniziale
- $v$ = velocità costante

Nel grafico posizione-tempo $x(t)$ si ottiene una **retta**.

Il coefficiente angolare è:

$$
v=\frac{\Delta x}{\Delta t}
$$

quindi indica quanto rapidamente varia la posizione nel tempo.

---
## Moto uniformemente accelerato
Il corpo si muove con **accelerazione costante**. La velocità varia linearmente:

$$
v(t)=v_0+a(t-t_0)
$$

La posizione varia secondo:

$$
x(t)=x_0+v_0(t-t_0)+\frac12a(t-t_0)^2
$$



---
## Moto verticale
È il moto di un corpo lanciato o lasciato cadere sotto l'azione della **gravità**.

Scegliamo l'asse $y$ positivo verso l'alto e poniamo $t_0=0$.

L'accelerazione è:

$$
a=-g\simeq -9.81\,\mathrm{m/s^2}
$$

Quindi:

$$
v(t)=v_0-gt
$$

$$
y(t)=y_0+v_0t-\frac12gt^2
$$

### Tempo di caduta
Se il suolo corrisponde a $y=0$, l'istante di impatto $t_s$ si trova imponendo:

$$
y(t_s)=0
$$

e risolvendo l'equazione rispetto a $t_s$.

Al momento dell'impatto:

$$
v(t_s)=v_0-gt_s
$$

Con l'asse orientato verso l'alto, una velocità negativa indica che il corpo si sta muovendo verso il basso.


---
## Moto armonico
Il moto armonico è descritto da funzioni seno o coseno.

La legge oraria può essere scritta come:

$$
x(t)=A\sin(\omega t+\phi)
$$

dove:
- $A$ = **ampiezza**
- $\omega$ = **pulsazione**
- $\phi$ = **fase iniziale**
- $\Phi(t)=\omega t+\phi$ = **fase**

La posizione oscilla tra:

$$
-A\le x(t)\le A
$$
>[!example]
>La funzione: $x(t)=4\sin\left(\frac{2\pi}{5}t\right)$ descrive un moto con le seguenti caratteristiche:
>![[Moti particolari-1790077157038.webp|right|280]]
>- $A=4$
>- $T=5$
>- $\omega=\frac{2\pi}{5}$
>- $\phi=0$
>Si può infatti notare che il grafico raggiunge la sua massima e minima altezza a $y=4$ e ritorna sembra a $y=0$ ogni $5$ unità dell'asse $x$ (secondi). 

### Periodo
Il **periodo** $T$ è il tempo necessario per compiere un'oscillazione completa.

$$
\omega=\frac{2\pi}{T}
$$

e quindi:

$$
T=\frac{2\pi}{\omega}
$$

La frequenza è:

$$
f=\frac1T
$$

perciò:

$$
\omega=2\pi f
$$

### Velocità
La velocità istantanea è la derivata della posizione:

$$
v(t)=\frac{dx}{dt}
$$

quindi:

$$
v(t)=\omega A\cos(\omega t+\phi)
$$

### Accelerazione
Derivando nuovamente:

$$
a(t)=\frac{d^2x}{dt^2}
$$

si ottiene:

$$
a(t)=-\omega^2A\sin(\omega t+\phi)
$$

Poiché:

$$
x(t)=A\sin(\omega t+\phi)
$$

allora:

$$
\boxed{a(t)=-\omega^2x(t)}
$$

Quindi nel moto armonico l'accelerazione è sempre proporzionale alla posizione ma ha **verso opposto**.