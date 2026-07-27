---
Materia: Programmazione Object-Oriented
tags:
  - progettazione_concettuale
  - grafica
Link risorse:
Libro:
Imparato: true
Ordine: 18
aliases:
---
## Low-Fidelity Mock-Up

Disegni semplificati delle interfacce grafiche per comprendere l'interazione tra utente ed interfaccia.
![[Screenshot 2026-06-17 alle 17.55.50.png]]
Non serve a fare una grafica bella. Serve a capire:
- quali schermate servono;
- quali informazioni l’utente deve inserire;
- quali informazioni l’utente deve vedere;
- quali pulsanti o azioni sono disponibili;
- quale flusso c’è tra una schermata e l’altra.
![[Screenshot 2026-06-17 alle 17.56.49.png]]![[Screenshot 2026-06-17 alle 17.57.05.png]]
## Mapping
Dopo aver disegnato le schermate, bisogna fare il **mapping**, cioè collegare ogni elemento del mock-up alle classi del programma.

| Mock-up            | Codice                                                      |
| ------------------ | ----------------------------------------------------------- |
| Schermata          | [[User Interface\|JFrame, JPanel]], [[DAO\|Class Boundary]] |
| Scritta            | [[User Interface\|JLabel]                                   |
| Campo Testo        | [[User Interface\|JTextField]]                              |
| Bottone            | [[User Interface\|JButton]]                                 |
| Lista              | `JList`,`JTable`                                            |
| Menù a tendina     | `JComboBox`                                                 |
| Azione dell'utente | Metodo del [[Modello Entity-Boundary-Controll\|controller]]                      |

