---
Materia: Basi di dati
tags:
  - SQL
  - PL-SQL
Link risorse:
Libro:
Imparato: true
Ordine: 10
aliases:
---

| Funzione    | Esempio                             | Risultato       | Scopo                                                                                    |
| ----------- | ----------------------------------- | --------------- | ---------------------------------------------------------------------------------------- |
| `ASCII`     | `ASCII('A')`                        | 65              | Ritorna il valore del codice ASCII del carattere                                         |
| `CHR`       | `CHR('65')`                         | A               | Ritorna il carattere corrispondente al codice ASCII                                      |
| `CONCAT`    | `CONCAT('A','BC')`                  | 'ABC'           | Unisce due stringhe (può essere abbreviato da \|\|)                                      |
| `INITCAP`   | `INITCAP('hi there')`               | Hi there        | Invertisce la capitalizzazione del primo carattere di una stringa                        |
| `INSTR`     | `INSTR('This is a car','is',1)`     | 3               | Restituisce la prima posizione in cui appare la substring                                |
| `LENGHT`    | `LENGHT('ABCDEFG')`                 | 7               | Restituisce la lunghezza della stringa                                                   |
| `UPPER`     | `UPPER('Abc')`                      | ABC             | Riscrive la stringa in maiuscolo                                                         |
| `LOWER`     | `LOWER('AbC')`                      | abc             | Rende minuscola l'intera stringa                                                         |
| `REPLACE`   | `REPLACE('JACK AND JOND','J','BL')` | BLACK AND BLOND | Sostituisce le occorrenze di una substring con un'altra                                  |
| `RPAD`      | `RPAD('Abc',5,'*')`                 | Abc**           | Riempie la spazio vuoto con un carattere fino a raggiungere una certa lunghezza.         |
| `RTRIM`     | `RTRIM(' ABC )`                     | ABC             | Rimuove lo spazio vuoto, o un carattere specificato, a destra della stringa              |
| `LTRIM`     | `LTRIM(';abc;')`                    | abc;            | Rimuove lo spazio vuoto, o un carattere specificato, a sinistra della stringa            |
| `TRIM`      | `TRIM(' ABC ')`                     | ABC             | Rimuove lo spazio vuoto, o un carattere specificato, dall'inizio e fino della stringa    |
| `SUBSTR`    | `SUBSTR('Oracle substring',1,6)`    | Oracle          | Estrae una substring iniziando da un certo carattere e finendo ad un altro partendo da 1 |
| `TRANSLATE` | `TRANSLATE('12345','143','bx')`     | b2x5            | Sostituisce i caratteri con altri caratteri                                              |
