---
Materia:
  - Fisica
tags:
Link risorse:
Libro:
Imparato: false
Ordine: 8
aliases:
---
## Moto circolare: definizione e grandezze angolari
Un **moto circolare** è un moto la cui traiettoria è una circonferenza di raggio $R$ costante. Non è necessariamente **uniforme**: la velocità scalare può variare nel tempo.
Nel **moto circolare uniforme**, invece, il modulo della velocità rimane costante, ma il vettore velocità cambia continuamente direzione. Per questo l'accelerazione non è nulla, a differenza del [[Moti particolari#Moto rettilineo uniforme|moto rettilineo uniforme]].
Scegliamo un sistema cartesiano con origine al centro della circonferenza, asse $x$ orizzontale e asse $y$ verticale. La distanza del punto dall'origine è sempre:
$$
|\vec r(t)|=R.
$$
Chiamiamo $\theta(t)$ l'**angolo orientato** (in radianti) fra il semiasse positivo delle $x$ e il raggio che congiunge il centro al punto materiale.
![[Moto circolare uniforme-1791289026748.webp|305x267]]
Per convenzione:
- una rotazione **antioraria** corrisponde ad angoli crescenti;
- una rotazione **oraria** corrisponde ad angoli decrescenti.
La **velocità angolare** indica la variazione dell'angolo nell'unità di tempo:
$$
\boxed{\omega(t)=\dot\theta(t)=\frac{d\theta}{dt}}
$$
L'**accelerazione angolare** indica quanto varia la velocità angolare:
$$
\boxed{\alpha(t)=\dot\omega(t)=\ddot\theta(t)=\frac{d^2\theta}{dt^2}}
$$
Le unità comunemente utilizzate sono $[\omega]=\mathrm{rad/s}$ e $[\alpha]=\mathrm{rad/s^2}$. L'angolo espresso in radianti è dimensionalmente adimensionale.
![[Moto circolare-1791269114705.webp]]
### Arco percorso e velocità scalare
L'arco orientato corrispondente a uno spostamento angolare $\Delta\theta$ ha lunghezza con segno $R\Delta\theta$. Se il punto percorre la circonferenza **in senso antiorario senza invertire il verso** e poniamo $s(t_0)=0$, allora lo spazio percorso dall'istante $t_0$ è:
$$
\boxed{s(t)=R[\theta(t)-\theta(t_0)]}.
$$
Nel caso particolare $t_0=0$ e $\theta(0)=0$, la formula diventa $s(t)=R\theta(t)$, come nella dispensa di Marrucci.
Derivando rispetto al tempo otteniamo la **velocità scalare**, cioè il modulo della velocità vettoriale:
$$
\boxed{v(t)=\frac{ds}{dt}=R\omega(t)}\qquad\text{se }\omega(t)\geq0.
$$
In generale, anche quando la rotazione è oraria, la velocità scalare deve essere non negativa:
$$
\boxed{v(t)=|\vec v(t)|=R|\omega(t)|}.
$$
Se il moto inverte il verso, lo spazio effettivamente percorso non coincide con la semplice differenza degli angoli orientati. Si ricava integrando la velocità scalare:
$$
s(t)-s(t_0)=\int_{t_0}^{t}R|\omega(\tau)|\,d\tau.
$$
---
## Vettore posizione e vettore velocità
Dalle relazioni trigonometriche, le coordinate cartesiane del punto sono:
$$
x(t)=R\cos\theta(t),\qquad y(t)=R\sin\theta(t).
$$
Quindi il **vettore posizione** è:
$$
\boxed{\vec r(t)=\begin{pmatrix}R\cos\theta(t)\\R\sin\theta(t)\end{pmatrix}}.
$$
La velocità si ottiene derivando il vettore posizione rispetto al tempo, come nella nota [[Moto in più direzioni]]:
$$
\vec v(t)=\frac{d\vec r(t)}{dt}.
$$
> [!tip] Dimostrazione
> **Dal vettore posizione al vettore velocità.**
>Poiché $R$ è costante, deriviamo separatamente le due componenti utilizzando la regola di derivazione delle funzioni composte:
>$$
>\frac{d}{dt}[R\cos\theta(t)]=-R\sin\theta(t)\,\dot\theta(t)
>$$
>$$
>\frac{d}{dt}[R\sin\theta(t)]=R\cos\theta(t)\,\dot\theta(t).
>$$
>Sostituendo $\dot\theta(t)=\omega(t)$:
>$$
>\vec v(t)=\begin{pmatrix}-R\omega(t)\sin\theta(t)\\R\omega(t)\cos\theta(t)\end{pmatrix}
>$$
>Raccogliendo $R\omega(t)$ otteniamo:
>$$
>\boxed{\vec v(t)=R\omega(t)\begin{pmatrix}-\sin\theta(t)\\\cos\theta(t)\end{pmatrix}}.
>$$

Definiamo il **[[Vettori|versore]] tangente orientato nel verso di $\theta$ crescente**:
$$
\boxed{\hat u_T(t)=\begin{pmatrix}-\sin\theta(t)\\\cos\theta(t)\end{pmatrix}}.
$$
È un versore perché ha modulo $1$. Di conseguenza:
$$
\boxed{\vec v(t)=R\omega(t)\hat u_T(t)}.
$$
Il vettore velocità è sempre tangente alla circonferenza quando è non nullo. Se $\omega>0$, il verso della velocità coincide con $\hat u_T$ e possiamo scrivere anche $\vec v=v\hat u_T$. Se $\omega<0$, invece, la velocità punta nel verso opposto: $\vec v=-v\hat u_T$.
### Versore normale o centripeto
Il **versore normale** (indicato anche con $\hat u_C$) è perpendicolare alla tangente e diretto verso il centro della circonferenza:
$$
\boxed{\hat u_N(t)=\begin{pmatrix}-\cos\theta(t)\\-\sin\theta(t)\end{pmatrix}}.
$$
I versori $\hat u_T$ e $\hat u_N$ sono perpendicolari, perché il loro prodotto scalare è nullo:
$$
\hat u_T\cdot\hat u_N=(-\sin\theta)(-\cos\theta)+(\cos\theta)(-\sin\theta)=0.
$$
Entrambi cambiano direzione mentre il punto si sposta lungo la circonferenza.
---
## Accelerazione nel moto circolare
Per trovare l'accelerazione, deriviamo il vettore velocità:
$$
\vec a(t)=\frac{d\vec v(t)}{dt}.
$$
> [!tip] Dimostrazione
> **Componenti dell'accelerazione.**
>Partiamo da:
>$$
>\vec v(t)=R\omega(t)\begin{pmatrix}-\sin\theta(t)\\\cos\theta(t)\end{pmatrix}.
>$$
>Utilizziamo la **regola del prodotto**: dobbiamo derivare sia $\omega(t)$ sia le funzioni di $\theta(t)$.
>Poiché $\dot\omega=\alpha$ e $\dot\theta=\omega$, le due componenti diventano:
>$$
>a_x=-R\alpha\sin\theta-R\omega^2\cos\theta
>$$
>$$
>a_y=R\alpha\cos\theta-R\omega^2\sin\theta.
>$$
>Raggruppando i termini tangenziali e quelli diretti verso il centro:
>$$
>\vec a=R\alpha\begin{pmatrix}-\sin\theta\\\cos\theta\end{pmatrix}+R\omega^2\begin{pmatrix}-\cos\theta\\-\sin\theta\end{pmatrix}.
>$$
>Riconoscendo i due versori:
>$$
>\boxed{\vec a=R\alpha\,\hat u_T+R\omega^2\,\hat u_N}.
>$$

L'accelerazione comprende **due componenti perpendicolari**:
- **Tangenziale:** descrive la variazione della velocità nella direzione tangente;
- **Normale o centripeta:** descrive il cambiamento di direzione della velocità ed è rivolta verso il centro.
![[Moto circolare uniforme-1791289070200.webp]]
### Accelerazione tangenziale
Rispetto al versore $\hat u_T$ scelto nel verso antiorario, la componente tangenziale con segno è:
$$
\boxed{a_T=R\alpha=R\frac{d\omega}{dt}}.
$$
Se il moto procede nel verso antiorario ($\omega>0$), allora $v=R\omega$ e quindi:
$$
\boxed{a_T=\frac{dv}{dt}=R\alpha}.
$$
Il segno di $a_T$ indica se l'accelerazione è concorde o discorde con $\hat u_T$. Se il punto ruota in senso orario, $R\alpha$ resta la componente lungo $\hat u_T$, ma la derivata della velocità **scalare** è $dv/dt=-R\alpha$ finché $\omega<0$.
### Accelerazione normale o centripeta
La componente normale ha modulo:
$$
\boxed{a_N=R\omega^2}.
$$
Dato che $v=R|\omega|$, si ottiene anche:
$$
\boxed{a_N=\frac{v^2}{R}}.
$$
Questa accelerazione è presente anche con velocità scalare costante: cambia la **direzione** di $\vec v$, non necessariamente il suo modulo.
### Accelerazione totale
Essendo i due versori perpendicolari:
$$
\vec a=a_T\hat u_T+a_N\hat u_N
$$
$$
|\vec a|=\sqrt{a_T^2+a_N^2}.
$$
Quindi:
$$
\boxed{|\vec a|=\sqrt{R^2\alpha^2+R^2\omega^4}}.
$$
Se il moto non cambia verso e utilizziamo la tangente orientata nel senso di percorrenza, la stessa formula si può scrivere:
$$
\boxed{|\vec a|=\sqrt{\left(\frac{dv}{dt}\right)^2+\left(\frac{v^2}{R}\right)^2}}.
$$
---
## Moto circolare uniforme
Il moto è **uniforme** quando la velocità scalare $v$ è costante. Poiché $R$ è fisso, anche il modulo della velocità angolare è costante; in un moto continuo di rotazione in un verso possiamo scrivere $\omega=\text{costante}$ e $\alpha=0$.
Ponendo $t_0=0$, l'angolo segue la legge oraria:
$$
\boxed{\theta(t)=\theta_0+\omega t}.
$$
Nel moto circolare uniforme:
- $v=R|\omega|$ è costante;
- la **direzione** del vettore velocità varia continuamente;
- $a_T=0$;
- $\vec a$ è solo centripeta e ha modulo costante, per $\omega\ne0$:
$$
\boxed{a=a_N=R\omega^2=\frac{v^2}{R}}.
$$
Poiché $\vec r=R(\cos\theta,\sin\theta)$ e il versore centripeto è opposto a quello radiale, vale anche:
$$
\boxed{\vec a(t)=-\omega^2\vec r(t)}.
$$
### Periodo e frequenza
Il **periodo** $T$ è il tempo necessario per completare un giro. La circonferenza ha lunghezza $2\pi R$, dunque:
$$
\boxed{T=\frac{2\pi R}{v}=\frac{2\pi}{|\omega|}}\qquad(\omega\ne0).
$$
La **frequenza** $f$ è il numero di giri per unità di tempo:
$$
\boxed{f=\frac1T=\frac{|\omega|}{2\pi}}.
$$
Le unità di misura sono $[T]=\mathrm{s}$ e $[f]=\mathrm{Hz}=\mathrm{s}^{-1}$. Quindi:
$$
\boxed{|\omega|=2\pi f}.
$$
Se si considera soltanto la rotazione antioraria, $\omega>0$ e il valore assoluto può essere omesso.
> [!example]- Esempio della giostra
>In una giostra rigida, due punti a distanze $R_1$ e $R_2$ dal centro impiegano lo stesso tempo a compiere un giro, quindi hanno la stessa velocità angolare in modulo:
>$$
>|\omega_1|=|\omega_2|.
>$$
>La velocità scalare è però $v=R|\omega|$. Se $R_2>R_1$:
>$$
>\boxed{v_2>v_1}.
>$$
>Anche l'accelerazione centripeta, $a_N=R\omega^2$, è maggiore nel punto più esterno:
>$$
>\boxed{a_{N,2}>a_{N,1}}.
>$$
>**Conclusione:** a parità di velocità angolare, aumentando la distanza dal centro aumentano sia la velocità scalare sia l'accelerazione centripeta.
> [!example]- Esercizio numerico
>Un punto percorre una circonferenza di raggio $R=2\,\mathrm{m}$ con velocità angolare costante $\omega=3\,\mathrm{rad/s}$. Calcoliamo velocità scalare, accelerazione e periodo.
>$$
>v=R\omega=2\cdot3=6\,\mathrm{m/s}
>$$
>$$
>a_N=R\omega^2=2\cdot 3^2=18\,\mathrm{m/s^2}
>$$
>$$
>T=\frac{2\pi}{\omega}=\frac{2\pi}{3}\,\mathrm{s}.
>$$
>Essendo uniforme, l'accelerazione tangenziale è nulla, ma il modulo dell'accelerazione totale è $18\,\mathrm{m/s^2}$.

---
## Collegamento con il moto armonico
Le **proiezioni** di un moto circolare uniforme sugli assi cartesiani descrivono moti armonici; la traiettoria circolare nel suo insieme non è un moto armonico unidimensionale.
Infatti, sostituendo $\theta(t)=\omega t+\theta_0$ nelle coordinate:
$$
\boxed{x(t)=R\cos(\omega t+\theta_0)}
$$
$$
\boxed{y(t)=R\sin(\omega t+\theta_0)}.
$$
Queste sono le leggi orarie di un [[Moti particolari#Moto armonico|moto armonico]] con ampiezza $R$, pulsazione $|\omega|$ e fase iniziale $\theta_0$ (con la convenzione scelta per la funzione trigonometrica).
![[Moto circolare uniforme-1791289048629.webp]]
---
## Coordinate polari e generalizzazione a traiettorie curve
Nel piano, un punto può essere rappresentato con coordinate cartesiane $(x,y)$ oppure **polari** $(r,\theta)$:
$$
x=r\cos\theta,\qquad y=r\sin\theta.
$$
Il moto circolare è il caso particolare in cui $r=R$ è costante: per descrivere la posizione è sufficiente conoscere $\theta(t)$.
### Descrizione intrinseca di una traiettoria
Per una **traiettoria regolare qualsiasi**, la velocità non nulla è tangente alla traiettoria. Indicando con $s(t)$ lo spazio percorso, con $v=ds/dt=|\vec v|$ la velocità scalare e con $\hat u_T$ il versore tangente nel **verso effettivo del moto**, possiamo scrivere:
$$
\boxed{\vec v=v\hat u_T}.
$$
L'accelerazione si scompone in una componente tangenziale e una normale (o centripeta):
$$
\boxed{\vec a=\frac{dv}{dt}\,\hat u_T+\frac{v^2}{\rho}\,\hat u_N},
$$
dove $\rho$ è il **raggio di curvatura** locale. Per una circonferenza di raggio fisso $R$ vale $\rho=R$.
### Cerchio osculatore
Una curva può essere approssimata localmente da un arco di circonferenza. La circonferenza che riproduce la curvatura nel punto considerato è detta **cerchio osculatore**; il suo raggio è $\rho$ e il versore $\hat u_N$ è diretto verso il centro di curvatura.
- Una curva che piega molto ha raggio di curvatura piccolo.
- Una curva poco incurvata ha raggio di curvatura grande.
- In un tratto rettilineo, la curvatura è nulla e la componente normale dell'accelerazione è zero.
La scomposizione permette quindi di distinguere le variazioni del **modulo** della velocità da quelle della sua **direzione**, anche in moti non circolari.
### Collegamento con il moto del proiettile
Anche nel [[Moto del proiettile|moto parabolico]] la velocità è tangente alla traiettoria, mentre l'accelerazione è il vettore gravitazionale verticale:
$$
\vec a=(0,-g).
$$
La stessa accelerazione può essere scomposta, punto per punto, in componenti tangenziale e normale. Le due descrizioni (cartesiana e intrinseca) rappresentano il **medesimo vettore** in basi differenti.
