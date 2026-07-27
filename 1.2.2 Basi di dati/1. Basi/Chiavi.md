---
Materia: Basi di dati
tags:
  - UML
  - ER
Link risorse:
Imparato: true
Ordine:
---
In un database relazionale una **chiave** è uno o più attributi che identificano le tuple di una tabella (relazione) in modo univoco.
Le chiavi permettono l'accesso ai dati della tabella(relazione) perché identificano univocamente le tuple (record) della tabella. Porre delle chiavi inoltre significa imporre dei [[Vincoli di integrità|vincoli]] su quei attributi.
### Chiave primaria
In una tabella relazionale la chiave primaria è una chiave che non contiene valori `Null`.
Se in una tabella non esiste un attributo in grado di diventare chiave primaria, allora devo aggiungere alla tabella un nuovo attributo apposito per svolgere questo scopo.
###  Superchiave
Un insieme di attributi è una superchiave se e solo se non contiene tuple duplicate al suo interno.
Una superchiave è una chiave se è una **superchiave minimale** ossia se non contiene altre superchiavi al suo interno. L'insieme delle superchiavi minimali sono le **chiavi candidate**. Tra le chiavi candidate si sceglie la chiave primaria.
### Chiave esterna (foreign key)
La chiave esterna lega due tabelle insieme. La chiave esterna di una tabella corrisponde ad un attributo legato alla chiave di un'altra tabella in cui è in relazione.