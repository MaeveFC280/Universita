---
Materia: Programmazione Object-Oriented
tags:
  - Java
  - grafica
Link risorse: https://www.geeksforgeeks.org/java/introduction-to-java-swing/
Libro:
Imparato: true
Ordine: 16
aliases:
  - GUI
  - Swing
  - Interfacce grafiche
---
Utilizzando `javax.swing` è possibile creare interfacce in JDK
## Container e Panel
Un **Top-Level Container** è il contenitore principale, cioè una finestra “esterna” che può stare direttamente sullo schermo. I principali sono:
- **`JFrame`** (principale)
- `JDialog`
- `JApplet` (deprecato)

*Esempio:*
````java
JFrame frame = new JFrame("La mia finestra");
````
![[Pasted image 20260617170313.png]]
Dentro il Top-Level-Container vi è il **pannello** (`JPanel`): serve a organizzare gli elementi grafici.
*Esempio:*
````java
JFrame frame = new JFrame("Prima GUI");
JPanel panel = new JPanel();
frame.setContentPane(panel);
````
## Schermo
Lo schermo è come un piano cartesiano. L'angolo in alto a sinistra ha coordinate (0,0).
L’asse `x` cresce verso destra., l’asse `y` cresce verso il basso.
![[Screenshot 2026-06-17 alle 17.09.04.png]]

## Componenti grafici
Gli elementi grafici sono oggetti come:
- `JButton`
- `JLabel`
- `JTextField`
- `JTextArea`-
- `JCheckBox`
- `JRadioButton`

Per aggiungerci gli elementi grafici uso `add`
*Esempio:*
````java
JFrame frame = new JFrame("Esempio");
JPanel panel = new JPanel();

JButton bottone = new JButton("Premi");
JLabel label = new JLabel("Nome:");

panel.add(label);
panel.add(bottone);

frame.setContentPane(panel);
frame.setSize(400, 300);
frame.setVisible(true);
````
In un `panel` si può aggiungere di tutto, anche altri `panel`. Un elemento grafico può essere aggiunto ad UN SOLO `panel`.
## Gerarchia di contenimento
Una GUI è organizzata come un **albero** che rappresenta la disposizione concettuale degli elementi ed ha come radice il Top-Level-Container
`JFrame`
 └── `JPanel`
      ├── `JLabel`
      ├── `JTextField`
      └── `JButton`
 
## Layout manager
Un **Layout Manager** decide in modo dinamico come disporre gli elementi grafici dentro un pannello.
## Gestione degli eventi
La gestione delle azioni dell'utente avviene tramite i **gestori di eventi**. Quando viene avviato un programma, la [[Genesi del linguaggio|java virtual machine]]  avvia un loop infinto per mantenere l'interfaccia reattiva. Il programmatore definisce degli elementi (*es. bottoni, slider...*) sensibili agli eventi aggiungendo un **listener** (ce ne sono di più tipi):
````java
nomeComponente.addTIPOListener(instanceOfMyClass) {
    //code that reacts to the action...;
};
````
Quando l'evento associato si verifica la JVM attiva in automatico il metodo specifico (*es. `actionPerformed()`*) associato al controllo.
Quindi la GUI usa la **programmazione basata su eventi**, detta anche **event-driven programming**.
````java 
import javax.swing.*;

public class PrimaGUI {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Esempio Swing");
        JPanel panel = new JPanel();

        JButton bottone = new JButton("Cliccami");
        JLabel label = new JLabel("Non hai ancora cliccato");

        bottone.addActionListener(e -> {
            label.setText("Hai cliccato il bottone!");
        });

        panel.add(label);
        panel.add(bottone);

        frame.setContentPane(panel);
        frame.setSize(400, 300);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}
````
