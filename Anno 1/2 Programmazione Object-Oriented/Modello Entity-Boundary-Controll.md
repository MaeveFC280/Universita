---
Materia: Programmazione Object-Oriented
tags:
  - grafica
  - Java
Link risorse:
Libro:
Imparato: true
Ordine: 17
aliases:
  - GUI
  - EBC
  - Entity-Bound-Controll
---
Una `package` è un contenitore di classi, ovvero una cartella interna a `srs`

`src`
 ├── `entities`
 ├── `gui`
 ├── `controllers`
 ├── `exceptions`
 └── `persistence`
 
 I nomi vanno scritti in minuscolo
 *Esempio:*
````java
 package entities;

public class Studente {
    ...
}
````
## Navigazione tra GUI
 ![[Screenshot 2026-06-17 alle 17.33.24.png]]
 Come navigare tra le finestre?
 - Collego tutte le finestre tra di loro:
![[Screenshot 2026-06-17 alle 17.37.12.png]]
Problemi:
1. Il codice diventa disordinato.
2. Non funziona con librerie diverse

- Creo una classe o più di **controllo**
## Controller
Il controller gestisce la navigazione.
Quindi non è la GUI a decidere direttamente quale finestra aprire, ma lo chiede al controller.
![[Screenshot 2026-06-17 alle 17.39.32.png]]
## Euristica ECB
Le classi del codice sono divise in tre parti:
1. **Classi Entity**: Rappresentano gli elementi del mondo reale.
*Es: Classe ContoCorrente, con metodi che garantiscano che il saldo non sia mai negati*
2. **Classi Boundary:** Classi di interfaccia grafica, che visualizzano dati e recepiscono dati.
3. **Classi Controller**: Classi che includono la logica di navigazione e di business.
#### Regole
1. Le classi boundary non si conoscono tra di loro (una finestra non dovrebbe aprirne un'altra).
2. I controller comunicano con boundary ed entity
3. Le entity non devono conoscere le boundary
![[Screenshot 2026-06-17 alle 18.05.00.png]]