---
Materia: Programmazione Object-Oriented
tags:
  - Java
Link risorse:
Libro:
Imparato: true
Ordine: 10
aliases:
  - Overriding
  - Overloading
---
 Il principio per cui una variabile può avere più tipi è **polimorfismo** (una variabile ha in se tutti i tipi antenati nella gerarchia)
- Posso definire strutture dati dei tipi più generici e metterci qualunque specializzazione
## Overriding
 Quando **una sottoclasse fornisce una specifica implementazione di un metodo che è già fornito** dalla sua classe base.
Una sottoclasse può ridefinire un metodo presente in una delle superclassi. **Stessa signature, implementazione diversa**
- **_Keyword:_** *`@Override`
La keyword non è obbligatoria ma costringe il compilatore a controllare che ci sia veramente un metodo da sovrascrivere.
*Esempio:*
````java
public class Animale {
    public void faiRumore() {
        System.out.println("Questo animale fa un suono.");
    }
}
public class Cane extends Animale {
    public void faiRumore() {
        System.out.println("Il cane fa: Bau Bau!");
    }
}
public class Gatto extends Animale {
    public void faiRumore() {
        System.out.println("Il gatto fa: Miao Miao!");
    }
}
````
## Overloading
Quando due o più metodi nella stessa classe hanno lo stesso nome ma parametri diversi.
````java
public class Animale {
    public void faiRumore() {
        System.out.println("Questo animale fa un suono.");
    }
    public void faiRumore(String suono) {
        System.out.println("Questo animale fa: " + suono);
    }
}
````
## Super
In Java, la parola chiave `super` viene utilizzata per fare riferimento alla classe madre di una sottoclasse.
- Per accedere agli attributi e ai metodi dalla classe principale
- Per chiamare il costruttore di classe padre
Se una sottoclasse ha un metodo con lo stesso nome di uno nella sua classe padre, puoi usare super per chiamare la versione principale.
*Esempio:*
````java
class Animal {
  public void animalSound() {
    System.out.println("The animal makes a sound");
  }
}

class Dog extends Animal {
  public void animalSound() {
    super.animalSound(); // Call the parent method
    System.out.println("The dog says: bow wow");
  }
}
````
Puoi anche usare `super` per accedere a un attributo dalla classe principale se hanno un attributo con lo stesso nome.
*Esempio:*
````java
class Animal {
  String type = "Animal";
}

class Dog extends Animal {
  String type = "Dog";
  public void printType() {
    System.out.println(super.type); // Access parent attribute
  }
}
````
Puoi chiamare il costruttore della superclasse usando `super()`
*Esempio:*
````java
class Animal {
  Animal() {
    System.out.println("Animal is created");
  }
}

class Dog extends Animal {
  Dog() {
    super(); // Call parent constructor
    System.out.println("Dog is created");
  }
}
````
*La chiamata a `super()` deve essere la prima istruzione nel costruttore di sottoclassi.*
## Polimorfismo dinamico
Il polimorfismo dinamico è il meccanismo per cui una chiamata a un metodo sovrascritto viene risolta a runtime in base al tipo reale dell’oggetto, e non solo in base al tipo della variabile di riferimento.
````java
Device d = new Smartphone(); //userà il metodo di Smartphone
````