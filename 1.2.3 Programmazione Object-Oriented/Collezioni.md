---
Materia: Programmazione Object-Oriented
tags:
  - Java
Link risorse:
Libro:
Imparato: true
Ordine: 6
aliases:
---
Un vettore è un oggetto con degli attributi. Per via dell'[[Introduzione a Java|incapsulamento]] non è possibile rappresentare internamente glie elementi e **l'aritmetica dei puntatori non esiste**.
Le stringhe sono immediatamente integrate e **non** sono un array di caratteri. [[Introduzione a Java|L'operatore == non funziona]].

Le `collections` fanno parte del pacchetto `java.util`
![[Pasted image 20260619145744.png]]

## `List`
[[DAO|Interfaccia]] per una collezione in cui gli elementi sono mantenuti in una sequenza il cui ordine è determinato dal modo con cui sono aggiunti o rimossi. Le posizioni di una lista `list` sono numerate da `0` a `list.size() - 1`. I principali metodi aggiunti dall'interfaccia `List<E>` sono i seguenti:
- [`void add(int index, E elem)`](http://docs.oracle.com/javase/8/docs/api/java/util/List.html#add-E-)
	Aggiunge l'elemento `elem` in posizione `index` spostando di una posizione in avanti tutti gli elementi che si trovavano nelle posizioni da `index` in poi.
- [`E set(int index, E elem)`](http://docs.oracle.com/javase/8/docs/api/java/util/List.html#set-int-E-)
	Sostituisce l'elemento in posizione `index` con `elem` e ritorna l'elemento sostituito.
- [`E get(int index)`](http://docs.oracle.com/javase/8/docs/api/java/util/List.html#get-int-)
	Ritorna l'elemento in posizione `index`.
- [`E remove(int index)`](http://docs.oracle.com/javase/8/docs/api/java/util/List.html#remove-int-)
	Rimuove e ritorna l'elemento in posizione `index`. Gli eventuali elementi successivi sono spostati di una posizione indietro.
- [`Iterator<E> iterator()`](http://docs.oracle.com/javase/8/docs/api/java/util/List.html#iterator--)
	Ritorna un iteratore che scandisce gli elementi secondo l'ordine della sequenza.
## `ArrayList`
Implementazione dell'[[DAO|Interfaccia]] `List<E>` tramite array.  Un'`ArrayList` gestisce automaticamente la capacità. I normali Array offrono il vantaggio dell'accesso diretto in lettura, ma sono molto lenti nelle modifiche strutturali. 
## `LinkedList`
Implementazione delle [[DAO|interfacce]] `List<E>`, `Queue<E>` e `Deque<E>` tramite liste bidirezionali (_doubly-linked list_). Quindi permette di rappresentare non solo strutture FIFO, cioè code, ma anche strutture LIFO, cioè pile e liste.
## `Set`
[[DAO|Interfaccia]] per un insieme di elementi (cioè, non può contenere elementi duplicati). Non mantiene alcun ordinamento.
## HashSet
Implementazione dell'[[DAO|Interfaccia]] `Set<E>` tramite tabelle hash.