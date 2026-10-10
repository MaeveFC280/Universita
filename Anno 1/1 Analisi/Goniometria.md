---
Materia:
  - Analisi
Imparato:
tags:
Ordine: 21
---
Le **funzioni trigonometriche** descrivono le coordinate di un punto sulla circonferenza goniometrica e sono esempi importanti di [[Funzioni elementari|funzioni reali]].

## Angoli e circonferenza goniometrica

La **circonferenza goniometrica** ha centro nell'origine e raggio $1$. A un angolo $x$, misurato in **radianti** a partire dal semiasse positivo delle ascisse (verso antiorario positivo), associamo il punto
$$
P=(\cos x,\sin x).
$$
Perciò:
- $\cos x$ è la coordinata orizzontale di $P$;
- $\sin x$ è la coordinata verticale di $P$.

Un giro completo corrisponde a $2\pi$ radianti, cioè $360^\circ$:
$$
\pi\ \text{rad}=180^\circ,\qquad x_{\text{rad}}=x_{\text{gradi}}\frac{\pi}{180}.
$$

Dalla circonferenza unitaria segue l'**identità fondamentale**:
$$
\boxed{\sin^2x+\cos^2x=1.}
$$

| $x$ | $0$ | $\frac\pi6$ | $\frac\pi4$ | $\frac\pi3$ | $\frac\pi2$ |
|---|---|---|---|---|---|
| $\sin x$ | $0$ | $\frac12$ | $\frac{\sqrt2}{2}$ | $\frac{\sqrt3}{2}$ | $1$ |
| $\cos x$ | $1$ | $\frac{\sqrt3}{2}$ | $\frac{\sqrt2}{2}$ | $\frac12$ | $0$ |

## Funzione seno

$$
\sin:\mathbb R\longrightarrow[-1,1],\qquad x\longmapsto\sin x.
$$
- **Dominio:** $\mathbb R$; **immagine:** $[-1,1]$.
- **Periodo fondamentale:** $2\pi$, perché $\sin(x+2\pi)=\sin x$.
- **Dispari:** $\sin(-x)=-\sin x$, dunque il grafico è simmetrico rispetto all'origine.
- **Zeri:** $x=k\pi$, con $k\in\mathbb Z$.
- **Massimi:** valore $1$ per $x=\frac\pi2+2k\pi$.
- **Minimi:** valore $-1$ per $x=\frac{3\pi}{2}+2k\pi$.

Per disegnare il grafico in un periodo basta segnare i punti:
$$
(0,0),\ \left(\frac\pi2,1\right),\ (\pi,0),\ \left(\frac{3\pi}2,-1\right),\ (2\pi,0).
$$
Tra questi punti la curva è continua e si ripete ogni $2\pi$.

## Funzione coseno

$$
\cos:\mathbb R\longrightarrow[-1,1],\qquad x\longmapsto\cos x.
$$
- **Dominio:** $\mathbb R$; **immagine:** $[-1,1]$.
- **Periodo fondamentale:** $2\pi$, perché $\cos(x+2\pi)=\cos x$.
- **Pari:** $\cos(-x)=\cos x$, dunque il grafico è simmetrico rispetto all'asse $y$.
- **Zeri:** $x=\frac\pi2+k\pi$, con $k\in\mathbb Z$.
- **Massimi:** valore $1$ per $x=2k\pi$.
- **Minimi:** valore $-1$ per $x=\pi+2k\pi$.

Punti caratteristici del grafico:
$$
(0,1),\ \left(\frac\pi2,0\right),\ (\pi,-1),\ \left(\frac{3\pi}2,0\right),\ (2\pi,1).
$$

## Funzione tangente

La tangente è definita come rapporto tra seno e coseno:
$$
\boxed{\tan x=\frac{\sin x}{\cos x}}
$$
soltanto dove $\cos x\ne0$.

$$
\tan:\mathbb R\setminus\left\{\frac\pi2+k\pi\mid k\in\mathbb Z\right\}\longrightarrow\mathbb R.
$$
- **Dominio:** tutti i reali tranne $\frac\pi2+k\pi$.
- **Immagine:** $\mathbb R$.
- **Periodo fondamentale:** $\pi$, perché $\tan(x+\pi)=\tan x$.
- **Dispari:** $\tan(-x)=-\tan x$.
- **Zeri:** $x=k\pi$.
- È **strettamente crescente** in ciascun intervallo $\left(-\frac\pi2+k\pi,\frac\pi2+k\pi\right)$.
- Il grafico presenta **asintoti verticali** nelle rette $x=\frac\pi2+k\pi$.

>[!warning] Attenzione
>La tangente non è definita quando $\cos x=0$. Non bisogna includere tali valori quando si risolvono equazioni o disequazioni.

## Formule di addizione, sottrazione e duplicazione

Per ogni $\alpha,\beta\in\mathbb R$:
$$
\boxed{\sin(\alpha\pm\beta)=\sin\alpha\cos\beta\pm\cos\alpha\sin\beta}
$$
$$
\boxed{\cos(\alpha\pm\beta)=\cos\alpha\cos\beta\mp\sin\alpha\sin\beta}
$$

>[!warning] Attenzione ai segni
>Nella formula del **coseno**, se dentro la parentesi c'è $+$, fra i prodotti compare $-$; se c'è $-$, fra i prodotti compare $+$.

Ponendo $\beta=\alpha$:
$$
\boxed{\sin(2\alpha)=2\sin\alpha\cos\alpha}
$$
$$
\boxed{\cos(2\alpha)=\cos^2\alpha-\sin^2\alpha=2\cos^2\alpha-1=1-2\sin^2\alpha}
$$

## Funzioni trigonometriche inverse

Seno e coseno **non sono iniettivi su tutto $\mathbb R$**, perché sono periodici. Per definirne l'inversa bisogna prima **restringere il dominio** a un intervallo nel quale la funzione sia biettiva sulla propria immagine.

### Arcoseno

Restringiamo il seno a $\left[-\frac\pi2,\frac\pi2\right]$, dove è strettamente crescente e assume tutti i valori di $[-1,1]$:
$$
f:\left[-\frac\pi2,\frac\pi2\right]\longrightarrow[-1,1],\qquad f(x)=\sin x.
$$
La sua inversa è l'**arcoseno**:
$$
\boxed{\arcsin:[-1,1]\longrightarrow\left[-\frac\pi2,\frac\pi2\right]}.
$$
- **Dominio:** $[-1,1]$; **immagine:** $\left[-\frac\pi2,\frac\pi2\right]$.
- È **strettamente crescente** e **dispari**.
- Il grafico si ottiene riflettendo quello del seno ristretto rispetto alla retta $y=x$.

Per la definizione di funzione inversa:
$$
\boxed{\sin(\arcsin x)=x\quad\forall x\in[-1,1]}
$$
$$
\boxed{\arcsin(\sin x)=x\quad\forall x\in\left[-\frac\pi2,\frac\pi2\right]}.
$$

>[!example] Esempi
>$\arcsin\left(\frac12\right)=\frac\pi6$ e $\arcsin(-1)=-\frac\pi2$.
>Invece $\arcsin(\sin\pi)=0$, **non** $\pi$: l'identità $\arcsin(\sin x)=x$ non vale fuori dall'intervallo scelto.

### Arcocoseno

Restringiamo il coseno a $[0,\pi]$, dove è strettamente decrescente e assume tutti i valori di $[-1,1]$:
$$
g:[0,\pi]\longrightarrow[-1,1],\qquad g(x)=\cos x.
$$
La sua inversa è l'**arcocoseno**:
$$
\boxed{\arccos:[-1,1]\longrightarrow[0,\pi]}.
$$
- **Dominio:** $[-1,1]$; **immagine:** $[0,\pi]$.
- È **strettamente decrescente**.
- Il grafico è il riflesso del coseno ristretto a $[0,\pi]$ rispetto a $y=x$.

Valgono:
$$
\boxed{\cos(\arccos x)=x\quad\forall x\in[-1,1]}
$$
$$
\boxed{\arccos(\cos x)=x\quad\forall x\in[0,\pi]}.
$$

>[!example] Esempi
>$\arccos(1)=0$, $\arccos(0)=\frac\pi2$ e $\arccos(-1)=\pi$.
>Invece $\arccos(\cos(2\pi))=0$, **non** $2\pi$.

### Arcotangente

La tangente è strettamente crescente e biettiva se ristretta all'intervallo $\left(-\frac\pi2,\frac\pi2\right)$:
$$
h:\left(-\frac\pi2,\frac\pi2\right)\longrightarrow\mathbb R,\qquad h(x)=\tan x.
$$
La sua inversa è l'**arcotangente**:
$$
\boxed{\arctan:\mathbb R\longrightarrow\left(-\frac\pi2,\frac\pi2\right)}.
$$
- **Dominio:** $\mathbb R$; **immagine:** $\left(-\frac\pi2,\frac\pi2\right)$.
- È **strettamente crescente** e **dispari**.
- Il grafico passa per $(0,0)$ e ha asintoti orizzontali $y=\pm\frac\pi2$.

Valgono:
$$
\boxed{\tan(\arctan x)=x\quad\forall x\in\mathbb R}
$$
$$
\boxed{\arctan(\tan x)=x\quad\forall x\in\left(-\frac\pi2,\frac\pi2\right)}.
$$

>[!example] Esempi
>$\arctan(0)=0$, $\arctan(1)=\frac\pi4$, $\arctan(-1)=-\frac\pi4$.
>Non si raggiungono mai i valori $\pm\frac\pi2$.

## Domini di funzioni composte con le inverse

Quando compare $\arcsin(f(x))$ oppure $\arccos(f(x))$, l'**argomento** deve appartenere a $[-1,1]$:
$$
-1\le f(x)\le1.
$$
Per $\arctan(f(x))$ non esistono vincoli aggiuntivi sul valore dell'argomento: basta che $f(x)$ sia definita.

>[!example]- Dominio di $\arcsin(2x-1)$
>Imponiamo:
>$$
>-1\le2x-1\le1
>$$
>$$
>0\le2x\le2\iff 0\le x\le1.
>$$
>Quindi:
>$$
>\boxed{D=[0,1]}.
>$$

## Equazioni e disequazioni trigonometriche

La **periodicità** permette di passare dalle soluzioni in un periodo a tutte le soluzioni reali. Occorre distinguere gli intervalli in cui seno, coseno e tangente sono positivi o negativi.

>[!example]- Disequazione $\sin x\ge\frac12$
>In $[0,2\pi)$ il seno vale $\frac12$ nei punti $\frac\pi6$ e $\frac{5\pi}6$; fra questi due angoli è maggiore o uguale a $\frac12$.
>Considerando tutti i periodi:
>$$
>\boxed{x\in\left[\frac\pi6+2k\pi,\frac{5\pi}6+2k\pi\right],\quad k\in\mathbb Z.}
>$$

>[!example]- Disequazione $\cos x\le0$
>Il coseno è non positivo nel secondo e nel terzo quadrante (compresi gli angoli in cui è nullo):
>$$
>\boxed{x\in\left[\frac\pi2+2k\pi,\frac{3\pi}2+2k\pi\right],\quad k\in\mathbb Z.}
>$$

>[!example]- Disequazione $\tan x<1$
>In ogni intervallo $\left(-\frac\pi2+k\pi,\frac\pi2+k\pi\right)$ la tangente è strettamente crescente e vale $1$ per $x=\frac\pi4+k\pi$.
>Pertanto:
>$$
>\boxed{x\in\left(-\frac\pi2+k\pi,\frac\pi4+k\pi\right),\quad k\in\mathbb Z.}
>$$
>Gli estremi sono esclusi: a sinistra la tangente non esiste, a destra la disequazione è stretta.

