---
Materia: Basi di dati
tags:
  - SQL
  - PL-SQL
  - SQL_Dinamico
Link risorse:
Libro:
Imparato: true
Ordine: 91
aliases:
---
I [[Cursore|cursori]] in [[SQL dinamico]] la `SELECT`  viene creata dinamicamente ed è contenuta in una variabile di tipo `VARCHAR`. Si definisce una variabile di tipo puntatore a cursore e si aggancia dinamicamente a runtime la `SELECT`: `<nome_cursore> SYS_REF.CURSOR`.
## Weakly e Strongly typed
Un cursore può essere weakly o strongly typed.
- Weakly: Non conosco la struttura del risultato: `<nome_cursore> SYS_REF.CURSOR`
- Strongly: Conosco il tipo di ritorno `<nome_cursore> SYS_REF.CURSOR RETURN <tipo>`
## Associare il cursore alla `SELECT`
Tramite una `OPEN` esplicita
````plsql
OPEN <nome_cursore> FOR <stringa_comando>
````