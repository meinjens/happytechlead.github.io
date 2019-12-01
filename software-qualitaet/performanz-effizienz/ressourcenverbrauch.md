---
layout: page
title: Ressourcenverbrauch
permalink: /software-qualitaet/performanz-effizienz/ressourcenverbrauch
---

Grad, in dem die Mengen und Arten von Ressourcen, die von einem Produkt oder System zur Erfüllung seiner Funktionen verwendet werden, den Anforderungen entsprechen.

## Taktiken (beta)

* Monitoring
  * Analyse mit Hilfe von Profiling (CPU-Zeit)
  * Application Performance Monitoring
* Steuerung des Ressourcenverbrauchs
  * Auto-Scaling von Ressourcen
  * Verändern der Anfragerate
  * Limitieren der Event Anwort
  * Events priorisieren
  * Überflüssiges entfernen
  * Ausführungszeiten begrenzen

## Wechselwirkungen mit anderen NFAs

### Wartbarkeit

Beispiel:
Ein System wurde aus Performancegründen auf mehrere Knoten verteilt und stellt dadurch höhere Anforderungen an die Analysierbarkeit (z.B. Loganalyse).

### Portierbarkeit

Beispiel:
Um einen Anwendung ausfallsicher zu gestalten, soll sie bei unterschiedlichen Cloud-Anbietern installiert werden.

### Kapazität

Beispiel:
Ist der Ressourcenbedarf einer Anwendung nicht erfüllt, so kann die Anwendung die angeforderte Arbeitslast ggf. nicht mehr erfüllen.