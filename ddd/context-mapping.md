---
layout: page
title: Context Mapping
permalink: /ddd/context-mapping
---

- Beziehungen zwischen Bounded Contexts aber auch Teams
- technische Mechanismen zwischen zwei Bounded Contexts

- Strich zwischen zwei Bounded Contexts symbolisiert die Übersetzung zwischen den Bounded Contexts


## Beziehungen zwischen Kontextgrenzen / Teams

### Partnership

- zwei Teams mit jeweils einem Bounded Context
- voneinander abhängige Ziele
- Hohes Niveau des gegenseitigen Engagements
- Kennzeichnung durch eine dicke Linie
- Sollte Zeitlich begrenzt werden, da es eine große Herausforderung ist, dies lange Zeit zu pflegen

### Shared Kernel

- teilen sich ein kleines aber gemeinsames Modell
- schwer einzuführen
- kann funktionieren wenn alles das wollen


### Customer-Supplier

- Supplier (Lieferant) ist vorgeschaltet (upstream)
- Customer (Kunde) ist nachgeschaltet (downstream)
- gemeinsame Planung
- am Ende bestimmt der Supplier den Lieferumfang


### Conformist

- Upstream-Team hat keine Motivation das Downstream-Team zu unterstützen
- das Downstream-Team muss sich dem Upstream-Team anpassen (konform gehen)

### Anticurruption Layer

- Übersetzung und Entkopplung von einem anderen Context
- Hohe Kosten bei der Erstellung

### Open Host Service

- Offene und wohl dokumentierte Schnittstelle
- leichte Integration

### Published Language

- wohldokumentierte Sprache
- Austausch von Informationen


### Separate Ways

- getrennte Wege gehen, da es keinen gemeinsamen Integrationsansatz gibt

### Big Ball of Mud

- ungewollte Beziehungen und aufgeblähte Modelle
- Änderungen führen zu ungewünschten Nebeneffekten


## Kommunikationswege

- RPC mit Soap
- REST
- Messaging (Beste Variante) 