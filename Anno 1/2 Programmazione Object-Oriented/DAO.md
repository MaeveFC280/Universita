---
Materia: Programmazione Object-Oriented
tags:
  - Java
  - DB
Link risorse:
Libro:
Imparato: true
Ordine: 17.5
aliases:
  - Interfaccia
  - EBCD
  - JDBC
---
## Persistenza
**Persistenza**: Come salvare, leggere, modificare e cancellare dati.
[[Modello Entity-Boundary-Controll]]->**EBCD**
Il quarto livello D contiene le classi che gestiscono il [[Database]], e si chiamano **DAO** (Data Access Object)
*Esempio: Mentre `Studente` rappresenta il singolo studente e contiene i suoi dati (matricola, nome, cognome), `StudenteDAO`  gestisce il salvataggio e e recupero degli studenti:*
````java
public class StudenteDAO {
    public Studente getStudente(String matricola) {
        // query al database
    }
    public void save(Studente studente) {
        // INSERT o UPDATE nel database
    }
    public void delete(String matricola) {
        // DELETE dal database
    }
    public List<Studente> getStudentiByCorso(String corso) {
        // SELECT dal database
    }
}
````
## JDBC
Il Controller interagisce con le **interfacce**, non con le implementazioni concrete.
**L'interfaccia è un contratto che definisce quali sono le operazioni che la classe deve avere.**
Non si può mai istanziare un'interfaccia con la keyword `new`.![[DAO-1783249125308.webp]]
![[DAO-1783249153937.webp]]
## Middleare
![[DAO-1783249200494.webp]]
### Embedded SQL
Il programma interagisce direttamente con il DBMS. Le istruzioni SQL sono compilate utilizzando un **precompilatore** del DBMS
- SQL diventa parte integrante del codice
### Call level interface
Il programma accede al DBMS tramite un'interfaccia standard. Le istruzioni SQL non vengono compilate ma mandate al DBMS in run-time
- Il DBMS può essere sostituito
- La stessa interfaccia può interagire con più DBMS
Si hanno:
- **ODBC**: 
	- Permette l'accesso a dati in differenti DBMS
	- Supportato da ogni DBMS commerciale
	- Converte le richieste SQL in linguaggio comprensibile da ogni DBMS
	- Lo sviluppatore non ha bisogno di conoscere l'interfaccia
	- È ostico e con pochi parametri
	- Procedurale
	- Utilizza interfacce C
- OLE-DB
- ADO
- UDA
- **JDBC** API: Insieme di classi ed interfacce che forniscono una **API standard** per operare con DBMS in **java puro**.
	- Base per package di alto livello
	1. Stabilisce una connessione con il DBMS
	2. Invia le istruzioni SQL al DBMS
	3. Processa i risultati restituiti dalla DBMS
	- Non sono necessari drivers
	- Sintassi URL
	- Mappa i tipi SQL in tipi java
	- Una classe speciale si occupa di attivare i drivers corretti
	- Tutte le classi implementate sono interfacce implementate dallo specifico driver

![[DAO-1783249852936.webp]]
### Passi essenziali
![[DAO-1783334707133.webp|390|666x449]]

#### Import
`import java.sql.*`
#### Registrazione del driver
````java
try
{
	Class.forName(NOME_DRIVER);
}
catch(ClassNotFoundException)
{ //Driver non trovato
}
````
Il metodo `Class.forName(NOME_DRIVER)` forza il caricamento del driver.
Il DriverManager mantiene una lista di classi Driver. 
L'inizializzatore statico del driver viene chiamato al caricamento della classe
````java
//all'interno del driver
public class MyDriver
{
	static
	{
		new myDriver();
	}
	
	public myDriver()
	{ 
		java.sql.DriverManagerregister(this);
	}
}
````
##### MySQL
`String driver="com.mysql.cj.jdbc.Driver";`
##### Oracle
`String driver="oracle.jdbc.OracleDriver";`
##### JDBC-ODBC
`String driver="sun.jdbc.odbc.JdbcOdbcDriver";`
##### PostegreSQL
`String driver="org.postgresql.Driver";`
#### Ottenere una connessione
L'oggetto Connection rappresenta il canale di comunicazione con il DBMS. Una sessione di connessione include istruzioni SQL che restituiscono valori tramite la connessione
`Connection con = DriverManager.getConnection(URL_MY_DATABASE)`
L'**url** è una stringa costituita da più porzioni: `protocollo:sottoprotocollo:databaseName`
#### Eseguire una query
Le istruzioni SQL sono eseguite tramite **Statement**, un oggetto unico per tutta la procedura che cambia stringa per ogni istruzione.
````java
try{
	Statement st = con.createStatement(); //connessione
	ResultSet rs = st.executeQuery("SELECT nome FROM Studenti"); //query
}
catch (SQLException sqe){
	//problema
}
````
- `executeQuery` interroga la DB
- `executeUpdate` per statement di definizione o aggiornamento
- `execute()` per query di tipo sconosciuto
	- restituisce true se `ResultSet` è disponibile 
	- bisogna chiamare `getResult` per recuperare le informazioni
##### PreparedStatement
Statement SQL **precompilato**: il DBMS lo analizza una volta e lo tiene in cache. Migliora le prestazioni se la query è eseguita molte volte e protegge dalla **SQL injection** (i valori non sono concatenati nella stringa).
- Usa i segnaposto `?`, numerati **da 1**.

```java
String comando = "UPDATE Studenti SET esami = ? WHERE Matricola LIKE ?";
PreparedStatement ps = con.prepareStatement(comando);
ps.setInt(1, 13);
ps.setString(2, "N86245389");
ps.executeUpdate();
```

- Ogni `?` si riempie con `setInt`, `setString`, `setDate`… a seconda del tipo.
- Per passare un valore NULL: `ps.setNull(indice, java.sql.Types.VARCHAR)`.
- È la scelta standard rispetto allo `Statement` semplice.

##### CallableStatement
Classe JDBC per richiamare **stored function** e **stored procedure** salvate sul DBMS. Usa la sintassi di escape con parentesi graffe `{ }`.
- Function (restituisce un valore):

```java
CallableStatement cs = con.prepareCall("{ ? = call autentica(?, ?) }");
cs.registerOutParameter(1, Types.INTEGER); // valore di ritorno
cs.setString(2, matricola);
cs.setString(3, password);
cs.execute();
int esito = cs.getInt(1);
```

- Procedure (non restituisce nulla → senza `? =`):

``` java
CallableStatement cs = con.prepareCall("{ call creaProgetto(?, ?, ?, ?) }");
cs.setString(1, codiceInvito);
// ... altri parametri
cs.execute();
```

- `registerOutParameter` = dice a JDBC che quel `?` è un output, non un input.
- In PostgreSQL le function si possono anche chiamare come query: `SELECT autentica(?, ?)`.

#### ResultSet — estrarre i dati

I risultati di una SELECT sono salvati in un `ResultSet`, una struttura con un **cursore** che punta a una riga alla volta.

- Dopo `executeQuery()` il cursore è posizionato **prima** della prima riga.
- `next()` avanza di una riga e restituisce `false` quando non ce ne sono più.


```java
ResultSet rs = ps.executeQuery();
while (rs.next()) {
    String nome  = rs.getString("nome");
    String descr = rs.getString("descrizione");
    // costruisci qui l'oggetto e aggiungilo a una lista
}
```

Lettura valori con `getXXX(colonna)`:

- La colonna si indica per **nome** (`getString("nome")`, case insensitive) o per **numero** (`getString(1)`, parte da 1).
- Il driver converte il tipo SQL in tipo Java (es. VARCHAR → String, DATE → java.sql.Date, INTEGER → int).

Navigazione cursore: `first()`, `last()`, `next()`, `previous()`, `beforeFirst()`, `afterLast()`, `absolute(int)`, `relative(int)`. (JDBC 1.0 permetteva solo in avanti.)

##### Dati NULL

`getXXX()` non distingue bene il NULL:

- `getString` su NULL → `null`
- `getInt` su NULL → **0**
- booleano su NULL → `false`

Per sapere davvero se il valore era NULL: leggere la colonna e chiamare subito `rs.wasNull()`.


```java
Date scad = rs.getDate("dataScadenza");
if (rs.wasNull()) scad = null;   // es. scadenza opzionale
```

#### Pulizia (Clean up)

Chiudere le risorse nell'ordine **inverso** all'apertura:


```java
rs.close();
st.close();
con.close();
```

Meglio ancora il **try-with-resources**, che chiude tutto in automatico (anche in caso di eccezione):



```java
try (Connection con = DriverManager.getConnection(url, user, pwd);
     PreparedStatement ps = con.prepareStatement(sql);
     ResultSet rs = ps.executeQuery()) {
    while (rs.next()) { ... }
} // chiusura automatica
```

### Sequenza delle operazioni

Catena degli oggetti JDBC:

`Applicazione → DriverManager → Driver → Connection → Statement → DBMS → ResultSet`

Qualsiasi errore lungo il percorso diventa una `SQLException`, che va gestita.


### Singleton pattern (gestione della connessione)

**Design pattern creazionale** (Gang of Four, 1995). La connessione al DB serve in tanti punti (ogni Control/DAO), ma aprirla ogni volta è costoso: si vuole **una sola istanza** condivisa, con punto d'accesso globale.

- **Scopo**: garantire che una classe abbia una sola istanza e fornire un accesso globale ad essa.
- **Applicabilità**: quando deve esistere esattamente un'istanza nota a tutte le classi che la usano (es. una sola coda di stampa per molte stampanti).


```java
public class Singleton {
    private static Singleton istanza = null; // unica istanza
    private Singleton() {}                    // costruttore privato: no "new" dall'esterno
    public static Singleton getSingleton() {
        if (istanza == null) {
            istanza = new Singleton();
        }
        return istanza;
    }
}
```

Tre chiavi:

- costruttore `private` → nessuna classe esterna può istanziare;
- istanza `static` → una sola, condivisa;
- `getSingleton()` → unico accesso: crea la prima volta, poi restituisce sempre la stessa.

Nota: questa versione base **non è thread-safe** (ok per app desktop a singolo utente).

Applicazione tipica: una classe `GestoreConnessione` che tiene l'unica `Connection` e la fornisce a tutti i DAO/Control → supporta la separazione tra logica applicativa e accesso ai dati.
