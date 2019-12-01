---
layout: page
title: Koexistenz
permalink: /software-qualitaet/kompatibilitaet/koexistenz
---

Grad, in dem ein Produkt seine erforderlichen Funktionen effizient ausführen kann, während es eine gemeinsame Umgebung und Ressourcen mit anderen Produkten teilt, ohne dass sich dies nachteilig auf andere Produkte auswirkt.

## Taktiken (beta)

* Gleiche Betriebsumgebung
  * Trennung durch Kontext / Namensräume
  * Trennung durch Versionen
* Getrennte Betriebsumgebung
  * Trennung durch Konfiguration
* Kontextbasierte Ausführung / Mandantenfähigkeit
  * Organisatorische Trennung
  * Trennung der Daten
  * Entkopplung von Verhalten
* Trennung durch Konfiguration
  * Trennung der Betriebsumgebung

## Wechselwirkungen mit anderen NFAs

### Sicherheit

Beispiel:
Ein mandantenfähiges System stellt hohe Anforderungen an die Datenintegrität, da es in den meisten Fällen unbedingt vermieden werden muss, dass sich die Mandanten gegenseitig beeinflussen können bzw. die Daten des anderen Mandanten sehen dürfen.

### Wartbarkeit

Beispiel:
Ein mandantenfähiges System stellt erhöhte Anforderungen an die Wartbarkeit, da für die jeweiligen Mandaten meist unterschiedliche Konfigurationen und Verhalten verwendet werden.

