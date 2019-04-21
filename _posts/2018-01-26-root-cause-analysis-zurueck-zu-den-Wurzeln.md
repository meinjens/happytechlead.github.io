---
layout: post
title: Root Cause Analysis, zurück zu den Wurzeln
bigimg: /assets/hieroglyphen_5967262068_2576ca5648.jpg
tags: [become agile]
---

Ich war lange Zeit als Feuerwehrmann in Projekten tätig. D.h. Fehler analysieren und reparieren. Dabei habe ich verschiedene Situationen erlebt: viel und wenig Zeitdruck, Mitarbeiter oder Chefs stehen hinter mir und drängeln, bekannte und unbekannte Ursachen oder bekanntes und unbekanntes Terrain. Jeder Fehler war eine neue Herausforderungen, aus der ich etwas lernen konnte.

## Meine Ungeduld

Mein Vater hat mich früher immer zum Angeln mit genommen. Einmal pro Nachmittag hab ich dann meine Schnur durcheinander gebracht. Ich war ungeduldig und zog an der erst besten Schlaufe. Anstatt den den Knoten aufzulösen, zog sich das Gewirr nur noch weiter zusammen. Es hat sehr lange gedauert, bis ich den Knoten eigenständig auflösen konnte. In vielen Fällen habe ich die Angel auch nur frustriert in die Ecke geworfen. Es sollte mir viel später weiterhelfen.

## Dunkle und Helle Seite der Macht

Es gibt Fehlerkorrekturen die gehen schneller, sind leichter und sind deshalb verführerisch. Besonders dann wenn man unter Druck steht. Die meisten Fehlerkorrekturen, die ich überhastet erledigt habe, kamen meistens irgendwann wieder. Entweder wenn ich das Umfelds des Fehlers noch mal berührt habe oder ich die Software erweitern musste. Für mich ist deshalb der Pfad zur hellen Seite der Macht, den Fehler auf den Grund zu gehen und sich die Zeit zu nehmen, um die eigentliche Ursache zu finden. Für diese Seite habe ich mich entschieden.

<iframe width="560" height="315" src="https://www.youtube.com/embed/vmO7y7hJG6c" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Der Pragmatische Lösungsweg

"Sei doch mal pragmatisch!" tönt es aus dem Projektmanagement Büro. Häufig mit einem Ausdruck von leichter Panik bis Angst, wenn ich den Fehler nicht gleich gefunden hatte. Es zuckt kurz in mir. Die dunkle Seite versucht kurz Besitz von mir zu ergreifen. Ich wäge im Kopf die unterschiedlichen Lösungswege ab und bewerte die Aufwände. Ich entscheide mich für einen kleinen schnellen Fix. Erstmal für den Kunden die Situation entschärfen. Dann bleibt genügend Zeit sich der Ursache zu widmen und vor allen Dingen dem Projektleiter die Situation zu erklären.

## Aktio = Reaktio

"Für jeden Fehler gibt es eine Ursache!" Ich weiß gar nicht, ob man das so mit Sicherheit sagen kann. Das ist jedoch meine Grundeinstellung, wenn ich mich auf die Suche nach Softwarefehlern begebe. Ich stelle also Thesen auf und teste sie. Zum Testen nutze ich je nach Anwendungsfall unterschiedliche Werkzeuge.

*   Decompiler für 3rd Party Libs
*   Debugger für Legacy Code
*   Chrome und Firefox für Webdebugging im Client
*   Webdebugging Proxy für den Netzwerkverkehr

Idealerweise kann ich dann einen Test schreiben oder ergänzen, der den gefunden Fehler explizit testet. Damit ist der Fehler nachhaltig beseitigt.

## Fehler im System?

Die Behebung des gefundenen Bugs ist der erste Schritt zur Fehlerkorrektur. Viele Fehler sind jedoch nur ein Symptom für den eigentlichen Fehler. Häufig wiederkehrende Fehler oder die sogenannte "Magic" hat meistens Ursachen, die nicht unbedingt in der Technik zu finden sind.

Ein Bespiel: Mehrere Teams arbeiten parallel an einem Software System. Trotz größter Sorgfalt aller Entwickler kommt es beim abschließenden Systemtest immer wieder zu Fehlern. Eine erste Analyse hat ergeben, dass nicht immer alle Artefakte auf dem Testsystem angekommen sind bevor der Systemtest begonnen wurde. Beim genaueren Analysieren wurde festgestellt, dass sich die Team gegen eine explizite Versionierung entschieden hat. Sobald ein eingecheckter Codestand als stabil getestet wird, wird eine Version erzeugt. Auf den ersten Blick kein schlechtes Vorgehen. Jedoch hatte das zur Folge, dass sich unterschiedliche Entwicklungsstände einzelner Features überlagern.

Solche Fehler sind nicht in der Software selbst, sondern in der Organisation des Entwicklungszyklus zu finden. Sie sind nur zu Beheben, wenn sich alle Entwickler einig sind, ihr Verhalten ändern zu müssen. Nicht selten hat eine Verhaltensänderung aber auch einen großen Effekt auf die Qualität und Entwicklungsgeschwindigkeit.

## Ursachenforschung

Für die Fehler in der Organisation oder in fachlichen Anforderungen lassen sich nicht mit klassischen Werkzeugen wie Debuggern o.ä. korrigieren. Aus diesem Grund finde ich diese Fehler auch sehr viel schwieriger und herausfordernder. Es gibt aber auch da Methoden um den eigentlichen Fehlern auf den Grund zu gehen. Zwei Methoden habe ich kennengelernt:

*   5 Why
*   Ursache-Wirkung-Diagramm

Meine Erkenntnis bei Fehlern in Organisationen ist, dass meistens mehrere Ursachen gefunden werden. Es gibt oft nicht die eine Ursache, die das Problem verursacht. Es nimmt zudem viel Zeit für Analyse und Behebung in Anspruch. Insbesondere dann wenn mehrere Abteilungen oder auch die Geschäftsführung beim zu untersuchenden Umfeld beteiligt sind.

## Es lohnt sich

Der Pfad zur hellen Seite lohnt sich! Ich habe somit viele sehr tiefe Einblicke in Organisationen und letztendlich in die Menschen selbst bekommen. Oft muss man dabei sehr geduldig sein und nicht gleich beim ersten Knoten die Angel in die Ecke werfen. Das hat mich in die Lage gebracht "Berge zu versetzen", langwierige Konflikte aufzulösen und Arbeitsprozesse deutlich zu beschleunigen.

_Das Bild ist von [ThoMo1969](https://www.flickr.com/photos/thomo1969/) - vielen Dank dafür!_