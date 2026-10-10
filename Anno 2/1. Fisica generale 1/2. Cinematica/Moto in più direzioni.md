---
Materia:
  - Fisica
tags:
Link risorse:
Libro:
Imparato: false
Ordine: 5
aliases:
  - vettori
---
![[Moto in più direzioni-1790767960214.webp|right]]
Nel [[Movimento unidirezionale|moto in una dimensione]] è sufficiente una coordinata per descrivere la posizione di un punto materiale. Se il corpo può muoversi in più direzioni, dobbiamo invece conoscere **più coordinate contemporaneamente**:
- nel **piano (2D)** bastano $x(t)$ e $y(t)$;
- nello **spazio (3D)** servono $x(t)$, $y(t)$ e $z(t)$.
In un sistema di riferimento cartesiano gli assi sono perpendicolari tra loro; nel caso tridimensionale possiamo orientarli secondo la **regola della mano destra**.
Le coordinate indicano *dove* si trova il punto all'istante $t$. Le loro variazioni nel tempo descrivono *come* si muove.

---
## Vettore posizione

La posizione del punto materiale $P$ rispetto all'origine $O$ è rappresentata dal **[[Vettori|vettore posizione]]**:
$$
\vec r(t)=\overrightarrow{OP}
$$
In tre dimensioni:
$$
\boxed{\vec r(t)=\big(x(t),y(t),z(t)\big)}
$$
Nel piano:
$$
\boxed{\vec r(t)=\big(x(t),y(t)\big)}
$$
La scrittura $(x,y,z)$ indica le **componenti cartesiane** di un unico vettore, non tre vettori separati.

### Angoli e componenti nel piano
Se un vettore $\vec r$ ha modulo $r=|\vec r|$ e forma un angolo $\theta$ con il **semiasse positivo delle $x$**, le sue componenti sono:
$$
\boxed{r_x=r\cos\theta,\qquad r_y=r\sin\theta}
$$
Infatti, nel triangolo rettangolo associato al vettore, $r$ è l'ipotenusa, $r_x$ il cateto adiacente all'angolo e $r_y$ quello opposto (considerando i segni delle componenti nel piano cartesiano).
Viceversa, dalle componenti ricaviamo il modulo:
$$
\boxed{r=\sqrt{r_x^2+r_y^2}}
$$
Le formule valgono anche per i vettori velocità e accelerazione, purché $\theta$ sia l'angolo del **vettore che stiamo scomponendo**: la direzione della velocità, ad esempio, non deve necessariamente coincidere con quella della posizione.

>[!example]- Esempio: scomposizione di un vettore
>Un vettore ha modulo $r=10\,\mathrm m$ e forma un angolo di $30^\circ$ con il semiasse positivo delle $x$.
>$$
>r_x=10\cos30^\circ=5\sqrt3\,\mathrm m
>$$
>$$
>r_y=10\sin30^\circ=5\,\mathrm m
>$$
>Le componenti sono quindi $(5\sqrt3,5)\,\mathrm m$. Se il vettore si trovasse in un altro quadrante, almeno una componente potrebbe risultare negativa.

---
## Spostamento e velocità media

Quando un corpo passa dalla posizione $\vec r(t_1)$ alla posizione $\vec r(t_2)$, il **vettore spostamento** è:
$$
\boxed{\Delta\vec r=\vec r(t_2)-\vec r(t_1)}
$$
Nel piano:
$$
\Delta\vec r=(x_2-x_1,\,y_2-y_1)=(\Delta x,\Delta y)
$$
Il vettore spostamento unisce **posizione iniziale e finale**: non coincide necessariamente con la distanza effettivamente percorsa lungo la traiettoria.
La **velocità vettoriale media** nell'intervallo $\Delta t=t_2-t_1$ è:
$$
\boxed{\vec v_{\mathrm{media}}=\frac{\Delta\vec r}{\Delta t}}
$$
Nel piano:
$$
\vec v_{\mathrm{media}}=\left(\frac{\Delta x}{\Delta t},\frac{\Delta y}{\Delta t}\right)
$$
Quindi la velocità media ha una componente per ciascun asse, mentre rimane **un solo vettore**.

---
## Velocità istantanea in più dimensioni

Come nel caso unidimensionale studiato in [[Velocità e accelerazione]], la **velocità istantanea** si ottiene facendo tendere a zero l'intervallo di tempo della velocità media:
$$
\vec v(t)=\lim_{\Delta t\to0}\frac{\vec r(t+\Delta t)-\vec r(t)}{\Delta t}
$$
Per definizione di derivata:
$$
\boxed{\vec v(t)=\frac{d\vec r}{dt}}
$$
**Derivare un vettore in coordinate cartesiane significa derivare separatamente ciascuna delle sue componenti.** Infatti, se:
$$
\vec r(t)=\big(x(t),y(t),z(t)\big)
$$
allora:
$$
\boxed{\vec v(t)=\left(\frac{dx}{dt},\frac{dy}{dt},\frac{dz}{dt}\right)}
$$
ossia:
$$
\boxed{v_x=\frac{dx}{dt},\qquad v_y=\frac{dy}{dt},\qquad v_z=\frac{dz}{dt}}
$$
Nel piano usiamo soltanto le prime due componenti. La derivata $dx/dt$ descrive quanto rapidamente cambia **la coordinata $x$**, mentre $dy/dt$ descrive la variazione di **$y$**: non sono due moti separati nel tempo, ma due aspetti dello stesso movimento.

### Modulo della velocità e velocità scalare
Il **modulo della velocità vettoriale**, detto anche *velocità scalare* o *rapidità*, è:
$$
\boxed{v(t)=|\vec v(t)|=\sqrt{v_x^2+v_y^2+v_z^2}}
$$
Nel piano:
$$
\boxed{v(t)=\sqrt{v_x^2+v_y^2}}
$$
La velocità scalare è **sempre non negativa**; le singole componenti $v_x,v_y,v_z$ possono invece essere positive, negative o nulle.
> [!important] Attenzione
> Non confondere la velocità scalare $|\vec v|$ con una componente, per esempio $v_x$. Se il corpo cambia direzione mantenendo invariato $|\vec v|$, il **vettore velocità cambia comunque**. È ciò che avviene nel [[Moto circolare|moto circolare uniforme]].

---
## Accelerazione in più dimensioni

L'**accelerazione vettoriale** misura la variazione della velocità vettoriale nel tempo:
$$
\boxed{\vec a(t)=\frac{d\vec v}{dt}=\frac{d^2\vec r}{dt^2}}
$$
In coordinate cartesiane:
$$
\boxed{\vec a(t)=\left(\frac{dv_x}{dt},\frac{dv_y}{dt},\frac{dv_z}{dt}\right)}
$$
Dunque:
$$
\boxed{a_x=\frac{dv_x}{dt}=\frac{d^2x}{dt^2}}
$$
$$
\boxed{a_y=\frac{dv_y}{dt}=\frac{d^2y}{dt^2}}
$$
$$
\boxed{a_z=\frac{dv_z}{dt}=\frac{d^2z}{dt^2}}
$$
L'accelerazione può essere diversa da zero **sia quando varia il modulo della velocità sia quando cambia la sua direzione**. Perciò accelerazione e velocità non devono necessariamente avere la stessa direzione.

---
## Ricostruire il moto dalle componenti

Se conosciamo le componenti della velocità, possiamo ricostruire le coordinate della posizione a patto di conoscere anche la **posizione iniziale**.
In forma generale, scegliendo un istante iniziale $t_0$:
$$
\boxed{x(t)=x_0+\int_{t_0}^{t}v_x(\tau)\,d\tau}
$$
$$
\boxed{y(t)=y_0+\int_{t_0}^{t}v_y(\tau)\,d\tau}
$$
(Analogamente per $z$.) Se conosciamo invece l'accelerazione, dobbiamo prima ricavare la velocità, conoscendo anche quella iniziale:
$$
\boxed{v_x(t)=v_{0x}+\int_{t_0}^{t}a_x(\tau)\,d\tau}
$$
$$
\boxed{v_y(t)=v_{0y}+\int_{t_0}^{t}a_y(\tau)\,d\tau}
$$
L'**integrale** qui rappresenta l'accumulo delle variazioni nel tempo: è l'operazione inversa della derivazione usata per ottenere velocità e accelerazione. Le condizioni iniziali servono a fissare la soluzione specifica del moto.

### Caso particolare: accelerazione costante
Se $\vec a$ è costante e poniamo $\Delta t=t-t_0$, otteniamo:
$$
\boxed{\vec v(t)=\vec v_0+\vec a\,\Delta t}
$$
$$
\boxed{\vec r(t)=\vec r_0+\vec v_0\,\Delta t+\frac12\vec a\,(\Delta t)^2}
$$
Sono le leggi del [[Moti particolari|moto uniformemente accelerato]], applicate **componente per componente**. Per esempio, nel [[Moto del proiettile]] si ha $a_x=0$ e $a_y=-g$, quindi il moto è uniforme lungo $x$ e uniformemente accelerato lungo $y$.

---
## Esempio completo nel piano

>[!example]- Dalla posizione alla velocità e all'accelerazione
>Un punto materiale si muove nel piano secondo le leggi orarie (con $t$ in secondi, coordinate in metri e coefficienti espressi nelle corrispondenti unità SI):
>$$
>x(t)=2t,\qquad y(t)=t^2
>$$
>**1. Vettore posizione**
>$$
>\vec r(t)=(2t,t^2)
>$$
>**2. Vettore velocità**: deriviamo ogni coordinata rispetto al tempo.
>$$
>v_x(t)=\frac{d(2t)}{dt}=2,\qquad v_y(t)=\frac{d(t^2)}{dt}=2t
>$$
>Quindi:
>$$
>\boxed{\vec v(t)=(2,2t)}
>$$
>**3. Vettore accelerazione**: deriviamo le componenti della velocità.
>$$
>a_x(t)=0,\qquad a_y(t)=2
>$$
>$$
>\boxed{\vec a(t)=(0,2)}
>$$
>**4. All'istante $t=2\,\mathrm s$**:
>$$
>\vec r(2)=(4,4)\,\mathrm m
>$$
>$$
>\vec v(2)=(2,4)\,\mathrm{m/s},\qquad\vec a(2)=(0,2)\,\mathrm{m/s^2}
>$$
>La velocità scalare in quell'istante è:
>$$
>v(2)=\sqrt{2^2+4^2}=2\sqrt5\,\mathrm{m/s}
>$$
>Il corpo si muove verso destra e verso l'alto; l'accelerazione è soltanto verticale.

---
## Collegamenti con gli altri argomenti

- **[[Vettori]]**: componenti, modulo e orientazione dei vettori.
- **[[Velocità e accelerazione]]**: definizioni nel moto a una dimensione.
- **[[Moto del proiettile]]**: applicazione delle leggi per componenti a un moto nel piano.
- **[[Moto circolare]]**: velocità che cambia direzione anche quando il modulo è costante; introduzione alle coordinate polari e alla descrizione intrinseca della traiettoria.

Le **coordinate polari** e le **trasformazioni tra sistemi di riferimento** sono modi diversi di descrivere lo stesso movimento: nelle dispense di Marrucci vengono approfondite separatamente dalla descrizione cartesiana per componenti e potranno essere sviluppate in una nota dedicata, senza appesantire questa.
