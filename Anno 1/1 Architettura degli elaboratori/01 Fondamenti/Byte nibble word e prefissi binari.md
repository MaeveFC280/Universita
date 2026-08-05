---
Materia: Architettura degli elaboratori
tags:
  - Binario
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 1.4.4-1.4.5'
Imparato: false
Ordine: 104
aliases:
  - byte
  - nibble
  - word
  - prefissi binari
---

# Byte, nibble, word e prefissi binari

## Terminologia dei raggruppamenti di bit
- **byte** = 8 bit
- **nibble** = 4 bit (mezzo byte)
- una cifra esadecimale memorizza un nibble; **due cifre hex = un byte intero**
- **word** = l'unità di dato su cui lavora il microprocessore. La dimensione dipende
  dall'architettura: processori a 64 bit operano su word di 64 bit, i più vecchi a 32 bit.

## Bit significativi
- **lsb** (*least significant bit*): il bit nella colonna di peso 1.
- **msb** (*most significant bit*): il bit all'estremo opposto (peso massimo).
- Dentro una word, allo stesso modo si parla di **LSB** e **MSB** riferiti ai *byte*
  (maiuscolo = byte, minuscolo = bit: attenzione alla convenzione del libro).

## Prefissi: la coincidenza dei 1024
Per pura coincidenza numerica:

$$2^{10} = 1024 \approx 10^3 \qquad 2^{20} \approx 10^6 \qquad 2^{30} \approx 10^9$$

Quindi in ambito digitale:
- $2^{10}$ byte = 1024 byte = 1 **kilobyte** (KB)
- $2^{20}$ byte = 1 **megabyte** (MB)
- $2^{30}$ byte = 1 **gigabyte** (GB)

> [!warning] Non confondere le unità
> La **capacità di memoria** si misura di solito in **byte**.
> La **velocità di comunicazione** si misura di solito in **bit/s**.
> Un modem a 56 kilobit/s trasferisce circa 7 KB/s.

## Da ricordare
- 4 bit = nibble = 1 cifra hex; 8 bit = byte = 2 cifre hex.
- $2^{10} = 1024$, e da qui tutti i prefissi binari.
- kilo/mega/giga in contesto binario sono potenze di 2, non di 10.

## Domande flash
1. Quante cifre esadecimali servono per scrivere una word a 32 bit?
2. Quanti byte sono $2^{16}$ byte, espressi in KB?
