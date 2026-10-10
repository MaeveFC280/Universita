---
Materia:
  - Algebra Lineare
  - Geometria
tags:
Link risorse:
Libro:
Imparato: false
Ordine: 5
aliases:
---
## Struttura algebrica
>[!info] Definizione
>Una **struttura algebrica** è costituita da uno o più insiemi, dotati di una o più [[Operazioni|operazioni]], delle quali si studiano le proprietà.
>Quando le operazioni sono definite su un unico insieme non vuoto $A$, la struttura può essere rappresentata da una tupla:
>$$
>(A,\perp_1,\dots,\perp_r),\qquad r\geq1
>$$
>dove $A$ è detto **insieme sostegno** (o supporto) e $\perp_1,\dots,\perp_r$ sono le operazioni considerate.
>Ad esempio, $(A,\perp)$ ha una sola operazione, mentre $(A,+,\cdot)$ ne ha due.

Le proprietà delle operazioni (associatività, commutatività, elemento neutro e inversi) sono definite in [[Operazioni]]. In base alle proprietà soddisfatte, possiamo riconoscere **gruppi**, **anelli** e **campi**.

---
## Gruppo
>[!info] Definizione
>Sia $A\neq\varnothing$ e sia $\perp:A\times A\to A$ un'operazione interna. La struttura $(A,\perp)$ è un **gruppo** se:
>1. **Associatività:** per ogni $x,y,z\in A$,
>   $$
>   (x\perp y)\perp z=x\perp(y\perp z).
>   $$
>2. **Elemento neutro:** esiste $e\in A$ tale che, per ogni $x\in A$,
>   $$
>   x\perp e=e\perp x=x.
>   $$
>3. **Inverso per ogni elemento:** per ogni $x\in A$ esiste $x^{-1}\in A$ tale che
>   $$
>   x\perp x^{-1}=x^{-1}\perp x=e.
>   $$
>Se inoltre $\perp$ è **commutativa**, ossia $x\perp y=y\perp x$ per ogni $x,y\in A$, il gruppo si dice **abeliano**.

^0826fd

>[!example]- Esempi
>**$(\mathbb Z,+)$ è un gruppo abeliano:** la somma è associativa e commutativa, l'elemento neutro è $0$ e l'inverso di ogni $z\in\mathbb Z$ è l'opposto $-z$.
>**$(\mathbb Q\setminus\{0\},\cdot)$ è un gruppo abeliano:** l'elemento neutro è $1$ e ogni numero razionale non nullo ammette un reciproco razionale.
>**$(\mathbb N,+)$ non è un gruppo:** indipendentemente dalla convenzione adottata per $0\in\mathbb N$, non tutti i naturali hanno l'opposto in $\mathbb N$ (ad esempio, $1$ non ha come opposto un numero naturale).

>[!note] Osservazione
>Non basta che **qualche** elemento ammetta inverso: in un gruppo deve essere invertibile **ogni** elemento dell'insieme.
>Le dimostrazioni dell'unicità del neutro, dell'unicità dell'inverso e della formula per l'inverso di un prodotto sono già in [[Operazioni]].

---
## Anello
>[!info] Definizione
>Sia $A\neq\varnothing$. Una struttura $(A,+,\cdot)$, con due operazioni interne su $A$, è un **anello** se:
>1. **$(A,+)$ è un gruppo abeliano:** la somma è associativa e commutativa, ammette un elemento neutro $0$ e ogni elemento ha un opposto.
>2. **Il prodotto è associativo:** per ogni $a,b,c\in A$,
>   $$
>   (ab)c=a(bc).
>   $$
>3. **Il prodotto è distributivo rispetto alla somma da entrambi i lati:** per ogni $a,b,c\in A$,
>   $$
>   \boxed{a(b+c)=ab+ac}
>   $$
>   $$
>   \boxed{(a+b)c=ac+bc}
>   $$

Un anello è detto:
- **commutativo**, se $ab=ba$ per ogni $a,b\in A$;
- **unitario**, se esiste un elemento neutro $1\in A$ per il prodotto, cioè $1a=a1=a$ per ogni $a\in A$.

Le due proprietà sono **indipendenti**: un anello può essere unitario senza essere commutativo, oppure commutativo senza essere unitario.

>[!example]- Esempi
>**$(\mathbb Z,+,\cdot)$** è un anello **commutativo e unitario**: il neutro della somma è $0$ e il neutro del prodotto è $1$.
>**$(M_2(\mathbb R),+,\cdot)$** è un anello **unitario ma non commutativo**: il prodotto tra matrici è associativo e distributivo, ammette la matrice identità $I_2$, ma in generale $AB\neq BA$. Si veda [[Prodotto tra matrici]].
>**$(2\mathbb Z,+,\cdot)$**, dove $2\mathbb Z$ è l'insieme degli interi pari, è un anello **commutativo non unitario**, con le operazioni usuali: nessun intero pari è elemento neutro del prodotto su $2\mathbb Z$.

>[!note] Attenzione
>Essere **unitario** non significa che tutti gli elementi siano invertibili per il prodotto. In $\mathbb Z$, ad esempio, $2$ non ha un inverso moltiplicativo intero, pur essendo l'anello unitario.

---
## Campo
>[!info] Definizione
>Un **campo** è un anello $(K,+,\cdot)$ che soddisfa tutte le seguenti condizioni:
>1. È **commutativo** rispetto al prodotto.
>2. È **unitario**, con elementi neutri distinti $0\neq1$.
>3. **Ogni elemento non nullo è invertibile rispetto al prodotto:**
>   $$
>   \forall a\in K\setminus\{0\},\quad\exists a^{-1}\in K:\quad aa^{-1}=a^{-1}a=1.
>   $$
>In particolare, un campo possiede le strutture di gruppo abeliano:
>$$
>(K,+),\qquad(K\setminus\{0\},\cdot).
>$$
>La moltiplicazione è inoltre distributiva rispetto alla somma.

^1ed1df

>[!example]- Esempi e controesempi
>**$\mathbb Q$, $\mathbb R$ e $\mathbb C$ sono campi** rispetto alle consuete operazioni di somma e prodotto.
>**$\mathbb Z$ non è un campo**, perché ad esempio $2$ non ammette inverso moltiplicativo in $\mathbb Z$.
>**Il campo con due elementi** è $\mathbb F_2=\mathbb Z/2\mathbb Z=\{[0],[1]\}$, con somma e prodotto modulo $2$. Identificando le classi con $0$ e $1$, valgono in particolare:
>$$
>1+1=0,\qquad 1\cdot1=1.
>$$
>L'unico elemento non nullo, $1$, è inverso di se stesso: quindi $\mathbb F_2$ è un campo.

### Come distinguere le tre strutture
- **Gruppo:** una operazione associativa, con neutro e inverso per ogni elemento.
- **Anello:** due operazioni; somma con struttura di gruppo abeliano, prodotto associativo e distributivo sulla somma.
- **Campo:** anello commutativo e unitario ($0\neq1$) in cui ogni elemento non nullo è invertibile per il prodotto.

Per la definizione di [[Spazi e sottospazi vettoriali|spazio vettoriale]], gli scalari vengono scelti proprio in un campo $K$.
