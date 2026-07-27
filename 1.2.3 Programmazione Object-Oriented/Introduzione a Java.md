---
Materia: Programmazione Object-Oriented
tags:
  - Java
Link risorse:
Libro:
Imparato: true
Ordine: 2
aliases:
---
- Java è **memory safe**: no puntatori o gestione dell’allocazione in memoria
- Java è **Object-Oriented**
- In java per forzare il programmatore ad organizzare lavoro e file **ogni classe deve andare in un file separato** e il **file si deve chiamare esattamente come il nome della classe**
## Compilatore: Javac
````
>Javac PrimoEsempio.java
>dir (crea PrimoEsempio.class, NON eseguibile)
>java PrimoEsempio
>Hello World 
````
Il compilatore Java non compila tutte le classi in un unico programma in codice macchina. Invece compila ciascuna classe separatamente, e non in codici macchina, bensì in un codice intermedio speciale (bytecode). La compilazione in codice macchina avviene all’avvio del programma.

## Classe

**Schema** di un nuovo **tipo**, in termini di **dati** (attributi) e **operazioni** (metodi).
Le **classi** in Java sono strutture che definiscono le caratteristiche e i comportamenti degli oggetti che saranno creati a partire da esse.

#**_Keyword_**: **`class`**
````java
 public class NomeClasse { 
double variabile;
}
````
- Ogni programma Java deve avere almeno una classe, solitamente `Main`
- Tutto ciò dichiarato nelle parentesi graffe appartiene alla classe
- La classe può essere:
	- **`public`**: La classe è **accessibile** da **qualsiasi** altra classe in qualsiasi pacchetto.
	- **`private`**: Un attributo privato è **accessibile** in lettura/scrittura **solo all’interno della classe** stessa (solo su attributi e metodi, non sulle classi)
	- **`protected`**: sono **accessibili** dalle classi dello **stesso pacchetto** e **dalle sottoclassi** (classi figlie), anche se si trovano in pacchetti diversi.
	- **`default`**: se non viene specificato alcun modificatore di accesso, il membro è considerato di accesso “default” o “package-private”. Questo significa che il membro è accessibile solo dalle classi nello stesso pacchetto.

## Metodo
- **I metodi definiscono le azioni** che gli oggetti di una classe possono eseguire.
- Un metodo nel linguaggio Java può avere un tipo di ritorno specifico, come int, double, String, o può essere void se non restituisce nulla.
- I metodi possono essere definiti senza parametri o con uno o più parametri. I parametri fungono da input al metodo e influenzano il suo comportamento.
````java
public void nome(){}
````
## Main
Il metodo Java `main()` è il punto iniziale di Java Virtual Machine (JVM). Viene utilizzato per avviare l'esecuzione di un programma Java.
````java
public static void main(String[] args){
// some code here in the main() method
}
````
La funzione main in Java accetta un singolo array String come input. Le stringhe dell'array sono argomenti della riga di comando. In fase di esecuzione, gli utenti possono utilizzare argomenti della riga di comando per influenzare il funzionamento del programma o per inviare dati al programma.

## Stampa

- **_Keyword:_** `System.out.println( )` 

Può essere diviso in tre parti:
- `System`: provvede accesso alle risorse del sistema, come input output ed errori
- `out`: rappresenta output standard nella console
- `println()`: una versione migliore di `print()` che aggiunge una nuova linea alla fine in automatico

## Attributi
Tutti gli attributi di una classe sono inizializzati a $\oslash$
- int=0
- double=0.0
- boolean=false
- char=\0000

**Le variabili locali NON vengono inizializzate e non possono essere lette variabili non inizializzate**

## Tipi primitivi e riferimento

### Tipi primitivi:
- Int
- Float
- Double
- Char
- Short
- Long
### Tipi riferimento:
- string 
- Out 
- “Persona”5 (tipo custom)

Per accedere agli attributi di riferimento è necessaria la dot-notation 
###  = o.equals()`
L'operatore  == va applicato sui tipi primitivi e confronto il loro valore. utilizzare == agli oggetti confronta invece i loro *indirizzi di memoria*, e perché necessario usare il metodo `.equals()` che permette di uguagliare il contenuto. 
### Classe wrapper
Sono versioni oggetto dei tipi primitivi (*es. int->Integer*). Sono necessari per alcune strutture, come le *Collection*, che accettato solo oggetti. **L'autoboxing** è il processo automatico che compie il compilatore in maniera trasparente per convertire un tipo primitivo in oggetto wrapper. **L'unboxing** è il processo opposto sempre automatico che estrapola il tipo primitivo.
## Oggetto
**Istanziare** significa creare un oggetto a partire da una classe

- **_keyword_****:** **`new`**

`NomeClasse NomeOggetto = new NomeClasse();`
Quando si scrive `new` java:
1. crea un oggetto in memoria
2. esegue il costruttore della classe
3. restituisce un riferimento a quell'oggetto

Per accede a metodi e attributi di un oggetto si utilizza la **notazione dot** (**`.`**)

`NomeOggetto.Metodo(parametro);`

`NomeOggetto.Attributo`

- **Stato**: Gli oggetti hanno uno “stato”, che è rappresentato da attributi o variabili di istanza.
- **Comportamento**: Gli oggetti hanno anche “comportamento”, che è rappresentato dai metodi della classe.
- **Identità**: Ogni oggetto ha un’identità unica, che in un ambiente di programmazione come Java viene gestita attraverso il riferimento all’oggetto. Anche se due oggetti hanno lo stesso stato, essi sono distinti e l’operazione su uno non influenzerà l’altro.

## Inizializzazione e costruttori

**Costruttore:** Metodo speciale che alloca un nuovo oggetto in memoria

`public NomeClasse(){}`

### Caratteristiche:

- Deve avere lo **stesso nome** della classe in cui è definito.
- A differenza di altri metodi, un costruttore **non ha un tipo di ritorno**, nemmeno void.
- Viene **automaticamente chiamato quando si crea un nuovo oggetto tramite** **new**
### Tipi:
- **Costruttore Predefinito**: Se non si definisce un costruttore per una classe, Java fornisce automaticamente un costruttore predefinito senza parametri che non fa nulla se non chiamare il costruttore della superclasse.
- **Costruttore Senza Parametri:** È un costruttore definito dall’utente senza argomenti. Serve per creare un oggetto senza passare valori espliciti e spesso assegna valori di default agli attributi.
- **Costruttore Con Parametri:** Questo tipo di costruttore permette di passare argomenti al momento della creazione di un oggetto, consentendo di inizializzare immediatamente lo stato dell’oggetto con valori specifici.
- Se il costruttore viene definito con dei parametri il costruttore di default viene disabilitato
## `this`
La keyword `this` rappresenta l'indirizzo di memoria dell'istanza corrente dell'oggetto in cui ci si trova. Viene utilizzata principalmente per risolvere problemi di shadowing (quando un parametro di un metodo ha lo stesso nome di un attributo della classe), e per gestire agevolmente le associazioni bidirezionali tra oggetti.
## Incapsulamento

L’incapsulamento è la pratica di **nascondere i dettagli interni di un oggetto** e di esporre solo ciò che è necessario. Questo è di solito realizzato con l’uso di modificatori di accesso (public e private, protected, default) e fornendo metodi pubblici (getter e setter) per accedere a quegli attributi.

- **Getter**: leggere attributo privato
````java
public int getVar() {

        return var;

    }
````
- **Setter**:  sovrascrivere attributo privato
````java
public void setVar(int v) {

        var = v;
    }
````
Setter può essere modificato per essere più selettivo, ad esempio aggiungendo dei if-else statement, proteggendo il campo da assegnazioni non valide o dannose.

