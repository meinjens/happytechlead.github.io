---
layout: page
title: Analysierbarkeit
permalink: /software-qualitaet/wartbarkeit/analysierbarkeit
---

Grad der Wirksamkeit und Effizienz, mit dem es möglich ist, die Auswirkungen einer beabsichtigten Änderung eines oder mehrerer seiner Teile auf ein Produkt oder ein System zu bewerten oder ein Produkt auf Mängel oder Fehlerursachen zu diagnostizieren oder zu ändernde Teile zu identifizieren.

## Weitere Merkmale

* Monitorbarkeit
* Debugbarkeit
* Nachverfolgbarkeit

## Ideen für Taktiken

* Implementierung
  * Clean Code
  * Aussagekräftige Fehlermeldungen / Codes
  * Pair Programming
  * Mob Programming
  * Coding Conventions
* Continous Inspection
  * Code Reviews
  * Automatisierte Codeanalyse
* Unterstützung der Analyse durch Werkzeuge
  * Monitoring
  * Tracing
  * Logging
  * Debugging

## Wechselwirkungen zu anderen NFAs

### Performance & Effizienz

Beispiel:
Ein hoher Grad an Anforderungen zu Analysierbarkeit kann dazu führen, dass viele zusätzliche Systeme, wie Tracing, Monitoring, Logging etc. eingesetzt werden, die Einfluss auf die Performance haben können.
