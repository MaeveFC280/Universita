---
tags: [architettura, combinatoria, booleana, cap2]
capitolo: 2
sezione: "2.3.3 / 2.5.2"
pagine_pdf: 79-89
---

# Teorema di De Morgan e bubble pushing

## Teorema di De Morgan (T12)
Il complemento del **prodotto** è la **somma** dei complementi; il complemento della
**somma** è il **prodotto** dei complementi.

$$\overline{AB} = \overline{A} + \overline{B} \qquad\qquad \overline{A+B} = \overline{A}\ \overline{B}$$

Conseguenza sui simboli: una porta **NAND** è equivalente a una **OR con i pallini
sugli ingressi**; una porta **NOR** è equivalente a una **AND con i pallini sugli
ingressi**.

## Il pallino (*bubble*)
Il cerchietto di inversione si chiama **bubble**. Intuitivamente si può pensare che il
bubble "attraversi" la porta: passandoci, la porta **cambia corpo** da AND a OR (o
viceversa) e i bubble si spostano dall'altro lato.

## Regole del bubble pushing
- Spostare un bubble **indietro** (dall'uscita verso gli ingressi) o **avanti**
  (dagli ingressi verso l'uscita) **cambia il corpo** della porta da AND a OR e viceversa.
- Spostare un bubble dall'uscita indietro verso gli ingressi mette i bubble su **tutti**
  gli ingressi.
- Spostare i bubble presenti su **tutti** gli ingressi avanti verso l'uscita mette un
  bubble sull'uscita.

## Procedura pratica per ripulire uno schema
1. **Parti dall'uscita** del circuito e lavora verso gli ingressi.
2. Sposta i bubble sull'uscita finale indietro, per farli annullare con altri bubble o
   per raggiungere gli ingressi.
3. Lavorando a ritroso, quando incontri una porta, **ridisegnala** in modo che i suoi
   bubble di ingresso si annullino con i bubble di uscita della porta precedente.
   Se non si annullano, inserisci un inverter.

Lo scopo: eliminare le coppie di inversioni consecutive (che si annullano per T4,
involuzione) e ottenere uno schema con meno porte.

> [!tip] Uso tipico
> La logica CMOS realizza naturalmente porte **invertenti** (NAND, NOR). Il bubble
> pushing serve a convertire uno schema AND/OR "logico" in uno schema NAND/NOR
> "implementabile", senza cambiare la funzione.

## Da ricordare
- $\overline{AB} = \overline{A}+\overline{B}$; $\overline{A+B} = \overline{A}\,\overline{B}$.
- Spostare un bubble ⇒ AND↔OR.
- Due bubble in serie si annullano.

## Domande flash
1. Trasforma $\overline{\overline{A}\,\overline{B} + \overline{C}}$ eliminando le
   inversioni annidate.
2. Un NAND a 3 ingressi è equivalente a quale porta con bubble sugli ingressi?
