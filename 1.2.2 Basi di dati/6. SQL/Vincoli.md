---
Materia: Basi di dati
tags:
  - SQL
Link risorse: "[W3schools](https://www.w3schools.com/sql/sql_constraints.asp)"
Imparato: true
Ordine: 12
aliases:
  - assertion
---
Esistono varie parole chiave per impartire dei [[Vincoli di integrità]] su una tabella SQL.

- [`NOT NULL`](https://www.w3schools.com/sql/sql_notnull.asp) fa in modo che l'attributo della tupla debba avere un valore non nullo
```MYSQL
attributeName VARCHAR(100) NOT NULL
```
- [`PRIMARY KEY`](https://www.w3schools.com/sql/sql_primarykey.asp) garantisce valori unici ed esistenti per ogni tupla
```MYSQL
attributeName int PRIMARY KEY
```
 - [`FOREIGN KEY`](https://www.w3schools.com/sql/sql_foreignkey.asp)stabilisce un legame tra due tabelle
````MYSQL
FOREIGN KEY (IDname)  
REFERENCES TABLE2(pkName)
````
- [`DEFAULT<valore>`](https://www.w3schools.com/sql/sql_default.asp) assegna un valore predefinito ad un attributo
```MYSQL
attributeName int DEFAULT 5
```
- [`CHECK`](https://www.w3schools.com/sql/sql_check.asp) dopo definizione di attributo o dominio. Può controllare le singole tuple.
```MYSQL
ADD CHECK (Age >= 18)
```
- È possibile assegnare un nome ai vincoli con [`ADD CONSTRAINT`](https://www.w3schools.com/sql/sql_constraints.asp) sia quando viene creata la tabella sia quando viene modificata
```MYSQL
ALTER TABLE TableName  
ADD CONSTRAINT unq_name UNIQUE (attribute1,attribute2)
```

## Assertion
````mysql
CREATE ASSERTION no_empty_departments CHECK  
(NOT EXISTS  
  (SELECT 'an empty department' 
     FROM dept d 
     WHERE NOT EXISTS 
                   (SELECT 'an employee in the department' 
                      FROM emp e 
                      WHERE e.deptno = d.deptno)));
````

