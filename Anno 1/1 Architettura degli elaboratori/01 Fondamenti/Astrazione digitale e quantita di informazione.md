---
Materia: Architettura degli elaboratori
tags:
  - astrazione
  - Binario
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 1.3'
Imparato: false
Ordine: 102
aliases:
  - astrazione digitale
  - quantità di informazione
  - bit
---

# Astrazione digitale e quantità di informazione

## Continuo vs discreto
La maggior parte delle grandezze fisiche è **continua**: tensione, posizione, tempo
possono assumere infiniti valori. I sistemi digitali invece rappresentano
l'informazione con **variabili a valori discreti**, cioè con un numero finito di
valori distinti.

Un segnale continuo contiene teoricamente una quantità **infinita** di informazione,
perché può assumere infiniti valori; in pratica il rumore ne limita la precisione.

## Quantità di informazione
Per una variabile discreta con $N$ stati distinti, l'informazione $D$ si misura in bit:

$$D = \log_2 N \ \text{bit}$$

- variabile binaria ($N=2$): $\log_2 2 = 1$ bit
- ingranaggio decimale di Babbage ($N=10$): $\log_2 10 \approx 3{,}322$ bit

## La scelta del binario
Quasi tutti i calcolatori elettronici usano una rappresentazione **binaria**: una
tensione alta indica `1`, una tensione bassa indica `0`. Il motivo è pratico: distinguere
due soli livelli è molto più robusto al rumore che distinguerne dieci.

> [!info] Sinonimi usati nel libro
> `1` = TRUE = HIGH  ·  `0` = FALSE = LOW

## Logica booleana
George Boole sviluppò un sistema di logica su variabili che possono essere solo TRUE o
FALSE: è la **logica booleana**, base di tutto il progetto digitale
(→ [[Assiomi e teoremi dell algebra di Boole]]).

## Da ricordare
- $D = \log_2 N$: la formula che quantifica l'informazione di una variabile discreta.
- "bit" = *binary digit*.
- La scelta binaria non è teoricamente obbligata, ma è la più robusta.

## Domande flash
1. Quanti bit di informazione trasporta una variabile a 8 stati?
2. Perché i calcolatori non usano 10 livelli di tensione?
