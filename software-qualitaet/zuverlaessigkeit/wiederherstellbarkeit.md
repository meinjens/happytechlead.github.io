---
layout: page
title: Wiederherstellbarkeit
permalink: /software-qualitaet/zuverlaessigkeit/wiederherstellbarkeit
---

Grad, in dem ein Produkt oder System im Falle einer Unterbrechung oder eines Ausfalls die direkt betroffenen Daten wiederherstellen und den gewünschten Zustand des Systems wiederherstellen kann.

## Taktiken

* Regelmäßiges Training der Wiederherstellbarkeit, um die Vollständigkeit der Wiederherstellung zu prüfen.
* Automatisierung der Wiederherstellung
* Backup
* Blue / Green
* Standby
* Resilliente Architekturen
* Exception Handling
* Circuit Breaker

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

## Weitere Merkmale

* Selbstheilbarkeit
* Resillience