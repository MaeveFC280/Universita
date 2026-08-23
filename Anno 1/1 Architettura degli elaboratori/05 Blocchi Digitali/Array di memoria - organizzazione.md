---
Materia: Architettura degli elaboratori
tags:
  - memoria
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 5.5.1'
Imparato: true
Ordine: 509
aliases:
  - array di memoria
  - bit cell
  - word line
  - bit line
---
I sistemi digitali richiedono **memorie** per conservare grandi quantità di dati. I registri costruiti con [[Flip-flop D e registri|flip-flop]] sono un tipo di memoria, ma memorizzano piccole quantità di dati.
## Struttura logica
Una memoria è organizzata come un **array bidimensionale** di celle:
- la **profondità** (*depth*) è il numero di **righe**;
- la **larghezza** (*width*) è il numero di **colonne**, cioè la dimensione della parola.

Un array $2^N \times M$ ha:
- $N$ bit di **indirizzo** (*Address*), che selezionano una delle $2^N$ righe;
- $M$ bit di **dato** (*Data*), la parola letta o scritta.

La dimensione totale è $2^N \times M$ bit.

## Bit cell, wordline e bitline
Gli array di memoria sono costruiti come array di **bit cell**, ognuna delle quali memorizza **1 bit**.

Ogni bit cell è connessa a:
- una **wordline** (linea di parola), condivisa da tutte le celle della stessa **riga**;
- una **bitline** (linea di bit), condivisa da tutte le celle della stessa **colonna**.

Per ogni combinazione degli ingressi di indirizzo, **un [[Decoder|decoder]] attiva esattamente una wordline, abilitando la riga corrispondente.

## Operazione di lettura
1. La bitline viene inizialmente lasciata **flottante (Z)**.
2. Si attiva la **wordline** della riga selezionata.
3. La bit cell si connette alla bitline e la **tira** verso 0 o 1, secondo il bit memorizzato.
4. Il valore viene letto (e in genere amplificato da un *sense amplifier*).

## Operazione di scrittura
1. La bitline viene **forzata** al valore desiderato (0 o 1) da un driver forte.
2. Si attiva la **wordline**.
3. Il driver **sovrascrive** il contenuto della bit cell.

Il driver di scrittura deve essere **più forte** della cella, per poterla ribaltare.

## Porte
Tutte le memorie hanno una o più **porte** (*ports*). Ogni porta fornisce accesso di lettura e/o scrittura a **un indirizzo**.

- Memoria a **porta singola**: si accede a un solo indirizzo per volta.
- Memoria **multiporta**: si può accedere a **più indirizzi simultaneamente**.

> [!important] Esempio: il register file
> Il *register file* di un processore è tipicamente una memoria a **tre porte**: due porte di **lettura** (per leggere due [[Operandi|operandi]] contemporaneamente) e una porta di
> **scrittura**, come avviene nei [[Register file ROM e logic array|register file e nelle ROM]].
