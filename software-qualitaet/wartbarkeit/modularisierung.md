---
layout: page
title: Modularisierung
permalink: /software-qualitaet/wartbarkeit/modularisierung
---

Grad, in dem ein System oder Computerprogramm aus diskreten Komponenten besteht, sodass eine Änderung an einer Komponente nur minimale Auswirkungen auf andere Komponenten hat.

## Ideen für Taktiken

* Überprüfung
  * Automatisierte Überprüfung von Abhängigkeiten und architektonischen Aspekten
  * Vertikaler und Horizontaler Schnitt
* Abstrakte Betriebsumgebung
  * Containerisierung
  * Virtuelle Umgebungen
* Entkopplung der Module
  * Event-Basierte Architekturen
  * Service-Orientierung
  * Microservices
  * Serverless

## Wechselwirkungen zu anderen NFAs

### Analysierbarkeit

Beispiel:
Ein hoher Grad an Modularisierung führt meist auch zu einer schlechteren Analysierbarkeit auf Grund der höheren Komplexität.