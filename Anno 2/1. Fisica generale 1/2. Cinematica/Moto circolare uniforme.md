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
Sappiamo che il vettore velocità corrisponde a $\vec v(t)=\frac{d\vec r}{dt}$, e  l'accelerazione è $\vec a(t)=\frac{d\vec v}{dt}=\frac{d^2\vec r}{dt^2}$.
Nel **moto rettilineo uniforme** il vettore velocità è costante, quindi:

$$  
\vec a=0  
$$

Nel moto circolare, invece, anche se il **modulo della velocità** rimane costante, il vettore velocità cambia continuamente direzione. 


Consideriamo un punto materiale che si muove lungo una circonferenza di raggio $R$.

Chiamiamo $\theta (t)$ l’angolo (in radianti) che descrive la posizione del punto materiale sulla circonferenza in funzione del tempo ed il raggio.
Lo spazio percorso (lunghezza arco) e la velocità scalare sono quindi 
le seguenti:




$$  
|\vec r|=R=\text{costante}  
$$
$$
|\vec{v}|=\text{costante}
$$
$$
\vec{ v} \text{ cambia per seguire traiettoria}
$$

La posizione del punto può essere descritta tramite l'angolo $\theta(t)$ misurato rispetto all'asse $x$.

![[Moto circolare uniforme-1791289026748.webp|305x267]]

Per convenzione:
- rotazione **antioraria** $\rightarrow \omega>0$;
- rotazione **oraria** $\rightarrow \omega<0$.

![[Moto circolare-1791269114705.webp]]

Nel sistema cartesiano la posizione può essere scritta come:
$$  
x(t)=R\cos\theta(t)  
$$
$$  
y(t)=R\sin\theta(t)  
$$

quindi:

$$  \boxed{
\vec r(t)=  
\begin{pmatrix}  
R\cos\theta(t)\  
R\sin\theta(t)  
\end{pmatrix}  }
$$

Lo spazio percorso lungo la circonferenza è:

$$  
s(t)=R\theta(t)  
$$

dove $\theta$ deve essere espresso in **radianti**.

Quindi angolo e spazio percorso sono legati da $s=R\theta$

---
## Velocità angolare

Definiamo la **velocità angolare**:

$$  
\boxed{\omega(t)=\frac{d\theta}{dt}}  
$$

La sua unità di misura sono i $\text{rad/s}$

Dato che:

$$  
s(t)=R\theta(t)  
$$

derivando rispetto al tempo otteniamo:

$$  
v(t)=\frac{ds}{dt}  
$$

quindi:

$$  
v(t)=R\frac{d\theta}{dt}  
$$

e quindi:

$$  
\boxed{v(t)=R\omega(t)}  
$$

Questa è la relazione tra **velocità tangenziale** e **velocità angolare**.

---

# Vettore velocità

Partiamo da:

$$  
\vec r(t)=  
\begin{pmatrix}  
R\cos\theta(t)\  
R\sin\theta(t)  
\end{pmatrix}  
$$

Derivando rispetto al tempo:

$$  
\vec v(t)=\frac{d\vec r}{dt}  
$$

otteniamo:

$$  
\vec v(t)=  
\begin{pmatrix}  
-R\sin\theta(t)\frac{d\theta}{dt}\  
R\cos\theta(t)\frac{d\theta}{dt}  
\end{pmatrix}  
$$

Poiché:

$$  
\omega(t)=\frac{d\theta}{dt}  
$$

si ha:

$$  
\vec v(t)=  
R\omega(t)  
\begin{pmatrix}  
-\sin\theta(t)\  
\cos\theta(t)  
\end{pmatrix}  
$$

Definiamo il **versore tangente**:

$$  
\boxed{  
\hat u_T=  
\begin{pmatrix}  
-\sin\theta\  
\cos\theta  
\end{pmatrix}  
}  
$$

Quindi:

$$  
\boxed{\vec v=v\hat u_T}  
$$

e, nel moto circolare:

$$  
\boxed{\vec v=R\omega\hat u_T}  
$$

La velocità è quindi sempre **tangente alla traiettoria**.

---

# Versore normale

Oltre al versore tangente $\hat u_T$, introduciamo il **versore normale** $\hat u_N$.

Il versore normale punta verso il **centro della circonferenza**:

$$  
\boxed{  
\hat u_N=  
\begin{pmatrix}  
-\cos\theta\  
-\sin\theta  
\end{pmatrix}  
}  
$$

Quindi:

- $\hat u_T$ è tangente alla traiettoria;
    
- $\hat u_N$ è perpendicolare alla traiettoria e punta verso il centro.
    

I due versori cambiano continuamente direzione durante il moto.

---

# Accelerazione angolare

Se la velocità angolare cambia nel tempo definiamo l'**accelerazione angolare**:

$$  
\boxed{\alpha(t)=\frac{d\omega}{dt}}  
$$

Poiché:

$$  
\omega=\frac{d\theta}{dt}  
$$

si ha anche:

$$  
\boxed{\alpha(t)=\frac{d^2\theta}{dt^2}}  
$$

L'unità di misura è:

$$  
[\alpha]=\text{rad/s}^2  
$$

![[Moto circolare uniforme-1791289070200.webp]]

---

# Accelerazione nel moto circolare

La velocità è:

$$  
\vec v=  
R\omega  
\begin{pmatrix}  
-\sin\theta\  
\cos\theta  
\end{pmatrix}  
$$

Derivandola rispetto al tempo si ottiene:

$$  
\vec a=  
R\alpha  
\begin{pmatrix}  
-\sin\theta\  
\cos\theta  
\end{pmatrix}  
+  
R\omega^2  
\begin{pmatrix}  
-\cos\theta\  
-\sin\theta  
\end{pmatrix}  
$$

Riconosciamo i versori $\hat u_T$ e $\hat u_N$:

$$  
\boxed{\vec a=R\alpha,\hat u_T+R\omega^2,\hat u_N}  
$$

L'accelerazione possiede quindi **due componenti**:

- accelerazione tangenziale;
    
- accelerazione normale o centripeta.
    

---

## Accelerazione tangenziale

La componente tangenziale è:

$$  
\boxed{a_T=R\alpha}  
$$

È diretta lungo $\hat u_T$.

Compare quando cambia il **modulo della velocità**.

Infatti:

$$  
v=R\omega  
$$

Derivando:

$$  
\frac{dv}{dt}=R\frac{d\omega}{dt}  
$$

quindi:

$$  
\boxed{a_T=\frac{dv}{dt}=R\alpha}  
$$

L'accelerazione tangenziale descrive quindi quanto rapidamente cambia il **modulo** della velocità.

---

## Accelerazione normale o centripeta

La componente normale è:

$$  
\boxed{a_N=R\omega^2}  
$$

ed è diretta verso il **centro della circonferenza**.

Dato che:

$$  
v=R\omega  
$$

abbiamo:

$$  
\omega=\frac{v}{R}  
$$

quindi:

$$  
a_N=R\left(\frac{v}{R}\right)^2  
$$

e quindi:

$$  
\boxed{a_N=\frac{v^2}{R}}  
$$

Questa accelerazione esiste anche quando il modulo della velocità rimane costante, perché cambia la **direzione** del vettore velocità.

---

# Accelerazione totale

Poiché $\hat u_T$ e $\hat u_N$ sono perpendicolari:

$$  
\vec a=a_T\hat u_T+a_N\hat u_N  
$$

Il modulo dell'accelerazione totale è:

$$  
|\vec a|=\sqrt{a_T^2+a_N^2}  
$$

quindi:

$$  
\boxed{  
|\vec a|=  
\sqrt{R^2\alpha^2+R^2\omega^4}  
}  
$$

oppure:

$$  
\boxed{  
|\vec a|=  
\sqrt{  
\left(\frac{dv}{dt}\right)^2+  
\left(\frac{v^2}{R}\right)^2  
}  
}  
$$

---

# Moto circolare uniforme

Nel **moto circolare uniforme** il modulo della velocità è costante:

$$  
v=\text{costante}  
$$

Di conseguenza anche la velocità angolare è costante:

$$  
\omega=\text{costante}  
$$

Quindi:

$$  
\alpha=0  
$$

e:

$$  
a_T=0  
$$

Rimane però l'accelerazione centripeta:

$$  
\boxed{\vec a=R\omega^2\hat u_N}  
$$

con modulo:

$$  
\boxed{a_N=R\omega^2=\frac{v^2}{R}}  
$$

Quindi nel moto circolare uniforme:

- il **modulo** della velocità è costante;
    
- la **direzione** della velocità cambia continuamente;
    
- l'accelerazione tangenziale è nulla;
    
- esiste sempre l'accelerazione centripeta.
    

![[Moto circolare-1791271490507.webp]]

---

# Periodo

Il moto circolare uniforme è un **moto periodico**, perché dopo un certo intervallo di tempo il punto ritorna nella stessa posizione.

La lunghezza della circonferenza è:

$$  
2\pi R  
$$

Definiamo **periodo $T$** il tempo necessario per compiere un giro completo.

Poiché:

$$  
v=\frac{2\pi R}{T}  
$$

otteniamo:

$$  
\boxed{T=\frac{2\pi R}{v}}  
$$

Utilizzando:

$$  
v=R\omega  
$$

si ha:

$$  
T=\frac{2\pi R}{R\omega}  
$$

quindi:

$$  
\boxed{T=\frac{2\pi}{\omega}}  
$$

---

# Frequenza

La **frequenza** indica quanti giri vengono compiuti in un secondo.

$$  
\boxed{f=\frac{1}{T}}  
$$

L'unità di misura è l'**hertz**:

$$  
[f]=\text{Hz}=\text{s}^{-1}  
$$

Da:

$$  
T=\frac{2\pi}{\omega}  
$$

otteniamo:

$$  
\boxed{\omega=\frac{2\pi}{T}=2\pi f}  
$$

Quindi:

$$  
\boxed{f=\frac1T}  
$$

$$  
\boxed{\omega=2\pi f}  
$$

---

# Esempio: giostra

Consideriamo una giostra rigida che ruota.

Due punti posti a distanze diverse dal centro hanno la **stessa velocità angolare**:

$$  
\omega_1=\omega_2  
$$

perché compiono un giro nello stesso tempo.

La velocità tangenziale però è:

$$  
v=R\omega  
$$

Quindi, a parità di $\omega$, chi si trova più lontano dal centro ha velocità tangenziale maggiore.

Se:

$$  
R_2>R_1  
$$

allora:

$$  
v_2>v_1  
$$

Anche l'accelerazione centripeta:

$$  
a_N=R\omega^2  
$$

è maggiore per chi si trova più lontano dal centro.

Quindi:

$$  
\boxed{  
R\uparrow \quad\Rightarrow\quad v\uparrow,\quad a_N\uparrow  
}  
$$

a parità di $\omega$.

---

# Moto circolare uniforme e moto armonico

Il moto circolare uniforme **non è un moto armonico**.

La **proiezione** del moto circolare uniforme su uno degli assi, invece, è un moto armonico.

Nel moto circolare uniforme:

$$  
\theta(t)=\omega t+\phi  
$$

quindi:

$$  
x(t)=R\cos(\omega t+\phi)  
$$

e:

$$  
y(t)=R\sin(\omega t+\phi)  
$$

Il moto armonico può quindi essere scritto nella forma:

$$  
\boxed{x(t)=A\sin(\omega t+\phi)}  
$$

oppure:

$$  
\boxed{x(t)=A\cos(\omega t+\phi)}  
$$

dove:

- $A$ = **ampiezza**;
    
- $\omega$ = **pulsazione**;
    
- $\phi$ = **fase iniziale**;
    
- $\Phi(t)=\omega t+\phi$ = **fase**.


![[Moto circolare uniforme-1791289048629.webp]]

---

# Coordinate cartesiane e coordinate polari

Nel piano cartesiano descriviamo la posizione mediante:

$$  
\vec r=(x,y)  
$$

La velocità è:

$$  
\vec v=  
\left(  
\frac{dx}{dt},  
\frac{dy}{dt}  
\right)  
$$

e l'accelerazione:

$$  
\vec a=  
\left(  
\frac{d^2x}{dt^2},  
\frac{d^2y}{dt^2}  
\right)  
$$

Nel sistema di coordinate polari la posizione viene invece descritta mediante:

$$  
(r,\theta)  
$$

con:

$$  
x=r\cos\theta  
$$

$$  
y=r\sin\theta  
$$

Nel caso particolare del moto circolare:

$$  
r=R=\text{costante}  
$$

quindi basta conoscere $\theta(t)$ per determinare la posizione del punto.

---

# Descrizione intrinseca della traiettoria

Il ragionamento fatto per la circonferenza può essere esteso a una traiettoria generica.

In ogni punto della traiettoria possiamo definire:

- un **versore tangente** $\hat u_T$;
    
- un **versore normale** $\hat u_N$.
    

La velocità è sempre tangente alla traiettoria:

$$  
\boxed{\vec v=v\hat u_T}  
$$

L'accelerazione può essere scomposta come:

$$  
\boxed{\vec a=a_T\hat u_T+a_N\hat u_N}  
$$

dove:

$$  
\boxed{a_T=\frac{dv}{dt}}  
$$

e:

$$  
\boxed{a_N=\frac{v^2}{R}}  
$$

In questo caso $R$ non è necessariamente il raggio di una vera circonferenza percorsa dal corpo, ma rappresenta il **raggio di curvatura** della traiettoria in quel punto.

---

# Cerchio osculatore

Una traiettoria generica può essere approssimata **localmente** mediante una circonferenza.

In ogni punto possiamo immaginare una circonferenza che segue il più possibile la curvatura della traiettoria.

Questa circonferenza prende il nome di **cerchio osculatore**.

Il suo raggio è detto:

$$  
R=\text{raggio di curvatura}  
$$

Più la traiettoria curva rapidamente, più piccolo è $R$.

Più la traiettoria è simile a una retta, più grande è $R$.

Il versore normale $\hat u_N$ punta verso il centro del cerchio osculatore.

Per questo motivo anche in una traiettoria generica possiamo scrivere:

$$  
\boxed{a_N=\frac{v^2}{R}}  
$$

L'accelerazione normale descrive quindi il cambiamento della **direzione** della velocità.

---

# Collegamento con il moto parabolico

Anche nel moto di un proiettile la velocità è sempre **tangente alla traiettoria**.

Nel sistema cartesiano possiamo descrivere la velocità tramite:

$$  
\vec v=(v_x,v_y)  
$$

e l'accelerazione tramite:

$$  
\vec a=(a_x,a_y)  
$$

Possiamo però anche utilizzare, istante per istante, il sistema formato dai versori:

$$  
\hat u_T,\hat u_N  
$$

scrivendo:

$$  
\vec v=v\hat u_T  
$$

e:

$$  
\vec a=a_T\hat u_T+a_N\hat u_N  
$$

Questa descrizione segue direttamente la traiettoria, invece di utilizzare assi cartesiani fissi $x$ e $y$.

---

# Formule fondamentali

Velocità:

$$  
\boxed{\vec v=\frac{d\vec r}{dt}}  
$$

Accelerazione:

$$  
\boxed{\vec a=\frac{d\vec v}{dt}=\frac{d^2\vec r}{dt^2}}  
$$

Spazio percorso sulla circonferenza:

$$  
\boxed{s=R\theta}  
$$

Velocità angolare:

$$  
\boxed{\omega=\frac{d\theta}{dt}}  
$$

Velocità tangenziale:

$$  
\boxed{v=R\omega}  
$$

Accelerazione angolare:

$$  
\boxed{\alpha=\frac{d\omega}{dt}=\frac{d^2\theta}{dt^2}}  
$$

Accelerazione tangenziale:

$$  
\boxed{a_T=R\alpha=\frac{dv}{dt}}  
$$

Accelerazione normale:

$$  
\boxed{a_N=R\omega^2=\frac{v^2}{R}}  
$$

Accelerazione totale:

$$  
\boxed{\vec a=a_T\hat u_T+a_N\hat u_N}  
$$

Nel **moto circolare uniforme**:

$$  
\boxed{\alpha=0}  
$$

$$  
\boxed{a_T=0}  
$$

$$  
\boxed{a=a_N=R\omega^2=\frac{v^2}{R}}  
$$

Periodo:

$$  
\boxed{T=\frac{2\pi}{\omega}}  
$$

Frequenza:

$$  
\boxed{f=\frac1T}  
$$

Relazione tra pulsazione e frequenza:

$$  
\boxed{\omega=2\pi f}  
$$