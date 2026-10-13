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
Un'importante applicazione del [[Moto in più direzioni]] è il **moto di un proiettile**.
Trascurando la resistenza dell'aria, sul corpo agisce solamente l'accelerazione di gravità.
La traiettoria risultante è un **ramo di parabola**.
Il punto fondamentale è che possiamo studiare separatamente il movimento lungo i due assi.

---
## Velocità iniziale
Supponiamo che il corpo venga lanciato con velocità iniziale $\vec v_0$ che forma un angolo $\alpha$ con l'orizzontale.

La velocità viene scomposta nelle sue componenti:

$$  
\boxed{v_{0x}=v_0\cos\alpha}  
$$

$$  
\boxed{v_{0y}=v_0\sin\alpha}  
$$

Quindi:

$$  
\boxed{  
\vec v_0=  
(v_0\cos\alpha,v_0\sin\alpha)  
}  
$$

La componente $v_{0x}$ determina il movimento orizzontale.

La componente $v_{0y}$ determina inizialmente il movimento verticale.

---
## Movimento orizzontale
Lungo l'asse $x$, trascurando l'attrito dell'aria:

$$  
a_x=0  
$$

Di conseguenza:

$$  
v_x=v_{0x}  
$$

è costante.

Quindi il moto lungo $x$ è un **moto rettilineo uniforme**:

$$  
\boxed{x(t)=x_0+v_0\cos\alpha,t}  
$$

---
## Movimento verticale
Lungo l'asse $y$ agisce invece la gravità:

$$  
a_y=-g  
$$

se scegliamo verso l'alto come verso positivo.

La velocità verticale è quindi:

$$  
\boxed{v_y(t)=v_0\sin\alpha-gt}  
$$

e la posizione verticale è:

$$  
\boxed{  
y(t)=y_0+v_0\sin\alpha,t-\frac12gt^2  
}  
$$

Quindi:

- lungo $x$ abbiamo un moto uniforme;
    
- lungo $y$ abbiamo un moto uniformemente accelerato.
    

La combinazione dei due movimenti produce la traiettoria parabolica.

---
## Punto più alto
Nel punto più alto della traiettoria la componente verticale della velocità si annulla:

$$  
v_y=0  
$$

quindi:

$$  
v_0\sin\alpha-gt=0  
$$

da cui:

$$  
\boxed{  
t_{\text{max}}=  
\frac{v_0\sin\alpha}{g}  
}  
$$

Attenzione: nel punto più alto **non è necessariamente nulla tutta la velocità**.

Infatti:

$$  
v_y=0  
$$

ma normalmente:

$$  
v_x\neq0.  
$$

Il corpo continua quindi a muoversi orizzontalmente.

---
## Gittata

La **gittata** è la distanza orizzontale percorsa dal proiettile prima di raggiungere il punto finale della traiettoria.

Indicandola con $D$:

$$  
D=x_f-x_0  
$$

Il suo valore dipende da:

- modulo della velocità iniziale $v_0$;
    
- angolo di lancio $\alpha$;
    
- accelerazione di gravità $g$;
    
- eventuale differenza tra altezza iniziale e altezza finale.
    

Nel caso particolare in cui il proiettile parte e arriva alla stessa altezza:

$$  
\boxed{  
D=\frac{v_0^2\sin(2\alpha)}{g}  
}  
$$

---
## Idea fondamentale

Nel moto in più dimensioni non bisogna cercare di analizzare tutto contemporaneamente.

Si scompone il moto lungo ciascun asse:

$$  
\boxed{  
\vec r=(x,y)  
}  
$$

$$  
\boxed{  
\vec v=(v_x,v_y)  
}  
$$

$$  
\boxed{  
\vec a=(a_x,a_y)  
}  
$$

e si studia separatamente ciò che accade lungo $x$ e lungo $y$.

Per trovare le componenti di un vettore a partire dal suo modulo e da un angolo si utilizzano seno e coseno.

Se l'angolo $\alpha$ è misurato rispetto all'asse $x$:

$$  
\boxed{x=r\cos\alpha}  
$$

$$  
\boxed{y=r\sin\alpha}  
$$

La regola più importante da ricordare è:

$$  
\boxed{  
\cos\alpha=  
\frac{\text{cateto adiacente}}{\text{ipotenusa}}  
}  
$$

$$  
\boxed{  
\sin\alpha=  
\frac{\text{cateto opposto}}{\text{ipotenusa}}  
}  
$$

Da queste due definizioni puoi sempre ricostruire le formule senza doverle imparare a memoria.