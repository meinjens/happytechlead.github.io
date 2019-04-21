---
layout: post
title: Implizite Qualitätserwartungen
bigimg: /assets/airport_ber_7189414714_1b6f443886.jpg
tags: [architecture, arc42, qualitätsszenarien]
---

Jeder Entwickler kennt die Situation: Die Software ist gerade fertig gestellt und ausgeliefert und sofort treffen die ersten Fehlermeldungen ein: "Die Software reagiert unter bestimmten Situationen langsam." Jetzt schnell nachgeschlagen in den nicht funktionalen Anforderungen.. und? Findet man dort etwas? Nein? Also kein Fehler?! Es war ja nicht spezifiziert. Der Ärger ist vorprogrammiert.

Jeder Architekt kennt die Situation: Eine Aufwandsschätzung wird vorgestellt und die geschätzten Aufwände sind - wie immer - zu groß. Jetzt beginnt das Feilschen und Argumentieren. Warum sieht die Lösung so aus? Geht das nicht günstiger? Braucht man so eine Infrastruktur? Können wir das Logging nicht weglassen?

In beiden Situationen hat man es mit fehlenden Qualitätsanforderungen zu tun. Oftmals ist sich der Auftraggeber dessen gar nicht bewusst. "Das war doch klar! Das muss man doch nicht extra erwähnen!" Doch, man muss!

Meine Erfahrung bestätigt immer wieder, dass Systeme ohne diese Anforderungen eine gewisse Schlampigkeit aufweisen. Ohne genaue Spezifikation der Qualitätskriterien findet auch keine Prüfung statt. Warum die Performance prüfen, wenn Sie dem Auftraggeber offensichtlich nicht so wichtig ist? Warum die Stabilität messen, wenn es keine Anforderung war? Warum die Analysierbarkeit sicherstellen, wenn Sie nicht bezahlt wurde?

Gernot Starke und Peter Hruschka schreiben in [arc42, der Vorlage für Architekturbeschreibungen](https://arc42.org), dass eine Architektur nicht ohne genaue Qualitätsanforderungen begonnen werden soll.

An dem Punkt wird es schwierig: Erstmal sind die Stakeholder für diese Anforderungen schwer zu finden. Es sind nämlich meistens die Nutzer also die Kunden des Kunden. Oftmals lassen sich aber nach geraumer Zeit die Entscheidungsträger finden. Zum zweiten ist die konkrete Formulierung der Qualitätsziele nicht immer einfach. Sie erfordert auch einen gewissen Mut. Aber im Grunde sind das die impliziten Erwartungen an die Qualität von Softwaresystemen.

"Das System soll in 95% der Fälle innerhalb von 1 Sekunde antworten. In 5% der Fälle kann die Antwort innerhalb von 1,5 Sekunden ausgeliefert werden.

"Als Betreiber der Software möchte ich einen Fehler innerhalb von 1 Stunde nachvollziehen können."

"Als Besitzer dieser Software möchte ich eine branchenübliche Technologie verwenden, um in der Zukunft die Software auch von einem anderen Dienstleister weiter betreiben lassen zu können."

"Ein Entwickler soll das System um eine Funktionalität innerhalb von 20PT erweitern können."

"Ein neuer Entwickler soll in der Lage sein, sich innerhalb von 10 PT in das System einarbeiten und eigene Module entwickeln zu können."

Qualitätsanforderungen sollten so konkret wie möglich zu Beginn des Projektes formuliert werden, damit sie einen nicht am Ende doch  durch eine Fehlermeldung oder eine unzufriedene Äußerung des Kunden erreicht. Gernot Starke bietet dazu eine große Sammlung an Beispielen:

*   [Ausformulierte Beispiele für Qualitätsziele](https://github.com/arc42/quality-requirements "Ausformulierte Beispiele für Qualitätsziele")

**_Ergänzung von Christian Fischer ([agile dojo](http://agiledojo.de))_**

Einen guten Hintergrundartikel zur Erstellung dieser Qualitätsszenarien sowie die Prüfung der Architektur in dieser Hinsicht gibt der Artikel von Raphael Bossek:

[http://raphaelbossek.wordpress.com/2010/10/08/qualitatsrezepte-fur-softwarearchitekturen/](http://raphaelbossek.wordpress.com/2010/10/08/qualitatsrezepte-fur-softwarearchitekturen/)

In der Regel schließt sich nach der Ermittlung der Nichtfunktionalen Anforderungen die Frage an, wie sichergestellt wird, dass diese auch im Laufe der Entwicklung angemessen berücksichtigt werden. Hierfür hat sich aus meiner Erfahrung eine einfache Tabelle, meist als Bestandteil des Qualitätshandbuchs, bewährt, in der für jedes Szenario die Prüfmethode sowie die entsprechenden Architekturstrategien aufgeführt werden.