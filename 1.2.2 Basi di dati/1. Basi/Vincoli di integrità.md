---
Materia: Basi di dati
tags:
  - progettazione_concettuale
Libro: '"Sistemi di basi di dati. Fondamenti e complementi" Capitolo 5'
Link risorse:
Imparato: true
Ordine:
---
Esistono vari tipi di vincoli.
Si dividono tra **intrarelazionali** e **interrelazionali**.
## Intrarelazionali
Sono vincoli dentro una stessa relazione. Ad esempio, vincoli di tupla e i vincoli di chiave
#### Vincoli di tupla
Un **vincolo di tupla** è una condizione applicata a ogni tupla di una tabella (relazione).
Se il vincolo di tupla riguarda un solo attributo della tabella è anche detto **vincolo sui valori** o **vincolo di dominio**, se riguarda più attributi è un vincolo **N-Pla**
#### Vincoli di chiave
I vincoli di chiave sono gli attributi scelti come chiave della tabella (relazione). Esistono diversi tipi di [[Chiavi|chiavi]], le più importante la **chiave primaria** duplicati né valori nulli.
## Interrelazionali
Sono vincoli tra relazioni diverse. Ad esempio, i vincoli referenziali.
#### Vincoli referenziali
I vincoli di integrità referenziale collegano diverse tabelle (relazioni) tramite i valori in comune. Sono anche detti **chiavi esterne**.