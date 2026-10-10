---
Materia:
  - Fisica
tags:
Link risorse:
Libro:
Imparato: false
Ordine: 6
aliases:
---
Un'importante applicazione del [[Moto in più direzioni]] è il **moto del proiettile** (o **moto parabolico/balistico**).

Consideriamo un corpo lanciato in un piano verticale, soggetto soltanto alla gravità. Supponiamo che:
- la **resistenza dell'aria sia trascurabile**;
- l'accelerazione di gravità sia costante, di modulo $g\simeq 9{,}8\,\mathrm{m/s^2}$ e diretta verso il basso;
- l'asse $x$ sia orizzontale e l'asse $y$ verticale, con verso positivo verso l'alto;
- l'istante del lancio sia $t=0$.

Il principio fondamentale è che possiamo **studiare separatamente i movimenti lungo i due assi**: lungo $x$ il moto è uniforme, lungo $y$ è uniformemente accelerato. Se la velocità iniziale ha una componente orizzontale non nulla, la traiettoria è un **arco di parabola**.

---
## Velocità iniziale e angolo di lancio
Supponiamo che il corpo parta dalla posizione $(x_0,y_0)$ con velocità iniziale $\vec v_0$ di modulo $v_0$, inclinata di un angolo $\alpha$ rispetto al semiasse positivo delle $x$.

Scomponiamo il vettore velocità iniziale utilizzando seno e coseno:
$$
\boxed{v_{0x}=v_0\cos\alpha,\qquad v_{0y}=v_0\sin\alpha}
$$
Quindi:
$$
\boxed{\vec v_0=(v_0\cos\alpha,\,v_0\sin\alpha)}
$$
La componente orizzontale è il **cateto adiacente** all'angolo, mentre quella verticale è il **cateto opposto**: per questo compaiono rispettivamente coseno e seno.

> [!important] Attenzione
> L'angolo $\alpha$ descrive la direzione della **velocità iniziale**, non quella della velocità durante tutto il volo. La componente verticale cambia nel tempo, quindi cambia anche la direzione del vettore velocità.

---
## Movimento orizzontale
Lungo l'asse $x$ non agisce alcuna accelerazione:
$$
a_x=0
$$
Di conseguenza, la velocità orizzontale è costante:
$$
\boxed{v_x(t)=v_{0x}=v_0\cos\alpha}
$$
La posizione segue quindi la legge del **moto rettilineo uniforme**:
$$
\boxed{x(t)=x_0+v_0\cos\alpha\,t}
$$

## Movimento verticale
Lungo l'asse $y$ agisce l'accelerazione di gravità, che è diretta verso il basso:
$$
a_y=-g
$$
La velocità verticale varia nel tempo secondo la legge del **moto uniformemente accelerato**:
$$
\boxed{v_y(t)=v_{0y}-gt=v_0\sin\alpha-gt}
$$
La posizione verticale è:
$$
\boxed{y(t)=y_0+v_0\sin\alpha\,t-\frac12gt^2}
$$
Il termine $-\frac12gt^2$ è negativo perché abbiamo scelto il verso positivo di $y$ verso l'alto.

In forma vettoriale:
$$
\boxed{\vec r(t)=\left(x_0+v_0\cos\alpha\,t,\;y_0+v_0\sin\alpha\,t-\frac12gt^2\right)}
$$
$$
\boxed{\vec v(t)=\left(v_0\cos\alpha,\;v_0\sin\alpha-gt\right),\qquad\vec a=(0,-g)}
$$

---
## Equazione della traiettoria
Le leggi $x(t)$ e $y(t)$ forniscono la posizione a ogni istante. Per trovare **la forma geometrica della traiettoria**, eliminiamo il tempo dalle due equazioni.

Se $v_0\cos\alpha\neq0$, dalla legge oraria orizzontale ricaviamo:
$$
t=\frac{x-x_0}{v_0\cos\alpha}
$$
Sostituendo nella legge verticale:
$$
y(x)=y_0+v_0\sin\alpha\,\frac{x-x_0}{v_0\cos\alpha}-\frac12g\left(\frac{x-x_0}{v_0\cos\alpha}\right)^2
$$
Poiché $\sin\alpha/\cos\alpha=\tan\alpha$, otteniamo:
$$
\boxed{y(x)=y_0+(x-x_0)\tan\alpha-\frac{g(x-x_0)^2}{2v_0^2\cos^2\alpha}}
$$
È un'equazione di **secondo grado in $x$**, quindi rappresenta una parabola con concavità verso il basso. Il moto puramente verticale ($v_{0x}=0$) è un caso particolare in cui non si può eliminare il tempo dividendo per $v_{0x}$: la traiettoria è una retta verticale.

---
## Punto più alto della traiettoria
Se il proiettile è lanciato inizialmente verso l'alto ($v_0\sin\alpha>0$), arriva a un punto in cui la componente verticale della velocità si annulla:
$$
v_y(t_{\max})=0
$$
Partendo da $v_y(t)=v_0\sin\alpha-gt$:
$$
0=v_0\sin\alpha-gt_{\max}
$$
Ricaviamo il **tempo per raggiungere la quota massima**:
$$
\boxed{t_{\max}=\frac{v_0\sin\alpha}{g}}
$$
Sostituendo questo istante nella posizione verticale troviamo l'**altezza massima**:
$$
y_{\max}=y_0+v_0\sin\alpha\left(\frac{v_0\sin\alpha}{g}\right)-\frac12g\left(\frac{v_0\sin\alpha}{g}\right)^2
$$
Semplificando:
$$
\boxed{y_{\max}=y_0+\frac{v_0^2\sin^2\alpha}{2g}}
$$
L'altezza guadagnata rispetto alla quota iniziale è dunque $h_{\max}=y_{\max}-y_0$.

> [!important] Attenzione
> Nel punto più alto **non si annulla tutta la velocità**: si annulla solo $v_y$. Se $v_{0x}\neq0$, resta $v_x=v_0\cos\alpha$ e il corpo continua a muoversi orizzontalmente. Anche nel punto più alto l'accelerazione vale $(0,-g)$.

---
## Tempo di volo e gittata
La **gittata** $D$ è lo spostamento orizzontale tra il punto di lancio e quello di arrivo, assunto positivo per un lancio verso destra:
$$
D=x_f-x_0
$$

### Caso particolare: lancio e arrivo alla stessa altezza
Supponiamo che il proiettile parta e arrivi alla **stessa quota**, cioè $y_f=y_0$, e che $v_0\sin\alpha>0$.

Per trovare il **tempo totale di volo** $t_f$, imponiamo $y(t_f)=y_0$:
$$
y_0+v_0\sin\alpha\,t_f-\frac12gt_f^2=y_0
$$
Portando tutto a sinistra e raccogliendo $t_f$:
$$
t_f\left(v_0\sin\alpha-\frac12gt_f\right)=0
$$
La soluzione $t_f=0$ corrisponde all'istante del lancio. L'altra soluzione è l'istante in cui il proiettile ritorna alla quota iniziale:
$$
\boxed{t_f=\frac{2v_0\sin\alpha}{g}=2t_{\max}}
$$
Durante questo tempo la velocità orizzontale resta costante, perciò:
$$
D=v_{0x}t_f=v_0\cos\alpha\,\frac{2v_0\sin\alpha}{g}
$$
Otteniamo prima:
$$
D=\frac{2v_0^2\sin\alpha\cos\alpha}{g}
$$
Usando $\sin(2\alpha)=2\sin\alpha\cos\alpha$ troviamo la **formula della gittata**:
$$
\boxed{D=\frac{v_0^2\sin(2\alpha)}{g}}
$$
Per $0<\alpha<90^\circ$, mantenendo fissi $v_0$ e $g$, la gittata è massima quando $\sin(2\alpha)=1$, ossia quando:
$$
\boxed{\alpha=45^\circ,\qquad D_{\max}=\frac{v_0^2}{g}}
$$
Questo risultato vale **solo per lancio e arrivo alla stessa quota**, trascurando la resistenza dell'aria.

### Caso generale: quote iniziale e finale diverse
Se $y_f\neq y_0$, **non possiamo usare direttamente** la formula $D=v_0^2\sin(2\alpha)/g$.

Bisogna prima trovare il tempo di arrivo risolvendo:
$$
\boxed{y_f=y_0+v_0\sin\alpha\,t_f-\frac12gt_f^2}
$$
Scelto il tempo fisicamente pertinente (con $t_f>0$), si calcola la gittata attraverso:
$$
\boxed{D=v_0\cos\alpha\,t_f}
$$
La stessa procedura comprende anche il **lancio orizzontale** da una certa altezza, ponendo $\alpha=0$.


> [!example]- Lancio obliquo con ritorno alla quota iniziale
> Un corpo viene lanciato dal suolo con velocità iniziale $v_0=20\,\mathrm{m/s}$ e angolo $\alpha=30^\circ$. Trascuriamo l'aria e prendiamo $g=9{,}8\,\mathrm{m/s^2}$. Troviamo le componenti iniziali, il tempo per arrivare al punto più alto, la quota massima, il tempo di volo e la gittata.
> **1. Componenti della velocità iniziale**
> $$
> v_{0x}=20\cos30^\circ=10\sqrt3\simeq17{,}32\,\mathrm{m/s}
> $$
> $$
> v_{0y}=20\sin30^\circ=10\,\mathrm{m/s}
> $$
> **2. Tempo per raggiungere il punto più alto**
> $$
> t_{\max}=\frac{v_{0y}}g=\frac{10}{9{,}8}\simeq1{,}02\,\mathrm s
> $$
> **3. Altezza massima rispetto al suolo** ($y_0=0$)
> $$
> y_{\max}=\frac{v_{0y}^2}{2g}=\frac{100}{19{,}6}\simeq5{,}10\,\mathrm m
> $$
> **4. Tempo di volo**
> $$
> t_f=\frac{2v_{0y}}g=\frac{20}{9{,}8}\simeq2{,}04\,\mathrm s
> $$
> **5. Gittata**
> $$
> D=v_{0x}t_f=\frac{200\sqrt3}{9{,}8}\simeq35{,}35\,\mathrm m
> $$
> In alternativa: $D=v_0^2\sin(2\alpha)/g$, che fornisce lo stesso risultato.

---
## Idea fondamentale
Nel moto del proiettile **non bisogna cercare di studiare tutto contemporaneamente**: si scompone il moto lungo gli assi e si applicano le leggi del [[Moti particolari|moto uniforme]] e del [[Moti particolari|moto uniformemente accelerato]].

- Lungo $x$: $a_x=0$, quindi $v_x$ è costante.
- Lungo $y$: $a_y=-g$, quindi $v_y$ varia linearmente nel tempo.
- L'istante del punto più alto si trova imponendo $v_y=0$.
- Il tempo d'arrivo si trova imponendo la **quota finale** in $y(t)$.
- La gittata si ricava poi dalla legge oraria $x(t)$.

Le formule di $t_f$ e $D$ per il ritorno alla quota iniziale sono **casi particolari**, mentre le leggi orarie $x(t)$ e $y(t)$ valgono per qualunque quota iniziale, finché rimangono valide le ipotesi sul moto.
