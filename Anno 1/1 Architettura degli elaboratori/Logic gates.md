---
Materia: Architettura degli elaboratori
tags:
  - Logica
Link risorse: https://youtu.be/QZwneRb-zqA?si=hfEXSbPngFlYnGYa&t=50
Libro:
Imparato: false
Ordine: 2
aliases:
  - logica booleana
---
## NOT
**NOT** inverte il segnale. Vero diventa falso e falso diventa vero

| INPUT | OUTPUT |
| ----- | ------ |
| 1     | 0      |
| 0     | 1      |

## AND
**AND** restituisce vero solo se entrambi gli input sono veri

| A   | B   | OUTPUT |
| --- | --- | ------ |
| 1   | 0   | 0      |
| 0   | 1   | 0      |
| 1   | 1   | 1      |
| 0   | 0   | 0      |

## OR
**OR** restituisce vero se almeno uno dei input è vero

| A   | B   | OUTPUT |
| --- | --- | ------ |
| 1   | 0   | 1      |
| 0   | 1   | 1      |
| 1   | 1   | 1      |
| 0   | 0   | 0      |

## NAND
**NAND** restituisce vero se gli input non sono entrambi veri (contrario di AND)

| A   | B   | OUTPUT |
| --- | --- | ------ |
| 1   | 0   | 1      |
| 0   | 1   | 1      |
| 1   | 1   | 0      |
| 0   | 0   | 1      |


## XOR
**XOR** restituisce vero se uno solo dei input è vero

| A   | B   | OUTPUT |
| --- | --- | ------ |
| 1   | 0   | 1      |
| 0   | 1   | 1      |
| 1   | 1   | 0      |
| 0   | 0   | 0      |
## Porprietà
I logic gates sono combinabili tra di loro e possiedono delle proprietà:
- Commutativo
- palle
- vabbe
## Combinazioni di NAND
Si possono ricavare tutti i gates da NAND.
### NOT
![[Logic gates-1785674899875.webp]]
### AND
![[Logic gates-1785674529626.webp]]
### OR
Ora che sappiamo come ricavare NOT da NAND, possiamo utilizzarlo per ricavare a sua volta OR. Questo circuito sappiamo quindi che è ricreabile solo con NAND sostituendo i NOT con l'immagine relativa.
![[Logic gates-1785675053477.webp]]