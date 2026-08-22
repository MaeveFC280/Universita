---
Materia: Architettura degli elaboratori
tags:
  - memoria
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 5.5.2-5.5.4'
Imparato: false
Ordine: 510
aliases:
  - DRAM
  - SRAM
  - ROM
  - memoria volatile
---
## La classificazione
Le memorie si classificano in base a **come la bit cell memorizza il bit**. La
distinzione più ampia:

| | RAM | ROM |
|---|---|---|
| nome | *random access memory* | *read only memory* |
| storicamente | volatile, leggibile e scrivibile | non volatile, solo lettura |

> [!warning] I nomi sono storici e ingannevoli
> - **RAM** si chiama così perché si accede a qualunque parola con lo **stesso ritardo**,
>   indipendentemente dall'indirizzo (a differenza dei nastri o dei dischi). Ma **anche
>   le ROM sono ad accesso casuale**.
> - **ROM** significherebbe "sola lettura", ma **la maggior parte delle ROM moderne si
>   può scrivere** (flash, EEPROM), anche se molto più lentamente della lettura.
>
> La distinzione utile oggi è: **RAM volatile** (perde i dati senza alimentazione)
> vs **ROM non volatile** (li conserva).

## DRAM (Dynamic RAM)
La **DRAM** memorizza un bit come **presenza o assenza di carica su un condensatore**.

- condensatore carico a $V_{DD}$ → bit = **1**
- condensatore scaricato a GND → bit = **0**

Struttura: **1 transistor + 1 condensatore** per bit cell. È questo il motivo della sua
densità altissima e del basso costo per bit.

### I due problemi della DRAM
1. **La lettura è distruttiva**: leggere la cella condivide la carica del condensatore
   con la bitline, alterandone il valore. Il dato va quindi **riscritto** dopo ogni
   lettura.
2. **La carica si disperde** (correnti di perdita): il valore va **riscritto
   periodicamente** anche senza accessi. Questo si chiama **refresh** (tipicamente ogni
   pochi millisecondi) — ed è da qui che viene l'aggettivo "**dinamica**".

## SRAM (Static RAM)
La **SRAM** memorizza un bit con una coppia di **inverter incrociati**
(→ [[Elementi bistabili]]): l'elemento bistabile mantiene il valore attivamente.

Si chiama **statica** perché i bit memorizzati **non hanno bisogno di refresh**.

Struttura: **6 transistor** per bit cell (2 inverter da 2 transistor + 2 transistor di
accesso).

## Confronto DRAM / SRAM
| | DRAM | SRAM |
|---|---|---|
| bit cell | 1 transistor + 1 condensatore | 6 transistor (2 inverter incrociati) |
| densità | **alta** | bassa |
| costo per bit | **basso** | alto |
| velocità | lenta | **veloce** |
| refresh | **necessario** | non necessario |
| lettura distruttiva | **sì** | no |
| uso tipico | memoria principale | cache, register file |

→ [[Gerarchia di memoria e principi di localita]]

## ROM
La **ROM** memorizza un bit come **presenza o assenza di un transistor**.

Lettura:
1. la bitline è tirata **debolmente a HIGH**;
2. si attiva la wordline;
3. **se il transistor è presente**, connette la bitline a massa e la tira a **0**;
   **se è assente**, la bitline resta a **1**.

Non c'è nulla da alimentare per mantenere il dato: è **non volatile** per costruzione.

### Varianti
- **Mask ROM**: programmata in fabbrica; economica solo in grandi volumi.
- **PROM** (*programmable*): programmabile una volta sola.
- **EPROM / EEPROM**: cancellabile (con UV / elettricamente) e riprogrammabile.
- **Flash**: la ROM riprogrammabile dominante oggi (SSD, chiavette, firmware).
  Lettura veloce, scrittura lenta e a blocchi, numero limitato di cicli di scrittura.

