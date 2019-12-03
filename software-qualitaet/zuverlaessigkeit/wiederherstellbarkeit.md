---
layout: page
title: Wiederherstellbarkeit
permalink: /software-qualitaet/zuverlaessigkeit/wiederherstellbarkeit
---

Grad, in dem ein Produkt oder System im Falle einer Unterbrechung oder eines Ausfalls die direkt betroffenen Daten wiederherstellen und den gewünschten Zustand des Systems wiederherstellen kann.

## Weitere Merkmale

* Selbstheilbarkeit
* Resillience

## Ideen für Taktiken

* Regelmäßiges Training der Wiederherstellbarkeit, um die Vollständigkeit der Wiederherstellung zu prüfen.
* Automatisierung der Wiederherstellung
* Backup
* Blue / Green
* Standby
* Resilliente Architekturen
* Exception Handling
* Circuit Breaker

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

## Wechselwirkungen mit anderen NFAs

* Geringe Wiederherstellbarkeit -> Hohes Risiko des wirtschaftlichen Schadens

