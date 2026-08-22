---
Materia: Architettura degli elaboratori
tags:
  - logica_sequenziale
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 3.2.6-3.2.7'
Imparato: false
Ordine: 305
aliases:
  - enable
  - reset sincrono
  - reset asincrono
---
## Flip-flop con enable
Aggiunge un ingresso **EN** (o **ENABLE**) che determina se il dato deve essere
caricato sul fronte di clock.

- $EN = 1$ → si comporta da normale flip-flop D: $Q$ prende il valore di $D$ sul fronte.
- $EN = 0$ → **ignora** il clock e **mantiene** il valore precedente.

### Due realizzazioni
1. **Con un mux 2:1** davanti al flip-flop: se $EN=1$ seleziona $D$, se $EN=0$
   riseleziona l'uscita $Q$. **È la soluzione preferita.**
2. **Con un AND sul clock** (*clock gating*): il clock arriva al flip-flop solo se
   $EN=1$. Funziona, ma è **rischiosa**: introduce ritardo sul clock e può generare
   glitch sul segnale di clock, violando la disciplina sincrona. Va usata solo con
   celle apposite fornite dalla libreria.

Uso tipico: caricare un registro solo in certi cicli (es. il *program counter* durante
uno stallo della pipeline).

## Flip-flop con reset
Aggiunge un ingresso **RESET**:
- $RESET = 0$ (non asserito) → si comporta da normale flip-flop D;
- $RESET = 1$ (asserito) → **ignora $D$** e azzera l'uscita: $Q = 0$.

Serve per portare il sistema in uno stato noto all'accensione o al comando di reset,
poiché il valore iniziale dei flip-flop è altrimenti imprevedibile.

### Sincrono vs asincrono
| Tipo | Quando fa reset | Realizzazione |
|---|---|---|
| **Sincronamente resettabile** | solo sul **fronte di salita** del clock | banale: un AND fra $D$ e $\overline{RESET}$ davanti al flip-flop |
| **Asincronamente resettabile** | **immediatamente**, indipendentemente dal clock | richiede la **modifica della struttura interna** del flip-flop |

Il reset asincrono è più potente (funziona anche se il clock non sta girando) ma più
delicato: il rilascio del reset deve essere sincronizzato per evitare metastabilità.

## Flip-flop con set
Usato più raramente. Carica un **1** nel flip-flop quando **SET** è asserito. Esiste
anch'esso nelle varianti sincrona e asincrona.

## Da ricordare
- Enable con **mux**, non con AND sul clock (evitare il clock gating artigianale).
- Reset **sincrono** = logica esterna semplice; **asincrono** = struttura interna
  modificata.
- Il reset esiste perché lo stato iniziale dei flip-flop è indeterminato.

## Domande flash
1. Perché mettere una porta AND sul clock è pericoloso?
2. Quale reset funziona anche con il clock fermo?
