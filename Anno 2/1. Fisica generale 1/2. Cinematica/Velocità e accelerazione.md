---
Materia:
  - Fisica
tags:
Link risorse:
Libro:
Imparato: true
Ordine: 3
aliases:
---
## Spostamento
Consideriamo $t_{1},t_{2}$ dove $t_{1}$ è il tempo iniziale e $t_{2}$ quello finale.
consideriamo
- $x_{1}=x(t_{1})$
- $x_{2}=x(t_{2})$
Spostamento nell'intervallo

$$
\Delta x=x_{2}-x_{1}
$$
Lo spostamento rappresenta la **variazione di posizione**. Può essere:
- $\Delta x>0$ → spostamento nel verso positivo dell'asse;
- $\Delta x<0$ → spostamento nel verso negativo;
- $\Delta x=0$ → posizione finale uguale a quella iniziale.

---
## Velocità media
La velocità media nell'intervallo $[t_1,t_2]$ è: $$ v_m= \frac{\Delta x}{\Delta t} = \frac{x_2-x_1}{t_2-t_1} = \frac{x(t_2)-x(t_1)}{t_2-t_1} $$ Rappresenta il **rapporto incrementale** della funzione $x(t)$ tra gli istanti $t_1$ e $t_2$. 

Graficamente, la velocità media corrisponde al **coefficiente angolare della retta secante** che passa per i punti della curva corrispondenti a $t_1$ e $t_2$.

---
## Velocità istantanea
Riducendo progressivamente l'intervallo di tempo: $$ v(t) = \lim_{\Delta t\to0} \frac{x(t+\Delta t)-x(t)}{\Delta t} $$ quindi: $$ \boxed{v(t)=\frac{dx}{dt}=\dot{x}(t)} $$ La velocità istantanea è quindi la **derivata della posizione rispetto al tempo**. La velocità dipende dal **sistema di riferimento** scelto.


---
## Velocità (istantanea) scalare
La **velocità scalare** indica quanto rapidamente viene percorso spazio, indipendentemente dal verso: $$ |\vec v|=\frac{ds}{dt} $$
dove $s$ rappresenta lo **spazio percorso** e $x$ è la coordinata della posizione. In un moto unidimensionale: $$ |\vec v|=\left|\frac{dx}{dt}\right| $$

---
## Rappresentazione grafica
Nel grafico posizione-tempo $x(t)$: 
- la **velocità media** è la pendenza della retta secante; 
- la **velocità istantanea** è la pendenza della retta tangente. 

Quindi:
- $v>0$ → $x(t)$ cresce; 
- $v<0$ → $x(t)$ decresce; 
- $v=0$ → tangente orizzontale.

---
## Determinare moto da velocità
L'operazione inversa della derivata è l'**integrale**. Se conosciamo $v(t)$: $$ x(t)=x_0+\int_{t_0}^{t}v(t')\,dt' $$ dove: $$ x_0=x(t_0) $$
L’integrale permette di ricostruire la variazione complessiva di una grandezza a partire dalla sua variazione istantanea.

### Moto uniforme da velocità istantanea costante
Se la velocità è costante: $$ v(t)=v $$ allora: $$ x(t) = x_0+\int_{t_0}^{t}v\,dt' $$ da cui: $$ \boxed{x(t)=x_0+v(t-t_0)} $$ Se $t_0=0$: $$ x(t)=x_0+vt $$

---
## Accelerazione
L'**accelerazione istantanea** è la derivata della velocità rispetto al tempo: $$ a(t) = \lim_{\Delta t\to0} \frac{v(t+\Delta t)-v(t)}{\Delta t} $$ quindi: $$ \boxed{ a(t)=\frac{dv}{dt} =\frac{d^2x}{dt^2} =\ddot{x}(t) } $$L'accelerazione è quindi:
- la derivata prima della velocità;
- la derivata seconda della posizione.

### Moto a partire da accelerazione
Se conosciamo $a(t)$: $$ v(t) = v_0+\int_{t_0}^{t}a(t')\,dt' $$ e successivamente: $$ x(t) = x_0+\int_{t_0}^{t}v(t')\,dt' $$
### Accelerazione nulla
Se: $$ a(t)=0 $$ allora: $$ v(t)=v_0 $$ quindi la velocità è **costante**, non necessariamente nulla.


### Accelerazione costante
Se: $$ a(t)=a_0 $$ allora: $$ v(t)=v_0+a_0(t-t_0) $$ e: $$ x(t) = x_0+v_0(t-t_0) +\frac12a_0(t-t_0)^2 $$ Se $t_0=0$: $$ \boxed{ x(t)=x_0+v_0t+\frac12a_0t^2 } $$