---
Materia:
  - Geometria
  - Algebra Lineare
tags:
Link risorse:
Libro:
Imparato: false
Ordine: 8
aliases:
---
## Vettori liberi
Un **vettore libero** è una [[Relazioni#^classeEquivalenza|classe di equivalenza]] di segmenti orientati aventi:
- stessa direzione;
- stesso verso;
- stessa lunghezza.

L'insieme di tutti i vettori liberi si indica con $V$


![[Vettori-1790939919483.webp]]

---
## Vettori applicati
Fisso con origine nello spazio

---
## Operazioni con i vettori
### Somma di vettori
L'addizione tra vettori è un'[[Operazioni|operazione interna]].

$$  
+\times V\to V  
$$

e può essere definita geometricamente mediante la **regola del parallelogramma**.
![[Operazioni-1790588572979.webp|right]]

La struttura $(V,+)$ è un **[[Strutture algebriche#^0826fd|gruppo abeliano]]**.

Questo significa che per ogni $u,v,w\in V$ valgono:
- Associatività: $(u+v)+w=u+(v+w)$
- Elemento neutro: $0\in V\qquad u+0=0+u=u$
- Elemento opposto: $\forall u\in V\exists-u\in V:u+(-u)=0$
- Commutatività: $u+v=v+u$

Poiché un vettore è una classe di equivalenza di segmenti orientati, **possiamo cambiare rappresentante, traslando il vettore, senza cambiare il vettore stesso**.

Questo permette di scegliere rappresentanti con lo stesso punto di applicazione e applicare la regola del parallelogramma.

### Moltiplicazione per uno scalare
Si definisce un'[[Operazioni|operazione esterna]]:

$$
\cdot:\mathbb R\times V\to V.
$$

Dato $\alpha\in\mathbb R$ e $v\in V$:

- se $\alpha>0$, $\alpha v$ ha stessa direzione e stesso verso di $v$, con lunghezza moltiplicata per $\alpha$;
- se $\alpha<0$, ha stessa direzione ma verso opposto;
- se $\alpha=0$, si ottiene il vettore nullo.

---
