---
layout: page
title: Zuverlässigkeit
permalink: /software-qualitaet/zuverlaessigkeit
---
Grad, in dem ein System, Produkt oder eine Komponente bestimmte Funktionen unter bestimmten Bedingungen für einen bestimmten Zeitraum ausführt.

[Reifegrad]({% link software-qualitaet/zuverlaessigkeit/reifegrad.md %})
Grad, in dem ein System, ein Produkt oder eine Komponente die Anforderungen an die Zuverlässigkeit im normalen Betrieb erfüllt.

[Verfügbarkeit]({% link software-qualitaet/zuverlaessigkeit/verfuegbarkeit.md %})
Grad, in dem ein System, ein Produkt oder eine Komponente betriebsbereit ist und bei Bedarf zur Verwendung verfügbar ist.

[Fehlertoleranz]({% link software-qualitaet/zuverlaessigkeit/fehlertoleranz.md %})
Grad, in dem ein System, Produkt oder eine Komponente trotz Hardware- oder Softwarefehlern bestimmungsgemäß funktioniert.

[Wiederherstellbarkeit]({% link software-qualitaet/zuverlaessigkeit/wiederherstellbarkeit.md %})
Grad, in dem ein Produkt oder System im Falle einer Unterbrechung oder eines Ausfalls die direkt betroffenen Daten wiederherstellen und den gewünschten Zustand des Systems wiederherstellen kann.

## Taktiken

* Fehlererkennung
  * Ping / Echo
  * Monitor
  * Heartbeat
  * Timestamp
  * Sanity Checking
  * Condition Monitoring
  * Voting
  * Exception Detection
  * Self-Test
* Wiederherstellung nach Fehlern
  * Vorbereitung und Reparatur
    * Aktive Redundanz (Hot Swap)
    * Passive Redundanz (Warm Standby)
    * Cold Stand By
    * Exception Handling
    * Rollback
    * Backup / Restore
    * Software Upgrade
    * Retry
    * Fehlerhaftes Verhalten ignorieren
    * Abbau
    * Rekonfiguration
  * Wiedereinführung
    * Schattenkopie 
    * State Resynchronisierung
    * Eskalation Restart
    * Non-Stop Forwarding
* Fehlervermeidung
  * Service entfernen
  * Transaktionen
  * Vorhersagbares Model
  * Vorbeugung von Ausnahmen
  * Handlungsspielraum erhöhen