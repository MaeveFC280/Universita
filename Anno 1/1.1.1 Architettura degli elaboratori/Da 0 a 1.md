---
Materia: Architettura degli elaboratori
tags:
Link risorse:
Libro: '"Digital Design and Computer Architecture" Capitolo 1'
Imparato: true
Ordine: 1
aliases:
  - Astrazione
---
Tramite l'*astrazione* è possibile suddividere in parti un sistema complesso. Un computer (o un altro sistema elettronico) per esempio è suddividibile nelle seguenti parti
1. **Fisica**: Elettroni
2. **Dispositivi**: Trasmettitori diode
3. **Circuiti analogici**: Filtri amplificatori
4. **Circuiti digitali**: AND e NOT
5. **Logica**: Adders memories
6. **Micro-architettura**: Data-path controllers
7. **Architettura**: Registri d'istruzioni
8. **Sistema operativo**: Device drivers
9. **Software**: Programmi
# Valori discreti
Le variabili fisiche sono continue, mentre quando vengono digitalizzate bisogna scegliere degli intervalli e un numero finito di valori. I computer usano un [[Sistemi di numerazione|sistema binario]] (2 valori) tramite un alto voltaggio "1" e basso voltaggio "0". L'informazione D con N possibili stati è misurabile in bit che sono: $D=\log_{2}N\text{ bits}$ . Quindi una variabile binaria trasmette $\log_{22}=1$ bit di informazione. Tale sistema è affiancabile alla [[Logic gates|logica booleana]] dove "1"=TRUE e "0"=FALSE.
