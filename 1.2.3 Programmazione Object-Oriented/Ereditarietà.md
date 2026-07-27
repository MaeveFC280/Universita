---
Materia: Programmazione Object-Oriented
tags:
  - Java
Link risorse:
Libro:
Imparato: true
Ordine: 9
aliases:
---
 ![[Screenshot 2026-06-17 alle 16.55.31.png]]
 Strumento chiave dei linguaggi OO. Le sotto
La keyword `extends` viene utilizzata nella dichiarazione della sottoclasse per indicare la superclasse.
````java
public class figlia extends padre{}
````
Le specializzazioni non possono nascondere attributi alle sottoclassi.
 Con `super`() richiamiamo il costruttore della superclasse.
````java
public figlia(x,y,z){
	super(x,y);
	this.z = z;
}
````

La keyword `super` funge da "[[Introduzione a Java|this]] per la superclasse". Si usa per richiamare i metodi della classe padre o, in particolare all'inizio del costruttore di una sottoclasse (`super();`), per forzare la Java VM a istanziare preventivamente l'oggetto padre in memoria prima di allocare le variabili aggiuntive della sottoclasse.