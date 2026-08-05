---
Materia: Architettura degli elaboratori
tags:
  - ARM
  - assembly
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 6.3.5-6.3.6'
Imparato: false
Ordine: 611
aliases:
  - ASCII
  - LDRB
  - stringhe
---

# Byte, caratteri ASCII e stringhe

## Perché i byte
I numeri nell'intervallo $[-128, 127]$ si possono memorizzare in un **singolo byte**
anziché in un'intera word: si risparmia memoria (4× per gli array grandi).

Inoltre, **i caratteri inglesi sono comunemente rappresentati da byte**.

## ASCII
L'**ASCII** (*American Standard Code for Information Interchange*) assegna a ogni
carattere un valore numerico univoco. I valori ASCII sono in genere dati in
**esadecimale**.

| Carattere | ASCII (hex) | ASCII (dec) |
|---|---|---|
| `0` | 0x30 | 48 |
| `9` | 0x39 | 57 |
| `A` | 0x41 | 65 |
| `Z` | 0x5A | 90 |
| `a` | 0x61 | 97 |
| `z` | 0x7A | 122 |
| spazio | 0x20 | 32 |
| newline (LF) | 0x0A | 10 |
| NUL | 0x00 | 0 |

> [!important] La proprietà da sapere
> **Le lettere minuscole e maiuscole differiscono di 0x20** ($32_{10}$).
> Quindi:
> - da maiuscolo a minuscolo: `ADD Rd, Rn, #0x20` (o `ORR Rd, Rn, #0x20`)
> - da minuscolo a maiuscolo: `SUB Rd, Rn, #0x20` (o `BIC Rd, Rn, #0x20`)
>
> Analogamente, la cifra numerica si ottiene dal carattere con `SUB Rd, Rn, #0x30`.

## Istruzioni per byte e half-word
| Istruzione | Effetto |
|---|---|
| `LDRB Rd, [Rn,#off]` | carica il byte all'indirizzo e riempie i bit restanti del registro con **zeri** |
| `LDRSB` | carica il byte e riempie con il **bit di segno** (estensione con segno) |
| `STRB Rs, [Rn,#off]` | scrive in memoria il **byte meno significativo** di `Rs` |
| `LDRH` / `LDRSH` / `STRH` | analoghe per le **half-word** (16 bit) |

> [!warning] La scelta tra LDRB e LDRSB
> Per i **caratteri** (valori 0–127 non negativi) va bene `LDRB`.
> Per i **numeri con segno** memorizzati in un byte serve `LDRSB`, altrimenti $-1$
> (`0xFF`) verrebbe letto come $255$.

## Stringhe
Una serie di caratteri si chiama **stringa**. Le stringhe hanno **lunghezza variabile**,
quindi un linguaggio di programmazione deve fornire un modo di determinarne la lunghezza
o la fine.

In **C** si usa la convenzione della **stringa terminata da NUL**: l'ultimo byte è
`0x00`, e la lunghezza si ricava scorrendo la stringa fino a trovarlo.

Esempio: la stringa `"Hi!"` occupa 4 byte:
```
'H' = 0x48, 'i' = 0x69, '!' = 0x21, NUL = 0x00
```

### Esempio: calcolare la lunghezza di una stringa
```
        ; R0 = indirizzo della stringa, R1 = lunghezza
        MOV  R1, #0
loop
        LDRB R2, [R0], #1       ; leggi il byte e avanza
        CMP  R2, #0             ; è il terminatore?
        BEQ  done
        ADD  R1, R1, #1
        B    loop
done
```

### Esempio: convertire una stringa in maiuscolo
```
        ; R0 = indirizzo stringa
loop
        LDRB R1, [R0]
        CMP  R1, #0
        BEQ  done
        CMP  R1, #'a'
        BLO  next               ; se < 'a' non è minuscola
        CMP  R1, #'z'
        BHI  next               ; se > 'z' non è minuscola
        SUB  R1, R1, #0x20      ; convertila
        STRB R1, [R0]
next
        ADD  R0, R0, #1
        B    loop
done
```

## Endianness (cenno)
Quando si accede a byte singoli dentro una word, conta l'ordinamento:
- **little-endian**: il byte meno significativo sta all'indirizzo più basso;
- **big-endian**: il byte più significativo sta all'indirizzo più basso.

ARM può funzionare in entrambi i modi, ma nella pratica si usa quasi sempre
**little-endian**.

## Da ricordare
- Maiuscole e minuscole differiscono di **0x20**; le cifre partono da **0x30**.
- `LDRB` estende con **zeri**, `LDRSB` con il **segno**.
- Stringhe C: **terminate da NUL** (`0x00`).

## Domande flash
1. Qual è il valore ASCII di `'5'`? E come si ottiene il numero 5 da quel carattere?
2. Perché `LDRSB` esiste, se i caratteri ASCII sono tutti positivi?
