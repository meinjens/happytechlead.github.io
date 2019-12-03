---
layout: page
title: Performanz & Effizienz
permalink: /software-qualitaet/performanz-effizienz/zeitverhalten
---

Grad, in dem die Reaktions- und Verarbeitungszeiten sowie die Durchsatzraten eines Produkts oder Systems bei der Erfüllung seiner Funktionen den Anforderungen entsprechen.

## Ideen für Taktiken

* Messung
  * Automatisiertes Performance Testing für das gesamte System
  * Analyse mit Hilfe von Profiling (CPU-Zeit)
* Skalierung
  * Effizienz der Ressourcen erhöhen (Vertikale Skalierung)
  * Weitere Ressourcen einbinden (Horizontale Skalierung)
* Verteilung
  * Nebenläufigkeit einführen
  * Berechnung auf mehrere Knoten
  * Redundante Speicherung (Caching)


## Wechselwirkungen mit anderen NFAs

### Ressourcenverbrauch

Beispiel:
Eine Anwendung wurde auf mehrere Knoten verteilt, um seine Funktionen schneller ausführen zu können.


### Wartbarkeit

Beispiel:
Eine verteilte Anwendung stellt auf Grund des höheren Konfigurationsaufwands erhöhte Anforderungen an die Wartbarkeit.


### Portierbarkeit

Beispiel:
Eine Anwendung soll auf mehrere Knoten installiert werden,