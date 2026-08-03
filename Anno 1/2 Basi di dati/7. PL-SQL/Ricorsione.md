---
Materia: Basi di dati
tags:
  - PL-SQL
  - SQL
aliases:
  - Funzioni innestate
Imparato: true
Ordine: 5.2
---
Una ricorsione avviene quando **una struttura chiama se stessa** per risolvere un problema a pezzi. Una [[Funzioni e procedure|procedura o funzione]] può chiamare se stessa in SQL.
*Esempio:*
````plsql
CREATE OR REPLACE FUNCTION fattoriale(n NUMBER)
RETURN NUMBER
IS
BEGIN
    IF n = 0 THEN
        RETURN 1;
    ELSE
        RETURN n * fattoriale(n - 1); -- qui la funzione fattoriale di richiama
    END IF;
END fattoriale;
/
````
*la funzione si richiamerà fino a quando n non equivarrà a 0:
fattoriale(5)
= 5 * fattoriale(4)
= 5 * 4 * fattoriale(3)
= 5 * 4 * 3 * fattoriale(2)
= 5 * 4 * 3 * 2 * fattoriale(1)
= 5 * 4 * 3 * 2 * 1 * fattoriale(0)
= 5 * 4 * 3 * 2 * 1 * 1
= 120*

Nel linguaggio SQL la ricorsione serve soprattutto per dati **gerarchici**, cioè dati “a livelli”.
*Esempio:*

| id  | nome    | id_capo |
|:---:| ------- |:-------:|
|  1  | Rossi   |  NULL   |
|  2  | Bianchi |    1    |
|  3  | Verdi   |    1    |
|  4  | Neri    |    2    |
È possibile usare `CONNECT BY` per risalire al capo o ai sottoposti
````plsql
SELECT nome, LEVEL -- pseudocolonna indica la profondità della query
FROM dipendente
START WITH id_capo IS NULL -- parti dal capo massimo senza capi al di sopra
CONNECT BY PRIOR id = id_capo; -- trova i sottoposti con quell'id_capo
````
