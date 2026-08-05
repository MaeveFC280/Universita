---
tags: [architettura, fondamenti, logica, cap1]
capitolo: 1
sezione: "1.5"
pagine_pdf: 36-39
---

# Porte logiche

Le **porte logiche** sono circuiti digitali elementari: uno o più ingressi binari, una
uscita binaria determinata dalla funzione della porta.

## Porte a un ingresso
| Porta | Funzione | Note |
|---|---|---|
| **NOT** (inverter) | $Y = \overline{A}$ | il pallino (*bubble*) indica l'inversione |
| **BUFFER** | $Y = A$ | logicamente inutile, elettricamente utile: rigenera il segnale e pilota carichi elevati |

## Porte a due ingressi
| Porta | Funzione | Uscita alta quando… |
|---|---|---|
| **AND** | $Y = AB$ | **tutti** gli ingressi sono 1 |
| **OR** | $Y = A+B$ | **almeno un** ingresso è 1 |
| **XOR** | $Y = A \oplus B$ | un numero **dispari** di ingressi è 1 |
| **NAND** | $Y = \overline{AB}$ | negazione dell'AND |
| **NOR** | $Y = \overline{A+B}$ | negazione dell'OR |
| **XNOR** | $Y = \overline{A \oplus B}$ | gli ingressi sono **uguali** (comparatore di uguaglianza) |

> [!tip] Trucco mnemonico
> - AND: la "A" di *All*.
> - OR: basta "uno o l'altro".
> - XOR a $N$ ingressi = **parità**: 1 se il numero di ingressi a 1 è dispari.
> - XNOR a 2 ingressi = **uguaglianza**.

## Porte a più ingressi
La maggior parte delle porte si estende naturalmente a $N$ ingressi: un NOR a 3
ingressi vale 1 solo se **tutti** gli ingressi sono 0.

## Da ricordare
- Il pallino sull'uscita = inversione.
- XOR = parità dispari; XNOR = uguaglianza.
- NAND e NOR sono porte **universali**: con esse si costruisce qualunque funzione.

## Domande flash
1. Scrivi la tabella di verità di un XOR a 3 ingressi.
2. Quando vale 1 un NAND a 4 ingressi?

Collegato a: [[Assiomi e teoremi dell algebra di Boole]] · [[Teorema di De Morgan e bubble pushing]]
