---
Materia: Architettura degli elaboratori
tags:
  - Binario
  - aritmetica
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 1.4.6'
Imparato: true
Ordine: 106
aliases:
  - complemento a due
  - two's complement
  - segno-modulo
  - numeri negativi
---
## Segno/modulo (sign/magnitude)
Un numero a $N$ bit usa:
- il **msb come segno** (0 = positivo, 1 = negativo)
- gli altri $N-1$ bit come **modulo** (valore assoluto)

Range: $[-2^{N-1}+1,\ 2^{N-1}-1]$

### Difetti
1. **L'addizione binaria ordinaria non funziona.** Es. $-5 + 5$ in segno/modulo a 4 bit: $1101 + 0101 = 10010$, che è un risultato privo di senso.
2. **Esistono due zeri**: $+0$ ($0000$) e $-0$ ($1000$).

## Complemento a due (two's complement)
Identico al binario senza segno, **tranne il peso del msb, che vale $-2^{N-1}$** anziché $+2^{N-1}$.

Su 4 bit: pesi $-8, +4, +2, +1$. $1101_2 = -8 + 4 + 1 = -3$

Range: $[-2^{N-1},\ 2^{N-1}-1]$ — un solo zero, e un negativo in più dei positivi.

### Come si nega un numero (regola operativa)
> **Inverti tutti i bit e aggiungi 1.**

*Esempio: negare $3 = 0011$ → inverti: $1100$ → +1: $1101 = -3$.*

### Casi particolari
- $0$: negare $0000$ dà $10000$ → troncato a 4 bit torna $0000$.
- $-2^{N-1}$ ($1000$ su 4 bit): negarlo dà $1000$, cioè se stesso. Il suo opposto **non è rappresentabile** in $N$ bit.

## Overflow in complemento a due
Si verifica quando si sommano due numeri **dello stesso segno** e il risultato ha il **segno opposto**. Sommare numeri di segno diverso non può mai andare in overflow.

## Estensione a più bit
- **Sign extension**: per estendere un numero con segno, si replica il msb nelle posizioni nuove ($-3 = 1101 \to 11111101$). Il valore non cambia.
- **Zero extension**: per numeri senza segno si riempie con zeri.
