---
Materia: Basi di dati
tags:
  - progettazione_concettuale
  - UML
  - modello_logico
Link risorse:
Imparato: true
aliases:
Ordine: 4
---
Il [[Mapping del modello relazionale|mapping]] verso uno schema logico parte dallo schema concettuale ristrutturato, cioè uno schema in cui:
-  **No attributi multipli
- **No atributi composti**
- **No gerarchie**
Vanno dunque effettuate varie azioni:
1. Eliminazione attributi strutturati
2. Eliminazione attributi multivalore
3. Eliminazione delle [[Gerarchie in UML|generalizzazioni]] 
4. Scelta dei[[Chiavi|identificatori primari]]
5. Analisi delle ridondanze
6. Partizionamento/accorpamento di entità e associazioni
## Eliminazione attributi strutturati e multivalore
Vanno create delle classi apposite per contenere codesti attributi![[Screenshot 2026-06-11 alle 10.34.38.png]]

![[Screenshot 2026-06-11 alle 10.35.29.png]]
## Rimozione gerarchie
1. Accorpamento della classe generale nelle specializzate
	- Solo su gerarchie totali e disgiunte
	- Devo gestire le associazioni in modo da rispettare i vincoli
	- Tutto ciò che era presente nella classe padre va trasferito nelle classi figlie
2. Fusione delle classi specializzate nella generalizzata
	- Indipendente dal tipo di gerarchia 
	- Trasferisco tutti gli attributi delle figlie nella classe padre
	- Necessito di un attributo discriminativo per distinguere una sottoclasse da un'altra
3. Sostituzione delle generalizzazioni con associazioni
	- Indipendente dal tipo di gerarchia 
	- Sostituisce le gerarchie con associazioni semplici
	- Indico la molteplicità
## Scelta identificatori
Scelgo la [[Chiavi|superchiave]] più importante nell'applicazione. Nel caso non ci fossero candidati soddisfacenti può essere creato un surrogato (id)
## Ridondanze
Elimino gli attributi derivabili/calcolabili:
- Da attributi della stessa entità
- Da attributi di altre entità
- Dal conteggio delle occorrenze
Anche le associazioni ricavabili dalla navigazione vanno eliminate:
- In presenza di cicli![[Screenshot 2026-06-11 alle 10.44.31.png]]