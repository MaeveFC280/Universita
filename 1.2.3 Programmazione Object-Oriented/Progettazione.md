---
Materia: Programmazione Object-Oriented
tags:
  - progettazione_concettuale
  - modello_logico
Link risorse: https://www.hoepli.it/editore/hoepli_file/download_pub/978-88-203-8302-2_Java9-Appendici.pdf
Libro:
Imparato: true
Ordine: 8
aliases:
  - UML
  - SEQUENCE DIAGRAM
  - Progettazione concettuale
  - Rappresentazione
---
![[Screenshot 2026-06-16 alle 14.58.42.png]]
## UML
[[UML]]-> Unified modeling language
![[Screenshot 2026-06-19 alle 14.34.02.png]]
![[Screenshot 2026-06-19 alle 14.35.34.png]]
![[Screenshot 2026-06-19 alle 14.36.12.png]]
![[Screenshot 2026-06-19 alle 14.36.34.png]]
### Nome classe
- Sostantivi
- Significativi
- CamelCase
### Attributi
Il simbolo precedente il nome dell'attributo ne indica la **visibilità**:
- `+` = `public`
- `-` = `private`
- `#`=`protected`
### Metodi
Le operazioni:
- Verbi
- CamelCase
- Iniziano con la minuscola
### Associazioni
- Ruolo: *Segue, Dirige, Lavora...*
- Molteplicità:
	- 0,1: Facoltativo, al più uno
	- 1: Obbligatorio 
	- 1,`*`: Obbligatorio, molti
	- 0,`*`: Facoltativo, molti
- Direzionalità: $\text{A vede}\leftarrow \text{B}\ \ \text{A è visto da}\rightarrow B\text{ A vede B}\leftrightarrow \text{B vede A}$
### Aggregazione/ Composizione

- [[Gerarchie in UML|Aggregazione]]: B esiste anche senza A
- [[Gerarchie in UML|Composizione]]: Se cancello A cancello B
![[Screenshot 2026-06-17 alle 16.45.29.png]]
### Generalizzazione

Quando una [[Ereditarietà|sottoclasse]] indica la superclasse la linea deve finire con un triangolo bianco vuoto o pieno.
![[Screenshot 2026-06-17 alle 16.47.06.png]]
### Classe di associazione
Rappresenta attributi e operazioni dipendenti dall'associazione
### Mapping

| UML                       | JAVA                                                                           |
| ------------------------- | ------------------------------------------------------------------------------ |
| Attributi                 | Attributi                                                                      |
| Classe                    | Classe                                                                         |
| Operazioni                | Metodi                                                                         |
| Associazioni              | Riferimenti                                                                    |
| Molt. 1                   | 1 riferimento                                                                  |
| Molt. *                   | Collezione di riferimenti                                                      |
| Molt. Obbligatoria        | Gestita dal codice                                                             |
| Direzionalità             | Gestita dal codice                                                             |
| Aggregazione/Composizione | Gestita dal codice                                                             |
| Classe di Associazione    | Nuova classe con riferimenti                                                   |
| Gerarchie                 | [[Ereditarietà\|extends]] [[Polimorfismo\|override]], [[Astrazione\|abstract]] |

## Sequence diagram
![[Screenshot 2026-06-19 alle 14.37.53.png]]
![[Screenshot 2026-06-19 alle 14.38.35.png]]
Diagramma di ogni funzionalità, mia ad identificare l'ordine delle chiamate dei metodi. Rappresenta il tempo.
Letto da sinistra a destra e dall'alto verso il basso.
- Sinistra destra: Spazio
- Alto basso: Tempo
I rettangoli indicano gli oggetti.
Si possono creare delle sezioni per indicare i loop:
- OPT: Blocco condizionale `if`
- ALT: Blocco condizionale `if...else`
[![UML Sequence Diagrams: An Agile Introduction](https://agilemodeling.com/wp-content/uploads/2023/04/sequenceDiagramTranscripts.jpg)
