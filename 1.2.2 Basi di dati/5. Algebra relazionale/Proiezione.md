---
Materia: Basi di dati
tags:
  - algebra_relazionale
  - operatore_unario
Libro: '"Sistemi di basi di dati. Fondamenti e complementi" Capitolo 6.1.2'
Link risorse: "[Personal Knowledge Base](https://www.andreaminini.com/database/algebra-relazionale/)"
Imparato: true
Ordine: 2
aliases:
  - PROJECT
---
 L’operazione PROJECT (di proiezione) **seleziona determinate colonne della tabella e scarta le altre**. Se si è interessati solo a determinati attributi di una relazione, si può usare l’operazione PROJECT per proiettare la relazione solo su di loro. 
$$
 \pi_{\text{<lista degli attributi>}}(R)
$$
Dove $\pi$ (pi greco) è il simbolo usato per rappresentare l’operazione e lista di attributi è l’elenco degli
attributi desiderati, presi fra quelli della relazione $R$.
 Il risultato dell’operazione PROJECT ha solo gli attributi specificati nella lista di attributi, nello stesso ordine con cui compaiono nella lista. Perciò il suo grado è uguale al numero di attributi in lista di attributi.
I duplicati  vengono eliminati.