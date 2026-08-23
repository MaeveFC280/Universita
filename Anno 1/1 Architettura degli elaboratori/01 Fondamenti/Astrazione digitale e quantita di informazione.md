---
Materia: Architettura degli elaboratori
tags:
  - astrazione
  - Binario
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 1.3'
Imparato: true
Ordine: 102
aliases:
  - astrazione digitale
  - quantità di informazione
  - bit
---
## Continuo vs discreto
La maggior parte delle grandezze fisiche è **continua**: tensione, posizione, tempo possono assumere infiniti valori. I sistemi digitali invece rappresentano l'informazione con **variabili a valori discreti**, cioè con un numero finito di valori distinti.

Un segnale continuo contiene teoricamente una quantità **infinita** di informazione, perché può assumere infiniti valori; in pratica il rumore ne limita la precisione.

## Quantità di informazione
Per una variabile discreta con $N$ stati distinti, l'informazione $D$ si misura in bit:

$$D = \log_2 N \ \text{bit}$$

- variabile binaria ($N=2$): $\log_2 2 = 1$ bit
- ingranaggio decimale di Babbage ($N=10$): $\log_2 10 \approx 3{,}322$ bit
## Terminologia dei raggruppamenti di bit
- **byte** = 8 bit
- **nibble** = 4 bit (mezzo byte)
- una cifra [[Sistemi di numerazione binario e esadecimale|esadecimale]] memorizza un nibble; **due cifre hex = un byte intero**
- **word** = l'unità di dato su cui lavora il microprocessore. La dimensione dipende dall'architettura: processori a 64 bit operano su word di 64 bit, i più vecchi a 32 bit.
## La scelta del binario
Quasi tutti i calcolatori elettronici usano una rappresentazione **binaria**: una tensione alta indica `1`, una tensione bassa indica `0`. Il motivo è pratico: distinguere due soli livelli è molto più robusto al rumore che distinguerne dieci.

> [!info] Sinonimi
> `1` = TRUE = HIGH   ·   `0` = FALSE = LOW

## Prefissi: la coincidenza dei 1024
Per pura coincidenza numerica:

$$2^{10} = 1024 \approx 10^3 \qquad 2^{20} \approx 10^6 \qquad 2^{30} \approx 10^9$$

Quindi in ambito digitale:
- $2^{10}$ byte = 1024 byte = 1 **kilobyte** (KB)
- $2^{20}$ byte = 1 **megabyte** (MB)
- $2^{30}$ byte = 1 **gigabyte** (GB)
## Logica booleana
George Boole sviluppò un sistema di logica su variabili che possono essere solo TRUE o FALSE: è la [[Assiomi e teoremi dell algebra di Boole|logica booleana]], base di tutto il progetto digitale.
