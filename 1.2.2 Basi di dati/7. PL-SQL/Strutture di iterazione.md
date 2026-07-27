---
Materia: Basi di dati
tags:
  - SQL
  - PL-SQL
  - flusso_di_controllo
aliases:
  - loop, ciclo, cicli
Imparato: true
Ordine: 3
---

### `FOR`
- `FOR` termina dopo un determinato numero di volte
- Vengono specificati upper/lower bounds e la variabile di loop
- La variabile loop viene incrementata automaticamente di 1. Non è utilizzabile al di fuori del loop se non viene definita al di fuori di esso.
````PLSQL
FOR variabile_loop IN <REVERSE> <lower_bound>..<upper_bound> LOOP
	-- istruzioni
END LOOP;
````
- `REVERSE` indica se la variabile deve essere decrementata invece che incrementata. Ciò non cambia l'ordine di lower e upper bound.
*Esempio:*
````plsql
BEGIN
    FOR i IN 1..5 LOOP
        DBMS_OUTPUT.PUT_LINE('Numero: ' || i);
    END LOOP;
END; 
````
*L'output:*
1. *Numero: 1*
2. *Numero: 2*
3. *Numero: 3*
4. *Numero: 4*
5. *Numero: 5*
### `LOOP`
- `LOOP` viene eseguito fino a terminazione esplicita del ciclo
- `EXIT` termina immediatamente il ciclo
- `EXIT WHEN` termina il ciclo se una certa condizione occorre
````PLSQL
LOOP
	-- istruzioni
	EXIT;
END LOOP;
````
*Esempio:*
````plsql
DECLARE
    i NUMBER := 1;
BEGIN
    LOOP
        DBMS_OUTPUT.PUT_LINE('Numero: ' || i);
        i := i + 1;
        EXIT WHEN i > 5;
    END LOOP;
END;
````
*L'output:*
1. *Numero: 1*
2. *Numero: 2*
3. *Numero: 3*
4. *Numero: 4*
5. *Numero: 5*
### `WHILE`
- `WHILE` termina quando si verifica una determinata condizione
- La condizione viene controllata all'inizio di ogni ciclo
- È possibile che il loop non avvenga mai se la condizione è falsa fin dall'inizio
- Si presuppone che l'interno del ciclo contenga una variazione della condizione, onde evitare un loop infinito
````PLSQL
WHILE <condition> LOOP
	-- istruzioni
END LOOP;
````
*Esempio:*
````plsql
DECLARE
    i NUMBER := 1;
BEGIN
    WHILE i <= 5 LOOP
        DBMS_OUTPUT.PUT_LINE('Numero: ' || i);

        i := i + 1;
    END LOOP;
END;
````
*L'output:*
1. *Numero: 1*
2. *Numero: 2*
3. *Numero: 3*
4. *Numero: 4*
5. *Numero: 5*