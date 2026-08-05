---
Materia: Architettura degli elaboratori
tags:
  - logica_combinatoria
  - logica_sequenziale
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 2.1'
Imparato: false
Ordine: 201
aliases:
  - circuito combinatorio
  - circuito sequenziale
---

# Circuiti combinatori e sequenziali

## Il circuito come scatola nera
Un circuito digitale è un **modulo** che si può vedere come una *black box* con:
- uno o più **terminali di ingresso** a valori discreti;
- uno o più **terminali di uscita** a valori discreti;
- una **specifica funzionale** che descrive la relazione tra ingressi e uscite;
- una **specifica temporale** che descrive il ritardo tra il cambio degli ingressi e
  il cambio delle uscite.

## Nodi ed elementi
Un circuito è una rete che elabora variabili a valori discreti, ed è composto da:
- **elementi**: essi stessi circuiti (con ingressi, uscite, specifiche);
- **nodi**: i fili che collegano gli elementi. Un nodo è classificato come
  **ingresso**, **uscita** o **interno** (nodo di collegamento non visibile
  dall'esterno).

## La classificazione fondamentale
| Tipo | Le uscite dipendono da… | Ha memoria? |
|---|---|---|
| **Combinatorio** | solo dai **valori correnti** degli ingressi | no |
| **Sequenziale** | dai valori **correnti e precedenti** degli ingressi | sì (**stato**) |

## Regole di composizione combinatoria
Un circuito è combinatorio se e solo se:
1. ogni suo elemento è **esso stesso combinatorio**;
2. ogni nodo è o un ingresso del circuito, o è connesso a **esattamente una** uscita di
   un elemento;
3. il circuito **non contiene cammini ciclici**: ogni percorso attraversa ogni nodo al
   massimo una volta.

> [!warning] Il punto 3 è quello che discrimina
> Un anello di retroazione (*cyclic path*) rende il circuito sequenziale, non
> combinatorio. → [[Progetto sincrono e race condition]]

## Notazione dei bus
Quando il numero di bit non è rilevante o è ovvio dal contesto, si usa una linea
singola con una **barra e un numero** che indica la larghezza del bus (es. `/8`).

## Da ricordare
- Specifica funzionale + specifica temporale = descrizione completa di un modulo.
- Combinatorio ⇔ nessun cammino ciclico e tutti gli elementi combinatori.

## Domande flash
1. Un circuito con un solo NOT retroazionato su se stesso è combinatorio?
2. Cosa distingue un nodo interno da un nodo di uscita?
