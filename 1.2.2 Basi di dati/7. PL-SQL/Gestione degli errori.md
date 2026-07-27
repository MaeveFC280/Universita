---
Materia: Basi di dati
tags:
  - PL-SQL
  - SQL
aliases:
  - EXCEPTION
  - Gestione delle eccezioni
Imparato: true
Ordine: 8
---
Il comando `EXCEPTION` trova gli errori e li gestisce in modo tale da non far crollare l'esecuzione. Gli errori si possono gestire in vari modi.
## Gestire errori già previsti
Utilizzando `WHEN <nome_errrore> THEN` è possibile **gestire ogni errore i maniera differente**, in base alla sua tipologia.
*Esempio:*
````plsql
DECLARE
    x NUMBER;
BEGIN
    SELECT 10 / 0
    INTO x
    FROM dual;

EXCEPTION
    WHEN ZERO_DIVIDE THEN
        DBMS_OUTPUT.PUT_LINE('Errore: divisione per zero');
END;
````
## Gestire errori qualsiasi
Utilizzando `WHEN OTHER THEN` è possibile gestire **qualsiasi errore non gestito altrove**.
## Errori personalizzati
Puoi **dichiarare una tua eccezione** con `DECLARE nome_errore EXCEPTION`. È  possibile richiamarlo in un qualsiasi momento con `RAISE`
*Esempio:*
````plsql
DECLARE
    errore_eta EXCEPTION;
    eta NUMBER := 15;
BEGIN
    IF eta < 18 THEN
        RAISE errore_eta;
    END IF;

    DBMS_OUTPUT.PUT_LINE('Maggiorenne');

EXCEPTION
    WHEN errore_eta THEN
        DBMS_OUTPUT.PUT_LINE('Errore: età inferiore a 18');
END;
````
Oppure utilizzare direttamente `RAISE_APPLICATION_ERROR`
*Esempio:*
````plsql
BEGIN
    RAISE EXCEPTION(-20001, 'Operazione non consentita');
END;
````
Il numero deve stare di solito tra -20000 e 20999
## Rilanciare un errore
Puoi catturare un errore, stampare qualcosa, e poi rilanciarlo:
*Esempio:*
````plsql
BEGIN
    DBMS_OUTPUT.PUT_LINE(10 / 0);

EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Si è verificato un errore');
        RAISE;
END;
````
Rilanci un errore quando vuoi **fare qualcosa localmente** — per esempio stampare/loggare l’errore — ma **non vuoi nasconderlo** al programma chiamante.