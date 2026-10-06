---
Materia: Fisica
tags:
  - Misure
Link risorse:
Libro:
Imparato: true
Ordine: 1
aliases:
  - Misure di grandezza
  - Misure fisiche
---
# Definizione operativa
La **fisica** si basa sull'osservazione della realtà e descrive i fenomeni attraverso **leggi matematiche, grandezze fisiche e unità di misura**.

Esempi di grandezze fisiche:
- Lunghezza
- Distanza
- Intervallo di tempo
- Massa
- Velocità

La **definizione operativa** di una grandezza è la sequenza di operazioni necessarie per **misurarla e associarle un valore numerico e un'unità di misura**.

Le grandezze possono essere misurate:

- **Direttamente**: utilizzando uno strumento.
	- Lunghezza → metro 
	- Intervallo di tempo → cronometro
- **Indirettamente**: ricavandole attraverso altre grandezze misurate
	- Velocità → rapporto tra spazio percorso e intervallo di tempo

---
# Misura completa di una grandezza
Una misura deve contenere tre informazioni:
1. **Valore numerico**: la stima ottenuta dalla misurazione.
2. **Incertezza**: indica il margine entro cui ci si aspetta che si trovi il valore della grandezza.
3. **Unità di misura**: specifica rispetto a quale unità è stato espresso il valore.

Una misura completa può quindi essere scritta nella forma:

$$
x = (x_0 \pm \Delta x)\,u
$$

dove:
- $x_0$ = valore misurato
- $\Delta x$ = incertezza
- $u$ = unità di misura

---
## Sensibilità e incertezza
Qualsiasi strumento di misura possiede una **sensibilità**, cioè la più piccola variazione della grandezza che lo strumento è in grado di rilevare.

L'incertezza può dipendere:
- dalla **sensibilità dello strumento**, per esempio dalla distanza tra le tacche di una scala graduata;
- dalle **variazioni della misura**, quando il valore ottenuto non è perfettamente stabile.


Due misure sono **compatibili** quando i rispettivi intervalli di incertezza presentano una regione di sovrapposizione.

In altre parole, deve esistere almeno un valore che potrebbe essere il valore vero per entrambe le misurazioni.

Nelle **misure dirette** l'incertezza può essere associata direttamente alle caratteristiche dello strumento utilizzato.

Le **misure indirette** sono ottenute mediante calcoli effettuati su altre grandezze misurate.
Di conseguenza, anche le loro incertezze devono essere ricavate a partire dalle incertezze delle grandezze utilizzate.

---
# Cifre significative
Le **cifre significative** sono le cifre che esprimono l'informazione effettivamente disponibile sul valore di una misura.

> [!EXAMPLE]- Esempio: cifre significative e precisione relativa
> Consideriamo il valore: $12,3$
>
> Il numero possiede **3 cifre significative** e l'ultima cifra significativa si trova nella posizione dei **decimi**.
>
> Questo significa che la più piccola variazione rappresentata dall'ultima cifra è $0,1$
>
> Rapportandola al valore misurato otteniamo una stima della **precisione relativa**:
>
> $$
> \frac{0,1}{12,3}=\frac{1}{123}\approx0,0081
> $$
>
> cioè circa:
>
> $$
> 0,81\%
> $$
>
> Quindi $1/123$ **non è l'incertezza assoluta della misura**, ma esprime quanto vale una variazione dell'ultima cifra rispetto al valore complessivo.

Il numero di cifre significative fornisce quindi una prima indicazione della **precisione** con cui è conosciuta la grandezza.

Non è utile riportare molte cifre decimali se lo strumento utilizzato non consente di determinarle con quella precisione.
## Moltiplicazioni e divisioni
Il risultato deve avere lo stesso numero di **cifre significative** del dato che ne possiede di meno.

> [!EXAMPLE]- Esempio
> $2.5 \times 3.142 = 7.855$ poiché $2.5$ ha 2 cifre significative il risultato va scritto come $7.9$
## Somme e differenze
Il risultato deve avere lo stesso numero di **cifre decimali** del dato che ne possiede di meno.

> [!EXAMPLE]- Esempio
> $12.3 + 1.24 = 13.54$ Il risultato va scritto come: $13.5$

Somme e differenze possono essere effettuate soltanto tra **grandezze omogenee**.

---
# Notazione scientifica
La **notazione scientifica** permette di rappresentare numeri molto grandi o molto piccoli nella forma:

$$
a \times 10^n
$$

dove:

$$
1 \leq |a| < 10
$$

- $a$ = **mantissa**
- $n$ = **esponente**

|    Valore | Potenza di 10 |
| --------: | ------------: |
|         1 |        $10^0$ |
|        10 |        $10^1$ |
|       100 |        $10^2$ |
|     1 000 |        $10^3$ |
|    10 000 |        $10^4$ |
|   100 000 |        $10^5$ |
| 1 000 000 |        $10^6$ |

---

# Sistema Internazionale
A ogni valore numerico deve sempre essere associata la relativa **unità di misura**.
Il **Sistema Internazionale (SI)** stabilisce le unità di misura fondamentali utilizzate in fisica.

| Grandezza fondamentale | Unità SI    | Simbolo |
| ---------------------- | ----------- | ------- |
| Lunghezza              | metro       | $m$     |
| Massa                  | chilogrammo | $kg$    |
| Tempo                  | secondo     | $s$     |
| Corrente elettrica     | ampere      | $A$     |
| Temperatura            | kelvin      | $K$     |
| Quantità di sostanza   | mole        | $mol$   |
| Intensità luminosa     | candela     | $cd$    |

Da queste unità fondamentali si ricavano le **unità derivate**.

Per esempio, l'unità di misura della velocità è:

$$
\frac{m}{s}
$$


---
# Dimensioni delle grandezze
Nel rappresentare le grandezze. Le adimensionali non sono associabili.
Se faccio calcoli con una grandezza deve essere restituita tale grandezza

