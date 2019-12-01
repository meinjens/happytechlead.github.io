---
layout: page
title: Koexistenz
permalink: /software-qualitaet/kompatibilitaet/koexistenz
---

Grad, in dem ein Produkt seine erforderlichen Funktionen effizient ausführen kann, während es eine gemeinsame Umgebung und Ressourcen mit anderen Produkten teilt, ohne dass sich dies nachteilig auf andere Produkte auswirkt.

## Taktiken

* Gleiche Betriebsumgebung
  * Trennung durch Kontext / Namensräume
* Getrennte Betriebsumgebung
  * Trennung durch Konfiguration
* Kontextbasierte Ausführung / Mandantenfähigkeit
  * Organisatorische Trennung
  * Trennung der Daten
  * Entkopplung von Verhalten
* Trennung durch Konfiguration
  * Trennung der Betriebsumgebung

## Wechselwirkungen mit anderen NFAs

* Keine Datenintegrität -> Sicherheitsverletzungen bei in verschiedenen Mandanten
* Hohe Koexistenz -> Hohe Anforderungen an die Sicherheit
* Wartbarkeit meist erhöht, wenn die koexistenz niedrig ist
