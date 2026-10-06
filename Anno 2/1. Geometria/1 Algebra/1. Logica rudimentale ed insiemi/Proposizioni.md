---
Materia: Algebra Lineare
tags:
  - Logica
Libro:
Link risorse:
Imparato: true
Ordine: 0
aliases:
date: 2026-06-11
---

- **Alfabeto**: insieme di simboli con un significato ben definito
La parte dei simboli si chiama **semantica**, l’altra **sintassi**
Tipi di formule:
- **Formule be formate:** scritta correttamente
- **Formula chiusa:** no variabili
- **Formula aperta**: con variabili
Altri [[Logic gates|simboli]] più particolari vengono usati nella logica e insiemistica
- **Connettivo binario**: Unisce 2 proposizioni (non necessariamente distinte)
- **Connettivo unario**: Unisce 1 proposizione
Proposizioni possono essere vere o false, scritte con simboli e regole sintattiche

> [!Predicato]
> Un predicato è una frase che non ha un valore di verità definito, e dipende da una o più **variabili libere** (ad esempio $x$ ).  
> Quando le variabili libere vengono sostituite da un valore determinato, il predicato diventa una proposizione con un valore di verità.


> [!Tautologia]
> 
>  Una **tautologia** è una proposizione composta sempre vera, indipendentemente dai valori di verità delle proposizioni atomiche che la compongono
1. **Terzo escluso**:  $p \vee \urcorner p$
2. **Doppia negazione:**  $\urcorner(\urcorner p)\Leftrightarrow p$
3. **Idempotenza**:  $p\Leftrightarrow p \wedge p \Leftrightarrow p \vee p$
4. **Commutatività:**  $p \vee q \Leftrightarrow q \vee p$
5. **Associatività:** $p\wedge (q\wedge r)\leftrightarrow (p\wedge q)\wedge r \text{/} p\vee (q\vee r)\leftrightarrow (p\vee q)\vee r$
6. **Distributività:**   $p\wedge(q\vee r)\leftrightarrow (p\wedge q)\vee(p\wedge r) \text{/}p\vee(q\wedge r)\leftrightarrow (p\vee q)\wedge(p\vee r)$
7. **De Morgan:**$\urcorner(p\wedge q)\leftrightarrow (\urcorner p\vee \urcorner q)\text{/}\urcorner(p\vee q)\leftrightarrow (\urcorner p\wedge \urcorner q)$

> [!Contradizione]
> 
>  Una **contraddizione** è una proposizione composta che risulta sempre falsa, indipendentemente dal valore di verità delle sue componenti atomiche.

> [!Equivalenza]
> 
>Due proposizioni sono **equivalenti** se assumono lo stesso valore in in tutte le loro combinazioni
