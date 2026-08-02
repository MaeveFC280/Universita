---
Materia: Programmazione Object-Oriented
tags:
  - Java
Link risorse:
Libro:
Imparato: true
Ordine: 1
aliases:
  - intro
  - base
---
Java usa un **approccio botto-up** (object-oriented) che migliora l'efficienza e la manutenzione. Con un paradigma procedurale non è possibile **proteggere i dati** da **accessi non autorizzati** mentre con l'OO si introduce  il concetto di [[Introduzione a Java|classe]], un tipo di dato personalizzato che permette di usare l'incapsulamento degli attributi, rafforzando la sicurezza.
Si creano gli oggetti, ognuno dei quali contiene dei dati e funzionalità.
Il `main` rimane succinto.
![[Pasted image 20260611001401.png]]
Il file `.java` viene passato ad un compilatore, che produce un file bytecode, il quale viene passato alla *java virtual machine*.

Java esegue codice all’interno della virtual machine
- **Portabilità**: Possibilità di eseguire lo stesso binario su hw/s.o. differenti

JavaVirtualMachine prende come argomento il ByteCode 
Java è il principale linguaggio **server-side**
 
- LTS: oracle si impegna a supportarla per anni
- SE: Standard Edition
- JRE: Per utenti
- **JDK**: Per sviluppatori+
## Memoria
Quando il programma tenta di uscire dall'area di memoria stabilità java stesso lo limita.
I puntatori sono nascosti e l'allocazione/deallocazione degli oggetti (tramite [[Introduzione a Java|`new`]]) è automatica.
Quando l'area di memoria non è più puntata viene marcata affinché il *Garbage collector* la liberi automaticamente.
