---
Materia:
  - Geometria
  - Algebra Lineare
tags:
Link risorse:
Libro:
Imparato: false
Ordine: 23
aliases:
---
Sia $(V,K,+,\cdot)$ uno [[Spazi e sottospazi vettoriali|spazio vettoriale]] sul campo $K$. Indichiamo con $0_V$ il vettore nullo. Per semplicità scriveremo $u+v$ per la somma di vettori e $\alpha u$ per il prodotto di uno scalare per un vettore.
## Combinazioni lineari
> [!info] Definizione
> Siano $u_1,\ldots,u_t\in V$ e $\alpha_1,\ldots,\alpha_t\in K$, con $t\geq1$. Si dice **combinazione lineare** dei vettori $u_1,\ldots,u_t$ il vettore
> $$
> \boxed{\alpha_1u_1+\cdots+\alpha_tu_t=\sum_{i=1}^t\alpha_iu_i.}
> $$
> Gli $\alpha_i$ sono i **coefficienti** (scalari) della combinazione lineare. È ammesso che uno scalare sia nullo o che un vettore compaia più volte nella famiglia: in quel caso si possono raccogliere i coefficienti dei vettori uguali.

> [!example]- Esempio
> In $\mathbb R^3$ consideriamo $u_1=(1,0,1)$ e $u_2=(0,1,1)$. Allora
> $$
> 3u_1-u_2=3(1,0,1)-(0,1,1)=(3,-1,2).
> $$
> Quindi $(3,-1,2)$ è una combinazione lineare di $u_1$ e $u_2$.

## Chiusura lineare
> [!info] Definizione
> Sia $X\subseteq V$. La **chiusura lineare** di $X$ (anche *spazio generato da $X$*) è l'insieme di tutte le combinazioni lineari **finite** di vettori di $X$. Si indica con $L(X)$ oppure $\langle X\rangle$:
> $$
> \boxed{L(X)=\begin{cases}
> \{0_V\}, & X=\varnothing,\\[2pt]
> \left\{\displaystyle\sum_{i=1}^t\alpha_iu_i\ \middle|\ t\geq1,\ u_i\in X,\ \alpha_i\in K\right\}, & X\neq\varnothing.
> \end{cases}}
> $$
> Anche se $X$ contiene infiniti vettori, una singola combinazione lineare ne coinvolge sempre **un numero finito**. La convenzione $L(\varnothing)=\{0_V\}$ corrisponde alla somma vuota.

> [!example]- Esempio: piano generato da due vettori
> Sia $X=\{(1,0,1),(0,1,1)\}\subseteq\mathbb R^3$. Allora
> $$
> \begin{aligned}
> L(X)&=\{\alpha(1,0,1)+\beta(0,1,1)\mid\alpha,\beta\in\mathbb R\}\\
> &=\{(\alpha,\beta,\alpha+\beta)\mid\alpha,\beta\in\mathbb R\}\\
> &=\{(x,y,z)\in\mathbb R^3\mid z=x+y\}.
> \end{aligned}
> $$
> È un piano passante per l'origine, **non** tutto $\mathbb R^3$. Ad esempio $(3,-1,2)\in L(X)$, mentre $(1,1,1)\notin L(X)$ perché $1\neq1+1$.

### Proprietà della chiusura lineare
> [!info] Proposizione
> Per ogni $X\subseteq V$ valgono:
> 1. $X\subseteq L(X)$.
> 2. $L(X)$ è un [[Sottospazi vettoriali|sottospazio vettoriale]] di $V$.
> 3. Se $W$ è un sottospazio di $V$ tale che $X\subseteq W$, allora $L(X)\subseteq W$.
> In conclusione, **$L(X)$ è il più piccolo sottospazio vettoriale di $V$ che contiene $X$**, dove «più piccolo» si riferisce all'inclusione.

> [!tip] Dimostrazione
> **1.** Se $X=\varnothing$, l'inclusione è immediata. Altrimenti, preso un qualsiasi $u\in X$, si ha $u=1\cdot u\in L(X)$, essendo una combinazione lineare di un elemento di $X$. Quindi $X\subseteq L(X)$.
> **2.** Se $X=\varnothing$, $L(X)=\{0_V\}$ è un sottospazio. Supponiamo $X\neq\varnothing$. Innanzitutto $0_V\in L(X)$: basta scegliere un vettore $u\in X$ e il coefficiente $0$.
> Siano ora $v,w\in L(X)$. Per definizione esistono vettori $u_1,\ldots,u_t,u'_1,\ldots,u'_s\in X$ e coefficienti $\alpha_i,\beta_j\in K$ tali che
> $$
> v=\sum_{i=1}^t\alpha_i u_i,\qquad w=\sum_{j=1}^s\beta_j u'_j.
> $$
> La loro somma è
> $$
> v+w=\sum_{i=1}^t\alpha_i u_i+\sum_{j=1}^s\beta_j u'_j\in L(X),
> $$
> perché è ancora una combinazione lineare finita di elementi di $X$. Inoltre, per ogni $\lambda\in K$,
> $$
> \lambda v=\lambda\sum_{i=1}^t\alpha_i u_i=\sum_{i=1}^t(\lambda\alpha_i)u_i\in L(X).
> $$
> Per il [[Sottospazi vettoriali|criterio di sottospazio]], $L(X)$ è un sottospazio di $V$.
> **3.** Sia $W$ un sottospazio con $X\subseteq W$. Se $X=\varnothing$, allora $L(X)=\{0_V\}\subseteq W$. Altrimenti, per ogni $v\in L(X)$ esistono $u_i\in X\subseteq W$ e $\alpha_i\in K$ tali che
> $$
> v=\sum_{i=1}^t\alpha_i u_i.
> $$
> Poiché $W$ è chiuso rispetto alla moltiplicazione per scalari e alla somma, ciascun $\alpha_i u_i\in W$ e anche $v\in W$. Pertanto $L(X)\subseteq W$.

### Quando due insiemi generano lo stesso spazio
> [!info] Proposizione
> Siano $S,T\subseteq V$. Allora
> $$
> \boxed{L(S)=L(T)\iff S\subseteq L(T)\ \text{e}\ T\subseteq L(S).}
> $$
> In pratica, per dimostrare che $S$ e $T$ generano lo stesso spazio basta verificare che **ogni generatore di un insieme** sia combinazione lineare dei vettori dell'altro, e viceversa.

> [!tip] Dimostrazione
> **($\Rightarrow$)** Per la prima proprietà della chiusura lineare, $S\subseteq L(S)=L(T)$ e $T\subseteq L(T)=L(S)$.
> **($\Leftarrow$)** Poiché $L(T)$ è un sottospazio contenente $S$, per la terza proprietà $L(S)\subseteq L(T)$. Analogamente, $T\subseteq L(S)$ implica $L(T)\subseteq L(S)$. Le due inclusioni danno l'uguaglianza.

## Sistemi di generatori
> [!info] Definizione
> Sia $W$ un sottospazio vettoriale di $V$. Un insieme $S\subseteq W$ è un **sistema di generatori** di $W$ se
> $$
> \boxed{L(S)=W.}
> $$
> Equivalentemente, **ogni** vettore di $W$ deve potersi esprimere come combinazione lineare *finita* di elementi di $S$. Non è necessario che tale espressione sia unica: è possibile che ci siano generatori superflui.

> [!info] Definizione: finitamente generato
> Uno spazio vettoriale $W$ si dice **finitamente generato** se ammette almeno un sistema di generatori $S$ con $|S|<+\infty$; anche il sottospazio nullo è finitamente generato, perché $L(\varnothing)=\{0_V\}$.

> [!example]- Esempio: generatori di $\mathbb R^2$
> Sia $S=\{(1,0),(0,1)\}$. Per ogni $(x,y)\in\mathbb R^2$ si ha
> $$
> (x,y)=x(1,0)+y(0,1).
> $$
> Quindi $L(S)=\mathbb R^2$. Anche $T=\{(1,0),(0,1),(1,1)\}$ genera $\mathbb R^2$, ma il terzo vettore è superfluo perché $(1,1)=(1,0)+(0,1)$.

> [!example]- Esempio del tuo appunto: spazio delle matrici
> Lo spazio $M_{m\times n}(K)$ delle [[Matrici|matrici]] $m\times n$ a coefficienti in $K$ è finitamente generato. Per ogni coppia di indici $(i,j)$, sia $E_{ij}$ la matrice con $1$ nella posizione $(i,j)$ e $0$ in tutte le altre.
> Ad esempio, per $m=2$ e $n=2$:
> $$
> E_{11}=\begin{pmatrix}1&0\\0&0\end{pmatrix},\ E_{12}=\begin{pmatrix}0&1\\0&0\end{pmatrix},\ E_{21}=\begin{pmatrix}0&0\\1&0\end{pmatrix},\ E_{22}=\begin{pmatrix}0&0\\0&1\end{pmatrix}.
> $$
> Ogni matrice $A=(a_{ij})\in M_{m\times n}(K)$ si scrive
> $$
> \boxed{A=\sum_{i=1}^{m}\sum_{j=1}^{n}a_{ij}E_{ij}.}
> $$
> Quindi le $mn$ matrici $E_{ij}$ formano un sistema di generatori di $M_{m\times n}(K)$. Sono anche indipendenti: se $\sum_{i,j}\lambda_{ij}E_{ij}=0$, confrontando l'elemento in posizione $(i,j)$ si ottiene $\lambda_{ij}=0$ per ogni coppia $(i,j)$. Pertanto costituiscono una base dello spazio delle matrici.

## Dipendenza e indipendenza lineare
> [!info] Definizione
> Una famiglia $u_1,\ldots,u_t\in V$ è **linearmente indipendente** se l'unica combinazione lineare che dà il vettore nullo è quella con tutti i coefficienti nulli:
> $$
> \boxed{\alpha_1u_1+\cdots+\alpha_tu_t=0_V\ \Longrightarrow\ \alpha_1=\cdots=\alpha_t=0.}
> $$
> È **linearmente dipendente** se esistono $\alpha_1,\ldots,\alpha_t\in K$, **non tutti nulli**, tali che $\alpha_1u_1+\cdots+\alpha_tu_t=0_V$.
> Per un **insieme** $X\subseteq V$, la definizione si applica a ogni scelta **finita di elementi distinti** di $X$. Una famiglia con lo stesso vettore ripetuto è invece automaticamente dipendente, perché $u-u=0_V$.
> Per convenzione $\varnothing$ è linearmente indipendente.

> [!example]- Esempio: due vettori indipendenti
> In $\mathbb R^2$, $u_1=(1,0)$ e $u_2=(0,1)$ sono linearmente indipendenti. Infatti
> $$
> \alpha(1,0)+\beta(0,1)=(0,0)\iff(\alpha,\beta)=(0,0).
> $$

> [!example]- Esempio: due vettori dipendenti
> I vettori $(1,2)$ e $(2,4)$ sono dipendenti, dato che
> $$
> 2(1,2)-(2,4)=(0,0),
> $$
> con coefficienti $(2,-1)$ non entrambi nulli.

### Proprietà immediate
- Un insieme che contiene $0_V$ è **linearmente dipendente**: $1\cdot0_V=0_V$ con coefficiente non nullo.
- Se $X$ è linearmente indipendente, ogni suo sottoinsieme $Y\subseteq X$ è **linearmente indipendente**.
- Se $Y\subseteq X$ e $Y$ è linearmente dipendente, allora anche $X$ è **linearmente dipendente**.
- Due vettori non nulli sono dipendenti esattamente quando uno è multiplo scalare dell'altro.
> [!tip] Dimostrazione
> **Sottoinsieme di un insieme indipendente.** Sia $Y\subseteq X$, con $X$ indipendente. Se $Y$ fosse dipendente, avremmo una combinazione lineare nulla di vettori distinti di $Y$ con coefficienti non tutti nulli. Ma quegli stessi vettori appartengono anche a $X$: avremmo una combinazione lineare non banale nulla di elementi di $X$, contro l'indipendenza di $X$.
> **Sovrainsieme di un insieme dipendente.** Se $Y$ contiene già una combinazione lineare nulla non banale, la stessa combinazione può essere considerata in $X\supseteq Y$.

### Metodo operativo per verificare l'indipendenza
Per verificare se $u_1,\ldots,u_t\in K^n$ sono indipendenti, si imposta l'equazione
$$
\alpha_1u_1+\cdots+\alpha_tu_t=0_V
$$
e si confrontano le componenti. Si ottiene un [[Sistema di equazioni lineari|sistema lineare omogeneo]] nelle incognite $\alpha_1,\ldots,\alpha_t$:
- se ha **solo la soluzione nulla**, i vettori sono indipendenti;
- se ha **anche una soluzione non nulla**, sono dipendenti.
> [!example]- Esempio svolto
> Consideriamo $u_1=(1,2)$ e $u_2=(2,1)$ in $\mathbb R^2$. Dobbiamo risolvere
> $$
> \alpha(1,2)+\beta(2,1)=(0,0)
> \iff\begin{cases}\alpha+2\beta=0\\2\alpha+\beta=0.\end{cases}
> $$
> Dalla prima equazione $\alpha=-2\beta$; sostituendo nella seconda:
> $$
> -4\beta+\beta=0\iff-3\beta=0\iff\beta=0.
> $$
> Ne segue $\alpha=0$. Esiste solo la soluzione nulla, quindi $u_1,u_2$ sono **linearmente indipendenti**.

### Caratterizzazione dei vettori superflui
> [!info] Proposizione
> Per ogni insieme $X\subseteq V$:
> $$
> \boxed{X\text{ è linearmente dipendente}\iff\exists u\in X:\ L(X)=L(X\setminus\{u\}).}
> $$
> Un insieme dipendente contiene dunque un vettore **eliminabile senza modificare lo spazio generato**.

> [!tip] Dimostrazione
> **($\Rightarrow$)** Poiché $X$ è dipendente, esistono vettori distinti $u_1,\ldots,u_t\in X$ e scalari non tutti nulli con
> $$
> \alpha_1u_1+\cdots+\alpha_tu_t=0_V.
> $$
> Riordiniamo gli indici affinché $\alpha_t\neq0$. Siccome $K$ è un campo, $\alpha_t$ ha inverso e possiamo isolare $u_t$:
> $$
> u_t=-\sum_{i=1}^{t-1}\frac{\alpha_i}{\alpha_t}u_i\in L(X\setminus\{u_t\}).
> $$
> Per $t=1$ la somma è vuota e $u_t=0_V$. Tutti gli elementi di $X\setminus\{u_t\}$ sono ovviamente in $L(X\setminus\{u_t\})$, e ora lo è anche $u_t$. Pertanto $X\subseteq L(X\setminus\{u_t\})$. Per la proprietà della chiusura lineare, $L(X)\subseteq L(X\setminus\{u_t\})$. L'inclusione opposta segue da $X\setminus\{u_t\}\subseteq X$.
> **($\Leftarrow$)** Supponiamo che $L(X)=L(X\setminus\{u\})$. Allora $u\in L(X\setminus\{u\})$: se $X\setminus\{u\}=\varnothing$, si ha $u=0_V$, e $X$ è dipendente. Negli altri casi possiamo scrivere, scegliendo $v_i\in X\setminus\{u\}$,
> $$
> u=\beta_1v_1+\cdots+\beta_sv_s.
> $$
> Quindi
> $$
> \beta_1v_1+\cdots+\beta_sv_s-u=0_V.
> $$
> Se qualche $v_i$ compare più volte, ne sommiamo i coefficienti; il coefficiente di $u$ rimane $-1\neq0$. Abbiamo così una combinazione lineare nulla **non banale** di elementi distinti di $X$: $X$ è dipendente.

## Basi
> [!info] Definizione
> Un insieme $B\subseteq V$ si dice **base** dello spazio vettoriale $V$ quando soddisfa **entrambe** le proprietà:
> 1. È un **sistema di generatori**: $L(B)=V$.
> 2. È **linearmente indipendente**.
> In altre parole, una base genera tutto lo spazio senza vettori superflui. La base di $\{0_V\}$ è l'insieme vuoto.

> [!example]- Esempio: base canonica di $K^n$
> La famiglia $e_1=(1,0,\ldots,0),\ldots,e_n=(0,\ldots,0,1)$ è una base di $K^n$. Infatti ogni $x=(x_1,\ldots,x_n)$ è generato dalla combinazione
> $$
> x=x_1e_1+\cdots+x_ne_n,
> $$
> e la relazione $\alpha_1e_1+\cdots+\alpha_ne_n=0$ implica $\alpha_1=\cdots=\alpha_n=0$.

### Una base permette rappresentazioni uniche
> [!info] Proposizione
> Se $B=\{e_1,\ldots,e_n\}$ è una base **finita** di $V$, ogni vettore $v\in V$ può essere scritto **in uno e un solo modo** come
> $$
> \boxed{v=\alpha_1e_1+\cdots+\alpha_ne_n.}
> $$
> Quando si fissa anche l'ordine $(e_1,\ldots,e_n)$, i coefficienti $(\alpha_1,\ldots,\alpha_n)$ sono le **componenti (o coordinate) di $v$ rispetto alla base ordinata**.

> [!tip] Dimostrazione
> L'**esistenza** segue da $L(B)=V$: ogni $v\in V$ è combinazione lineare dei vettori della base.
> Per l'**unicità**, supponiamo che
> $$
> v=\sum_{i=1}^n\alpha_i e_i=\sum_{i=1}^n\beta_i e_i.
> $$
> Sottraendo le due espressioni otteniamo
> $$
> 0_V=\sum_{i=1}^n(\alpha_i-\beta_i)e_i.
> $$
> Poiché la base è linearmente indipendente, $\alpha_i-\beta_i=0$ per ogni $i$, dunque $\alpha_i=\beta_i$ per ogni $i$.

### Teorema di estrazione di una base
> [!info] Teorema
> Se $V$ è **finitamente generato** e $S\subseteq V$ è un suo sistema **finito** di generatori, allora esiste una base $B$ di $V$ con $B\subseteq S$.

> [!tip] Dimostrazione
> Se $S=\varnothing$, allora $V=L(\varnothing)=\{0_V\}$ e $B=\varnothing$ è una base.
> Supponiamo $S\neq\varnothing$. Se $S$ è già indipendente, essendo anche un sistema di generatori, è una base.
> Se invece $S$ è dipendente, per la proposizione sui vettori superflui esiste $u\in S$ tale che
> $$
> L(S\setminus\{u\})=L(S)=V.
> $$
> Eliminiamo $u$ e ripetiamo lo stesso controllo sul sistema rimasto. A ogni eliminazione diminuisce il numero di vettori, ma **non** cambia lo spazio generato. Poiché $S$ è finito, dopo un numero finito di passi otteniamo un insieme indipendente $B\subseteq S$ con $L(B)=V$. Quindi $B$ è una base.

> [!example]- Esempio: estrazione di una base
> Consideriamo $S=\{(1,0),(0,1),(1,1)\}\subseteq\mathbb R^2$.
> $$
> (1,1)=(1,0)+(0,1),
> $$
> perciò l'ultimo vettore è superfluo. Eliminandolo rimane $B=\{(1,0),(0,1)\}$, che genera $\mathbb R^2$ ed è indipendente: dunque è una base estratta da $S$.

### Aggiungere un vettore a un insieme indipendente
> [!info] Proposizione
> Sia $S=\{u_1,\ldots,u_m\}$ linearmente indipendente e sia $v\in V\setminus S$. Allora
> $$
> \boxed{S\cup\{v\}\text{ è indipendente}\iff v\notin L(S).}
> $$
> Anche senza supporre $v\notin S$ valgono due affermazioni: se $v\notin L(S)$, allora $S\cup\{v\}$ è indipendente; se $S\cup\{v\}$ è dipendente, allora $v\in L(S)$.

> [!tip] Dimostrazione
> **($\Rightarrow$)** Supponiamo per assurdo che $v\in L(S)$; allora esistono $\lambda_i\in K$ con $v=\lambda_1u_1+\cdots+\lambda_mu_m$. Quindi
> $$
> \lambda_1u_1+\cdots+\lambda_mu_m-v=0_V.
> $$
> È una combinazione nulla non banale (coefficiente di $v$ uguale a $-1$), in contraddizione con l'indipendenza di $S\cup\{v\}$.
> **($\Leftarrow$)** Supponiamo $v\notin L(S)$. Se $S\cup\{v\}$ fosse dipendente, esisterebbero coefficienti non tutti nulli con
> $$
> \alpha_1u_1+\cdots+\alpha_mu_m+\beta v=0_V.
> $$
> Se $\beta=0$, l'indipendenza di $S$ impone $\alpha_1=\cdots=\alpha_m=0$, assurdo. Se $\beta\neq0$, isolando $v$ otteniamo
> $$
> v=-\sum_{i=1}^m\frac{\alpha_i}{\beta}u_i\in L(S),
> $$
> ancora assurdo. Quindi $S\cup\{v\}$ è indipendente.


> [!example]- Esercizio 1 — Appartenenza a uno spazio generato
> Sia $S=\{(1,0,1),(0,1,1)\}\subseteq\mathbb R^3$. Stabilire se $w=(3,-1,2)$ appartiene a $L(S)$.
> **Soluzione.** Cerchiamo $\alpha,\beta\in\mathbb R$ tali che
> $$
> (3,-1,2)=\alpha(1,0,1)+\beta(0,1,1)=(\alpha,\beta,\alpha+\beta).
> $$
> Le prime due componenti danno $\alpha=3$ e $\beta=-1$; la terza è verificata, poiché $3+(-1)=2$. Quindi $w\in L(S)$.

> [!example]- Esercizio 2 — Riconoscere una dipendenza
> Studiare i vettori $u_1=(1,0,1)$, $u_2=(0,1,1)$, $u_3=(1,1,2)$.
> **Soluzione.** Si osserva che $u_3=u_1+u_2$, quindi
> $$
> u_1+u_2-u_3=0_V.
> $$
> La combinazione usa i coefficienti $(1,1,-1)$, non tutti nulli: i tre vettori sono dipendenti. Il terzo può essere eliminato senza cambiare lo spazio generato.

> [!example]- Esercizio 3 — Estendere un insieme indipendente
> In $\mathbb R^3$ sia $S=\{(1,0,0),(0,1,0)\}$. Stabilire se $S\cup\{(0,0,1)\}$ è indipendente.
> **Soluzione.** Ogni vettore in $L(S)$ ha terza componente nulla: $(a,b,0)$. Poiché $(0,0,1)\notin L(S)$, la proposizione precedente garantisce che $S\cup\{(0,0,1)\}$ è indipendente.
