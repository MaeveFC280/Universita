---
Materia: Basi di dati
tags:
  - DML
  - SQL
Imparato: true
Ordine: 8
---
Può essere fatto specificando i valori o estraendoli/calcolandoli dalla base di dati
````mysql
INSERT INTO <nome_tabella> [<elenco_attributi>]
	VALUES [<lista_valori>]
````
- **Omettendo l'elenco degli attributi uso automaticamente l'ordine in cui sono definiti gli attributi, altrimenti è possibile indicare un ordine diverso o solo alcuni attributi**
- Vanno rispettati i formati di definizione dei tipi
- Vanno specificati i valori di tutti gli attributi `NOT NULL`
- **È possibile usare `SELECT` per calcolare il valore degli attributi inseriti**
````mysql
INSERT INTO <nome_tabella> [<lista_attributi>](
	SELECT <lista_attributi>
	FROM <nome_tabella>
	WHERE <condiz_booleana>)
````
- La lista nella `SELECT` deve corrispondere alla lista degli attributi dichiarati nella `INSERT` o nella definizione di tabella
- È possibile inserire più righe contemporaneamente 
````mysql
INSERT INTO <nome_tabella> [<elenco_attributi>]
	VALUES [<lista_valori>],[<lista_valori>]
````
