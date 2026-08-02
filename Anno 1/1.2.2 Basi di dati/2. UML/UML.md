---
Materia: Basi di dati
tags:
  - progettazione_concettuale
  - UML
Link risorse: https://web.archive.org/web/20110322065222/http://liuct.altervista.org/download/repository/ingsof/Appunti_UML.pdf
Imparato: true
aliases:
Ordine: 1
---
## Entità
Concetto fondamentale del [[Definizioni|minimondo]]. Descrive in modo astratto una istanza.
## Associazione
Caratterizzate da:
- **Nome**
- **Ruolo**
- **Grado**:numero di entità che comprende
- **Molteplicità**: Rapporto di cardinalità
Una associazione può essere **ricorsiva**
## Attributi
In un UML il nome degli attributi è sempre accompagnato dal suo tipo (int, string...)
- Non è possibile indicare quando un attributo è composto
- Un attributo multi-valued è accompagnato da {0...n}, indicando il numero di possibilità
- Gli attributi calcolabili sono preceduti da `<<derive>>`
- Quando una entità non possiede un attributo distintivo è detta **entità debole**!

![[Screenshot 2026-06-10 alle 23.56.31.png]]

| NomeEntità        |
| ----------------- |
| attributo: String |
## Note importanti
- Non mettere MAI degli ID  a questo punto, ci troviamo nella **CONCETTUALE** quindi deve essere in linguaggio naturale e non tecnico