---
Materia: Architettura degli elaboratori
tags:
  - logica_sequenziale
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 5.4'
Imparato: false
Ordine: 508
aliases:
  - contatore
  - shift register
  - registro a scorrimento
---

# Contatori e shift register

Due blocchi sequenziali fondamentali costruiti a partire dai registri.

## Contatore binario
Un **contatore binario a $N$ bit** è un circuito aritmetico sequenziale con ingressi di
**clock** e **reset** e un'uscita a $N$ bit, $Q$.

Comportamento: il reset inizializza l'uscita a 0; poi il contatore **incrementa** l'uscita
di 1 a ogni **fronte di salita** del clock, avanzando attraverso tutti i $2^N$ valori
possibili e poi ripartendo da 0 (conteggio **modulo $2^N$**).

### Realizzazione
Un **sommatore** e un **registro resettabile** in anello: il sommatore aggiunge 1
all'uscita del registro, il risultato torna nell'ingresso del registro.

$$Q' = Q + 1$$

### Varianti
- **Contatore up/down**: un segnale di direzione seleziona $+1$ o $-1$.
- **Contatore con enable**: conta solo quando l'enable è attivo.
- **Contatore caricabile**: si può inizializzare a un valore arbitrario.
- **Divisore di frequenza**: il bit più significativo di un contatore a $N$ bit è
  un'onda quadra a frequenza $f_{clk}/2^N$.

### Usi
Divisione di frequenza, generazione di indirizzi sequenziali, temporizzazione,
**decomposizione di FSM** (→ [[Procedura di progetto di una FSM]]).

## Shift register (registro a scorrimento)
Ha un **clock**, un ingresso **seriale** $S_{in}$, un'uscita **seriale** $S_{out}$ e $N$
uscite **parallele** $Q_{N-1:0}$.

Comportamento: a ogni fronte di salita del clock, **un nuovo bit entra** da $S_{in}$ e
tutti i bit memorizzati **scorrono** di una posizione; il bit più vecchio esce da
$S_{out}$.

### Realizzazione
$N$ flip-flop collegati **in serie**: l'uscita di ciascuno è l'ingresso del successivo.
Alcuni shift register hanno anche un segnale di **reset** per inizializzare tutti i
flip-flop.

## Convertitori seriale/parallelo
> [!tip] L'uso più importante
> Uno shift register **è** un convertitore **seriale-parallelo**: converte un flusso
> seriale di bit in una parola parallela.
>
> Aggiungendo un ingresso di **caricamento parallelo** (con un mux davanti a ogni
> flip-flop) si ottiene un convertitore **parallelo-seriale**: carica $N$ bit in
> parallelo e li emette uno alla volta.

Applicazione tipica: le comunicazioni. I dati viaggiano in **seriale** su un filo (per
risparmiare piedini e fili) e vengono elaborati in **parallelo** dentro il chip.

### Scan chain (cenno)
Gli shift register con caricamento parallelo si usano anche per il **test** dei chip:
si collegano tutti i flip-flop in una catena (*scan chain*) che permette di leggere e
scrivere l'intero stato interno dall'esterno, con pochi piedini.

## Da ricordare
- Contatore = sommatore + registro resettabile in anello; conta modulo $2^N$.
- Shift register = $N$ flip-flop in serie; 1 bit entra, tutti scorrono.
- Shift register con load parallelo = convertitore parallelo↔seriale.

## Domande flash
1. Quale bit di un contatore a 8 bit ha frequenza $f_{clk}/256$?
2. Come si trasforma uno shift register in un convertitore parallelo-seriale?
