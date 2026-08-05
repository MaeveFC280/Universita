---
tags: [architettura, arm, assembly, funzioni, cap6]
capitolo: 6
sezione: "6.3.7"
pagine_pdf: 336-345
---

# Lo stack

## Definizione
Lo **stack** è una porzione di memoria usata per **salvare informazioni all'interno di
una funzione**. È una coda **LIFO** (*last-in-first-out*): come una pila di piatti,
l'ultimo elemento inserito è il primo a essere prelevato.

## Direzione di crescita
> [!important] Lo stack ARM cresce verso il basso
> Lo **stack pointer (SP, R13)** parte da un indirizzo di memoria **alto** e
> **decrementa** per espandere lo stack quando serve più spazio.
>
> - **allocare** spazio: `SUB SP, SP, #n`
> - **deallocare** spazio: `ADD SP, SP, #n`

SP punta sempre alla cima dello stack, cioè al dato più recentemente inserito.

## L'uso principale: salvare i registri
> Uno degli usi importanti dello stack è **salvare e ripristinare i registri** che la
> funzione modifica.

Una funzione **salva i registri sullo stack prima di modificarli**, e li **ripristina
dallo stack prima di terminare**.

## I cinque passi canonici
Una funzione che deve usare registri preservati:

1. **Fa spazio** sullo stack per memorizzare i valori di uno o più registri.
2. **Memorizza** i valori dei registri sullo stack.
3. **Esegue** la funzione usando quei registri.
4. **Ripristina** i valori originali dei registri dallo stack.
5. **Dealloca** lo spazio sullo stack.

```
funzione
        SUB  SP, SP, #12       ; 1. fa spazio per 3 word
        STR  R4, [SP, #8]      ; 2. salva R4
        STR  R5, [SP, #4]      ;    salva R5
        STR  LR, [SP]          ;    salva LR (chiamate annidate)

        ...corpo della funzione, usa liberamente R4, R5, chiama altre funzioni...

        LDR  R4, [SP, #8]      ; 4. ripristina
        LDR  R5, [SP, #4]
        LDR  LR, [SP]
        ADD  SP, SP, #12       ; 5. dealloca
        MOV  PC, LR
```

## Stack frame
Lo spazio che una funzione allocca per sé sullo stack si chiama **stack frame**
(*record di attivazione*). Contiene tipicamente:
- i registri preservati salvati (compreso LR);
- le variabili locali che non entrano nei registri;
- gli argomenti oltre il quarto, per le funzioni che chiama.

Ogni chiamata annidata crea un nuovo frame; al ritorno il frame viene distrutto. È così
che funziona la **ricorsione**: ogni invocazione ha il proprio spazio privato.

## Istruzioni multiple: LDM e STM
> Salvare e ripristinare registri sullo stack è un'operazione **così comune** che ARM
> fornisce istruzioni dedicate per **caricare e memorizzare più registri** in un colpo
> solo.

| Istruzione | Nome |
|---|---|
| `STM` | *store multiple* |
| `LDM` | *load multiple* |

`LDM` e `STM` esistono in **quattro varianti**, per stack **discendenti e ascendenti**,
**pieni e vuoti** (*full/empty*, *descending/ascending*): `FD`, `ED`, `FA`, `EA`.
La combinazione standard per lo stack ARM è **FD** (*full descending*).

### PUSH e POP
Gli alias più leggibili delle varianti FD:
```
PUSH {R4, R5, LR}      ; equivale a STMFD SP!, {R4,R5,LR}
...
POP  {R4, R5, LR}      ; equivale a LDMFD SP!, {R4,R5,LR}
```
oppure, per tornare direttamente:
```
POP  {R4, R5, PC}      ; ripristina e salta all'indirizzo di ritorno
```

> [!tip] La forma idiomatica di una funzione ARM
> ```
> funzione
>         PUSH {R4-R6, LR}     ; prologo
>         ...corpo...
>         POP  {R4-R6, PC}     ; epilogo + ritorno in una istruzione
> ```
> Da preferire alle SUB/STR manuali: più compatta, più veloce, meno errori.

## Nota sull'ordine
In `PUSH`/`POP` i registri sono elencati tra graffe e vengono salvati **in ordine di
numero di registro**, indipendentemente dall'ordine in cui li scrivi. Il registro con
numero più basso finisce all'indirizzo più basso.

## Da ricordare
- Lo stack **cresce verso il basso**: `SUB SP` alloca, `ADD SP` dealloca.
- I 5 passi: fa spazio → salva → esegue → ripristina → dealloca.
- **Salvare LR** è obbligatorio se la funzione chiama altre funzioni.
- `PUSH {..., LR}` / `POP {..., PC}` è la forma idiomatica.

## Domande flash
1. Perché SP decrementa invece di incrementare?
2. Cosa succede se una funzione annidata non salva LR?
3. Cosa contiene uno stack frame?
