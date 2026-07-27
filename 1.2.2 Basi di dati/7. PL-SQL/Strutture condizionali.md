---
Materia: Basi di dati
tags:
  - PL-SQL
  - SQL
  - flusso_di_controllo
aliases:
  - condition statements
  - costrutto di selezione
Link risorse: "[Oracle](https://docs.oracle.com/en/database/oracle/oracle-database/21/lnpls/plsql-control-statements.html#GUID-0E130F2D-9635-4C0B-9D63-16C3D9FBE7D2)"
Imparato: true
Ordine: 4
---
Le istruzioni di selezione condizionale, `IF` e `CASE`, eseguono istruzioni diverse per diversi valori di dati.
## `IF`
L'istruzione `IF` esegue o salta una sequenza di una o più istruzioni, a seconda di una condizione. L'istruzione `IF` ha questi moduli:
- `IF THEN`
- `IF THEN ELSE`
- `IF THEN ELSIF`
````PLSQL
IF condition THEN
  statements
END IF;
````
*Esempio:*
````plsql
DECLARE
    voto NUMBER := 27;
BEGIN
    IF voto >= 30 THEN
        DBMS_OUTPUT.PUT_LINE('Ottimo');
    ELSIF voto >= 24 THEN
        DBMS_OUTPUT.PUT_LINE('Buono');
    ELSIF voto >= 18 THEN
        DBMS_OUTPUT.PUT_LINE('Sufficiente');
    ELSE
        DBMS_OUTPUT.PUT_LINE('Bocciato');
    END IF;
END;
````
*L'output: "Buono"*
## `CASE`
L'istruzione `CASE` sceglie tra una sequenza di condizioni ed esegue l'istruzione corrispondente. L'istruzione `CASE` ha questi moduli:
- `CASE` **semplice**: valuta una singola espressione e la confronta con diversi valori potenziali
````PLSQL
CASE selector
WHEN selector_value_1 THEN statements_1
WHEN selector_value_2 THEN statements_2
...
WHEN selector_value_n THEN statements_n
[ ELSE
  else_statements ]
END CASE;]
````
*Esempio:*
````plsql
DECLARE
    giorno NUMBER := 2;
BEGIN
    CASE giorno
        WHEN 1 THEN
            DBMS_OUTPUT.PUT_LINE('Lunedì');
        WHEN 2 THEN
            DBMS_OUTPUT.PUT_LINE('Martedì');
        WHEN 3 THEN
            DBMS_OUTPUT.PUT_LINE('Mercoledì');
        ELSE
            DBMS_OUTPUT.PUT_LINE('Altro giorno');
    END CASE;
END;
````
*L'output: Martedì*


- `CASE` **con ricerca**: valuta molteplici condizioni e sceglie la prima che è vera.
L'affermazione `CASE` è appropriata quando si deve intraprendere un'azione diversa per ogni alternativa.
````PLSQL
CASE
WHEN condition_1 THEN statements_1
WHEN condition_2 THEN statements_2
...
WHEN condition_n THEN statements_n
[ ELSE
  else_statements ]
END CASE;]
````
*Esempio:*
````plsql
DECLARE
    voto NUMBER := 27;
BEGIN
    CASE
        WHEN voto >= 30 THEN
            DBMS_OUTPUT.PUT_LINE('Ottimo');
        WHEN voto >= 24 THEN
            DBMS_OUTPUT.PUT_LINE('Buono');
        WHEN voto >= 18 THEN
            DBMS_OUTPUT.PUT_LINE('Sufficiente');
        ELSE
            DBMS_OUTPUT.PUT_LINE('Bocciato');
    END CASE;
END;
````
*L'output: Buono*