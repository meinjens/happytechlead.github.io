---
layout: post
title: Ist TDD tot???
tags: [tdd, test driven development]
---

Die aktuelle Diskussion von [David Heinemeier Hansson](http://de.wikipedia.org/wiki/David_Heinemeier_Hansson "Wikipedia Eintrag zu David Heinemeier Hansson") (DHH) "Is TDD dead?" nehme ich zum Anlass, um mich ebenfalls zu dem Thema zu äußern. DHH hat sich in seinem Talk auf der [Railsconf 2014](https://www.youtube.com/watch?v=9LfmrkyP81M "Keynote auf der RailsConf 2014 by DHH") sehr kritisch gegenüber [TDD](http://de.wikipedia.org/wiki/Testgetriebene_Entwicklung "Wikipedia Eintrag zu TDD") geäußert. In einem [Google Hangout](https://plus.google.com/u/1/b/102046517467703229044/events/couv627cogaue9dahj08feoa6b8 "Google Hangout zu "Is TDD dead?"") diskutiert er öffentlich mit [Martin Fowler](http://martinfowler.com/ "Website von Martin Fowler") und [Kent Beck](http://de.wikipedia.org/wiki/Kent_Beck "Wikipedia Eintrag über Kent Beck"), ob Test-Driven-Development wirklich die richtige Methode ist, um heute zu programmieren.

## Die Kritikpunkte

**Definition von Unit-Test ist nicht hilfreich  
**Einer der Kritikpunkte ist, dass die Definition von Unit-Tests nicht hilfreich ist. Unit-Tests sollen per Definition in TDD sehr schnell ablaufen (< 1 Sekunde).  Unit-Tests dürfen per Definition in TDD nicht mit der Datenbank, dem Filesystem oder anderen Komponenten zusammenarbeiten. Das ist aus Sicht von DHH wenig praktikabel und kaum durchzuhalten.

**Mock-Driven-Development beschädigt die Architektur**  
Der zweite Kritikpunkt ist, dass durch den Anspruch alles entkoppeln zu wollen, sehr häufig auf Mocks zurückgegriffen wird.  So wird auch innerhalb eines Softwaresystems die eigene Logik durch Mocks ersetzt. Dadurch wird jedoch die Architektur zerstört, so DHH.

**Red-Green-Refactor ist nicht immer praktikabel**  
Der dritte Kritikpunkt ist, dass der verpflichtende Arbeitsablauf von TDD: "Write a failing test (Red), Make it pass (Green) and Refactor" (R-G-R) nicht immer anwendbar ist.

## Meine Gedanken dazu

Während meiner gesamten Zeit als Entwickler hat sich bislang keine Methode und kein Prinzip als uneingeschränkt gültig erwiesen. Vielmehr begreife ich es als ein großen Werkzeugkasten, in dem immer wieder neue bessere Werkzeuge ergänzt werden. Und so sehe ich auch TDD als ein weiteres Werkzeug. Und natürlich sind dann nicht automatisch alle anderen Werkzeuge veraltet.  Die neue Bohrmaschine bohrt schneller und sauberer, als das alte Dingen mit der Kurbel.

**Bei den Unit-Tests die Testpyramide nicht vergessen**  
Laut der [Test Pyramide (ursprünglich von Mike Cohn)](http://martinfowler.com/bliki/TestPyramid.html "Test-Pyramide") sollte eine Breite Basis der Tests aus Unit-Tests bestehen. Darüber folgen die Komponententests, Integrationstests, Systemtests oder verschiedene andere Abfolgen in der Granularität. Jede Kategorie von Test lässt sich als Unit-Test (Test mit Hilfe eines xUnit-Frameworks) umsetzen. Aber deswegen ist es noch lange kein Test, der nur die einzelne Unit testet. Natürlich testet ein Komponententest auch das Zusammenspiel mit den kleineren Units. Aber irgendwann ist dann Schluß, dann schwenke ich zu Systemtests um. Und dort wird natürlich das gesamte Umfeld (Deployment Container, Datenbank, Webservices) in den Test mit einbezogen. Dann habe ich aber die Entwicklungsphase der Kernapplikation bereits verlassen und bin dabei die einzelnen Komponenten meiner Anwendung zu einem System zusammen zu bauen.

**Mocking nur wenn es notwendig ist**  
Was war der eigentliche Grund um Mocks einzusetzen? Soweit ich mich erinnern kann, ging es darum Systeme, die meist nur in der Produktion verfügbar sind, zu ersetzen, wie Datenbanken, Webservices o.ä. Mittlerweile werden Mocks auch eingesetzt, wenn alle unterliegenden Schichten zu lange für die Ausführung benötigen.

Aber ist das wirklich der richtige Ansatz? Für ein großes Subsystem, das behandelt werden kann wie eine Blackbox, ja klar. Aber auch nur dann, während ich entwickle und ich im Red-Green-Refactor-Cycle bin. Denn nur dann brauche ich kurze Feedbackzeiten. Integrationstest und Regressionstest beziehen das gesamte System auf einer Testumgebung mit ein und informieren mich, falls ich im Zusammenspiel der Systeme etwas übersehen habe.

**Red-Green-Refactor ist nicht immer praktikabel**  
Das ist wohl jedem selbst überlassen. Ich habe mich am Anfang schwer getan überhaupt den richtigen Einstieg zu finden. Gerade für Informationssysteme ist es nicht leicht die eigentliche "Businesslogik" auszumachen. CRUD Operationen als BusinessLogik scheiden erschienen mir als zu trivial. Ich starte derzeit immer mit der Validierung. Dieser lässt sich gut mit dem R-G-R-Cycle entwickeln.

Und bei vielen Problemen falle ich in klassische Verhaltensmuster zurück. Insbesondere wenn ich mit schwergewichtigen Frameworks arbeite, die kein vorgegebenes Testverfahren haben. Aber ich weiß aus Erfahrung, dass, wenn ich möglichst viele Entscheidungen durch Tests validiere, ich am sichersten sein kann, dass meine Implementierung korrekt ist. Ich denke einfach, dass wir noch jede Menge in Tests und Test-Werkzeuge investieren müssen, damit uns das gelingt.

## Mein Zwischenfazit

Kent Beck: "There are much more other ways." Ja das würde mich sehr interessieren. Aber "Is TDD dead?" Nein, hierzu Lande ist es noch nicht mal richtig geboren! In meinem Umfeld gibt es da noch jede Menge zu lernen. Ich erlebe oft noch Implementierungen, die vollkommen frei von jeglichen automatisierten Tests sind (Free Code).

Soll man TDD dogmatisch einsetzen? Ja! Solange bis man es gelernt und verinnerlicht hat. Dann hat man die genügende Reife, um abzuwägen, wann man die Regeln brechen kann und sollte und wann nicht.

Am kommenden Freitag geht es weiter in der Diskussion in dem [zweiten Teil](https://plus.google.com/events/couv627cogaue9dahj08feoa6b8 "Google Hangout zu "Is TDD dead?""). Zwischenzeitlich geht die Diskussion auch in den vielen Blogs weiter:

*   [Mockists Are Dead. Long Live Classicists.](http://www.thoughtworks.com/insights/blog/mockists-are-dead-long-live-classicists)
*   [UnitTest](http://martinfowler.com/bliki/UnitTest.html)