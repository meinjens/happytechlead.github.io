---
layout: page
title: Wartbarkeit
permalink: /software-qualitaet/wartbarkeit
---

Dieses Merkmal gibt den Grad an Effektivität und Effizienz an, mit dem ein Produkt oder System modifiziert werden kann, um es zu verbessern, zu korrigieren oder an Änderungen in der Umgebung und in den Anforderungen anzupassen.

[Modularisierung]({% link software-qualitaet/wartbarkeit/modularisierung.md %})
Grad, in dem ein System oder Computerprogramm aus diskreten Komponenten besteht, sodass eine Änderung an einer Komponente nur minimale Auswirkungen auf andere Komponenten hat.

[Wiederverwendbarkeit]({% link software-qualitaet/wartbarkeit/wiederverwendbarkeit.md %})
Grad, in dem ein Asset in mehr als einem System oder beim Erstellen anderer Assets verwendet werden kann.

[Analysierbarkeit]({% link software-qualitaet/wartbarkeit/analysierbarkeit.md %})
Grad der Wirksamkeit und Effizienz, mit dem es möglich ist, die Auswirkungen einer beabsichtigten Änderung eines oder mehrerer seiner Teile auf ein Produkt oder ein System zu bewerten oder ein Produkt auf Mängel oder Fehlerursachen zu diagnostizieren oder zu ändernde Teile zu identifizieren.

[Modifizierbarkeit]({% link software-qualitaet/wartbarkeit/modifizierbarkeit.md %})
Grad, in dem ein Produkt oder System effektiv und effizient modifiziert werden kann, ohne dass Mängel auftreten oder die vorhandene Produktqualität beeinträchtigt wird.

[Testability]({% link software-qualitaet/wartbarkeit/testbarkeit.md %})
Effektivitäts- und Effizienzgrad, mit dem Testkriterien für ein System, ein Produkt oder eine Komponente festgelegt und Tests durchgeführt werden können, um festzustellen, ob diese Kriterien erfüllt wurden.

## Taktiken

* Größe von Modulen reduzieren
  * Modul teilen
  * Verantwortlichkeiten aufteilen
* Kohäsion erhöhen
  * Inneren semantischen Zusammenhang erhöhen
* Kopplung reduzieren
  * Kapselung
  * Vermittler verwenden
  * Abhängigkeiten begrenzen
  * Refactoring
  * Allgemeine Services abstrahieren
* Bindung verschieben