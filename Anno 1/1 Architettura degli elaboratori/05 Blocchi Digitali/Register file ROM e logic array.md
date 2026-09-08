---
Materia: Architettura degli elaboratori
tags:
  - memoria
  - Logica
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 5.5.5-5.6'
Imparato: false
Ordine: 511
aliases:
  - register file
  - PLA
  - FPGA
  - logic array
---
## Register file
I sistemi digitali usano spesso un **gruppo di registri** per memorizzare variabili temporanee. Questo gruppo, detto **register file**, è tipicamente realizzato come una **piccola SRAM multiporta**, perché è più compatta di un banco di flip-flop.

Struttura tipica (quella del processore ARM del capitolo 7):
- **due porte di lettura**, ciascuna con il proprio indirizzo (A1, A2) e la propria uscita dati (RD1, RD2);
- **una porta di scrittura**, con indirizzo (A3), dato (WD3) e abilitazione (WE3).

Così si possono leggere **due [[Operandi|operandi]]** e scriverne **uno** nello stesso ciclo — che è esattamente ciò che serve a un'istruzione come `ADD R0, R1, R2`.

## Le memorie come logica combinatoria
> [!important] Idea potente
> Un [[Array di memoria - organizzazione|array di memoria]] può **realizzare funzioni logiche combinatorie**. Se si collegano gli ingressi della funzione all'**indirizzo** della ROM e si programma ogni parola con il valore d'uscita desiderato, l'uscita della ROM **è** la [[Porte logiche|tabella di verità]] della funzione.

Una ROM $2^N \times M$ realizza $M$ funzioni arbitrarie di $N$ variabili.

Usata in questo modo, la memoria si chiama **[[Multiplexer|lookup table]]** (LUT): una tabella di consultazione. È la stessa idea del mux come LUT.

Limite: il costo cresce come $2^N$, quindi le LUT convengono solo per un numero piccolo di ingressi (tipicamente 4-6).

## Logic array
I **logic array** (array logici) sono chip che possono essere **configurati** per realizzare qualunque funzione, **senza** che l'utente debba progettare un chip su misura. Sono la risposta al costo altissimo dei circuiti dedicati.

### PLA (Programmable Logic Array)
Realizza logica **a due livelli** in forma **[[Forme canoniche SOP e POS|somma di prodotti]]**:
- un **AND array** che produce gli implicanti;
- un **OR array** che li somma.

Gli array sono programmabili: si decide quali ingressi entrano in ogni AND e quali AND entrano in ogni OR. Le PLA sono limitate alla logica combinatoria.

### FPGA (Field Programmable Gate Array)
Molto più generale e potente. Un'FPGA è un array di **elementi logici** (LE, o CLB) e di risorse di interconnessione programmabili, oltre a blocchi di I/O.

Ogni elemento logico contiene tipicamente:
- una o più **LUT** (tipicamente a 4-6 ingressi) per la logica combinatoria;
- uno o più **flip-flop** per la logica sequenziale;
- **multiplexer** di configurazione che instradano i segnali.

Le interconnessioni programmabili collegano gli elementi logici tra loro e ai piedini.

> [!tip] Come si progetta con un'FPGA
> Si descrive il circuito in un **HDL** (Verilog/VHDL); gli strumenti CAD eseguono
> **sintesi** (dalla descrizione alla rete di porte), **mapping** (dalle porte alle LUT),
> **place & route** (posizionamento e instradamento), e generano il file di configurazione da caricare nell'FPGA.

### Confronto
| | ASIC | FPGA | PLA |
|---|---|---|---|
| flessibilità | nessuna (fisso) | **massima** | solo combinatoria |
| costo non ricorrente (NRE) | altissimo | nullo | basso |
| costo unitario | **bassissimo** in volumi | alto | basso |
| prestazioni | **massime** | medie | medie |
| tempo di sviluppo | mesi | giorni | giorni |

## Da ricordare
- Register file = piccola SRAM multiporta, 2 letture + 1 scrittura.
- ROM/mux come **lookup table**: qualunque funzione di $N$ variabili.
- PLA = AND array + OR array, solo combinatoria.
- FPGA = LUT + flip-flop + interconnessioni programmabili.
