---
Materia:
tags:
Link risorse:
Libro:
Imparato: false
Ordine: 6
aliases:
---
In generale le misure si dividono tra **scalari** (lavoro, energia, calore, distanza...) e **vettori** (velocità, movimento, forza...).

Un vettore è una grandezza caratterizzata da:
- **modulo**;
- **direzione**;
- **verso**.

Un vettore può essere scomposto nelle sue componenti lungo gli assi del sistema di riferimento.

Per trovare le componenti di un vettore si considera il sistema di coordinate e si proietta il vettore lungo ciascun asse.

---
## Versori
I **versori** sono vettori particolari di modulo pari a $1$, utilizzati per indicare determinate direzioni.

I versori degli assi cartesiani sono: $\hat{\imath},\ \hat{\jmath},\  \hat{k}$
dove:

- $\hat{\imath}$ indica la direzione dell'asse $x$;
- $\hat{\jmath}$ indica la direzione dell'asse $y$;
- $\hat{k}$ indica la direzione dell'asse $z$.

I versori si indicano con un **cappellino** invece che con una freccia.

Un vettore può quindi essere rappresentato utilizzando i versori.
$$
\boxed{\vec r=r_x\hat{\imath}+r_y\hat{\jmath}}
$$

$$
\boxed{
\vec v=
v_x\hat{\imath}
+
v_y\hat{\jmath}
+
v_z\hat{k}
}
$$

![[Moto in più direzioni-1790778471547.webp]]

---
## Somma di vettori
![[Moto in più direzioni-1790769132192.webp|right]]
La somma di due vettori può essere rappresentata geometricamente mediante la **regola del parallelogramma** (o punta-coda).

Per calcolare la **differenza** tra due vettori è possibile applicare la stessa tecnica usando l'inverso del secondo vettore.

Se i vettori sono espressi tramite le loro componenti, la somma si effettua componente per componente.
$$
\boxed{
\vec a\pm \vec b=
(a_x\pm b_x,\ a_y\pm b_y)
}
$$


Equivalentemente, usando i versori:

$$

\vec a+\vec b=
(a_x+b_x)\hat{\imath}
+
(a_y+b_y)\hat{\jmath}

$$



---
## Prodotto scalare
### Scalare per vettore
Il prodotto definisce un nuovo vettore con stessa direzione e verso ma lunghezza uguale al prodotto della lunghezza del vettore iniziale per lo scalare (verso opposto se lo scalare è negativo).

$$
\boxed{|a \vec{v}|=a\cdot|\vec{v}|}
$$
![[Vettori-1790779713030.webp]]
### Vettore per vettore

$$
\boxed{\vec{}v_{1} \vec{v}=|\vec{v_{1}}|\cdot|\vec{v_{2}}|\cos \alpha}
$$
![[Vettori-1790779878428.webp|334]] ![[Vettori-1790780048975.webp|354]]



---
## Prodotto vettoriale
Vettore la cui intensità data dal prodotto dei corpi per il seno dell'angolo  dell'angolo alpha
$$
\boxed{|\vec{v_{1}}\cdot \vec{v_{2}}|=|\vec{v_{1}}||\vec{v_{2}}|\sin \alpha}
$$
![[Vettori-1790780304805.webp]]

risultato delle sottomatrici

$$
\begin{matrix}
\hat{\imath} & \hat{\jmath} & \hat{k} \\
v_{1x} & v_{1y} & v_{1z} \\
v_{2x} & v_{2y} & v_{2z}
\end{matrix}
$$

trovare determinante (anche se non so cosa sia)

---
## Angoli e componenti di un vettore
Per capire come scomporre un vettore bisogna utilizzare seno e coseno.

Supponiamo di avere un vettore $\vec r$ di modulo $r$ che forma un angolo $\alpha$ con il **semiasse positivo delle $x$**.
![[triangolo|200x200]]
Graficamente, il vettore e le sue componenti formano un triangolo rettangolo:
- $r$ è l'ipotenusa;
- $r_x$ è il cateto orizzontale;
- $r_y$ è il cateto verticale.

Per definizione:

$$  
\cos\alpha=  
\frac{\text{cateto adiacente}}{\text{ipotenusa}} \implies \cos\alpha=\frac{r_x}{r} 
$$


Analogamente:
$$  
\sin\alpha=  
\frac{\text{cateto opposto}}{\text{ipotenusa}}  \implies\sin\alpha=\frac{r_y}{r}
$$


e ${r_y=r\sin\alpha}$, pertanto:
  
$$
\boxed{\vec r=(r\cos\alpha,r\sin\alpha)}  
$$

Il seno e il coseno permettono di determinare **quanto di un vettore è diretto lungo ciascun asse**.
Se il vettore è quasi orizzontale, allora l'angolo $\alpha$ è piccolo: $\cos\alpha\approx1$, e: $\sin\alpha\approx0$, quindi quasi tutto il vettore è diretto lungo $x$.
Se invece il vettore è quasi verticale: $\alpha\approx90^\circ$, allora: $\cos90^\circ=0$, e: $\sin90^\circ=1$, quindi la componente orizzontale è nulla e il vettore è completamente diretto lungo $y$.

> [!example]  
> Se un vettore ha modulo: $r=10$ e forma un angolo: $\alpha=30^\circ$ con l'asse $x$, allora:
> $$  
> r_x=10\cos30^\circ  
> $$
> $$  
> r_y=10\sin30^\circ  
> $$
> 
> Poiché:
> $$  
> \cos30^\circ=\frac{\sqrt3}{2}  
> $$
> $$  
> \sin30^\circ=\frac12  
> $$
> 
> si ottiene:
> 
> $$  
> r_x=5\sqrt3  
> $$
> 
> $$  
> r_y=5  
> $$

Le formule:
$$  
\boxed{r_x=r\cos\alpha  \qquad r_y=r\sin\alpha}
$$

valgono direttamente quando $\alpha$ è l'angolo misurato rispetto all'asse $x$.

Se invece l'angolo viene misurato rispetto all'asse $y$, seno e coseno si scambiano.


$$  
\boxed{r_y=r\cos\beta \qquad r_x=r\sin\beta}  
$$

Questo accade perché il coseno è sempre associato al **cateto adiacente all'angolo**, mentre il seno è associato al **cateto opposto**.


### Relazione tra $\alpha$ e $\beta$
In un triangolo rettangolo i due angoli acuti sono complementari:
$$  
\alpha+\beta=90^\circ  
$$

quindi:
$$  
\beta=90^\circ-\alpha  
$$

Per questo valgono le relazioni: $\sin\beta=\cos\alpha$ e $\cos\beta=\sin\alpha$. Quindi le due scritture:
$$  
r_x=r\cos\alpha  \qquad r_x=r\sin\beta  
$$

descrivono la stessa componente.

### Segno delle componenti
Seno e coseno permettono di trovare il modulo delle componenti, ma bisogna anche osservare il **verso del vettore**.

### Primo quadrante
$$  
x>0,\qquad y>0  
$$
quindi:
$$  
\vec r=(+r_x,+r_y)  
$$

### Secondo quadrante
$$  
x<0,\qquad y>0  
$$
quindi:
$$  
\vec r=(-r_x,+r_y)  
$$

### Terzo quadrante
$$  
x<0,\qquad y<0  
$$
quindi:
$$  
\vec r=(-r_x,-r_y)  
$$

### Quarto quadrante
$$  
x>0,\qquad y<0  
$$
quindi:
$$  
\vec r=(+r_x,-r_y)  
$$

Per esempio, se un vettore è diretto verso destra e verso il basso:

$$  
r_x>0  
$$

mentre:

$$  
r_y<0  
$$

e quindi può essere scritto come:

$$  
\boxed{\vec r=(r\cos\alpha,-r\sin\alpha)}  
$$

se $\alpha$ rappresenta l'angolo rispetto all'asse orizzontale.

---
## Tangente dell'angolo
Dal triangolo rettangolo:

$$  
\tan\alpha=  
\frac{\text{cateto opposto}}{\text{cateto adiacente}}  
$$

quindi, se:
- $H$ è lo spostamento verticale
- $D$ è lo spostamento orizzontale

si ha:

$$  
\boxed{\tan\alpha=\frac{H}{D}}  
$$

Da cui è possibile ricavare l'angolo:

$$  
\boxed{\alpha=\arctan\left(\frac{H}{D}\right)}  
$$

