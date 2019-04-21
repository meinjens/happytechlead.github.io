---
layout: post
title: Test-Driven-Development - Zwischen Traum und Wirklichkeit
bigimg: /assets/einhorn_6833346648_65b0f3efdb.jpg
tags: [become agile]
---

Test-Driven-Development (TDD) ist der Anspruch, den ich an meine eigene Arbeit stelle. Aber häufig ist es für mich noch sehr schwierig diese Praktik überall anzuwenden. Die üblichen Tests zu schreiben ist dabei nicht das Problem. Es ist eher das viele drum herum, was mir oft Probleme bereitet: mit welchen Tests fange ich an, Granularität von Tests, Test-Frameworks und der berühmte Zeitdruck.

## Mein Leben vor SUnit

Zum Ende meiner Ausbildung hatte ich die Aufgabe bekommen Unit Tests für ein Software System in Smalltalk zu evaluieren. Das war mein allererster Berührungspunkt mit Software Tests. Vorher war alles reines Tüfteln: Versuch und Irrtum. Je nach Programmiersprache hat das teilweise lange gedauert, bis man das programmierte Ergebnis testen konnte: Typing, Compiling, Linking, Testing und wieder von vorne. Ab dem Zeitpunkt meiner Abschlussarbeit, waren Tests bei meiner Arbeitsweise mehr ins Zentrum gerückt.

## Wo fange ich an?

Der erste Test ist für mich oft der Schwerste. Ich falle meist noch mit der Tür ins Haus und will zu schnell die generelle Lösung entwerfen. Mir hilft es mich immer wieder auf einzelne Fehlersituationen zu fokussieren. Was soll passieren, wenn das Ergebnis null oder ein leeres Objekt ist? Was kann alles schief gehen? Wie verhält sich das System, wenn die Schnittstelle offline ist? Diese Situationen sind sehr speziell und erfordern meist wenig Code.

Ich erinnere mich an das Training mit Uncle Bob und die [Transformation Priority Premise](https://8thlight.com/blog/uncle-bob/2013/05/27/TheTransformationPriorityPremise.html). Er zeigt damit Wege vom Spezialfall zur Generalisierung auf. Diese Wege liefern jede Menge Hinweise, wie der nächste Test ausschauen und damit auch welchen Weg die Software nehmen kann.

Eine Skizze mit dem groben Aufbau helfen mir auch oft weiter: Welche Entitäten sind beteiligt? Welche Anwendungsfälle werden angewendet? Wie sehen die Schnittstellen aus?

Dann einfach loslegen und mit dem Code arbeiten; im Pairing reflektieren; Pseudo Code schreiben; **Red**\-**Green**\-**Refactor**; das Ergebnis "fühlen" und so lange schmieden, bis es passt. Steht das Grundgerüst erstmal geht der Rest meistens wie von selbst.

## Granularität von Tests

Bei Unit Tests ist die technische Herausforderung keine sonderlich Große. Viele Probleme sind bereits gelöst. Es gibt unzählige Artikel und HowTos zu den verschiedenen Test-Frameworks. Schwieriger wird es dann schon das richtige Augenmaß bei dem Umfang der Tests zu wählen und gemäß der [Test-Pyramide von Mike Cohn](https://www.mountaingoatsoftware.com/blog/the-forgotten-layer-of-the-test-automation-pyramid) mit den Tests auch nur das Notwendige zu testen. Beispielsweise ist es nicht effizient viele System-Tests durch die UI zu implementieren und dann auf Unit-Tests zu verzichten ("Das wird ja durch die UI getestet!").

Was teste ich also wie? Und wo sind die Grenzen meines Tests?

### Unit-Tests

Diese Tests testen die kleinsten Units. Sie haben keine Abhängigkeiten zu anderen Units und testen nur die innere Funktion. Zu dem Verfahren und Umfang ist - denke ich - bereits das meiste klar.

### Komponenten-Tests

Diese Tests testen die Schnittstelle und damit auch das Zusammenspiel zwischen zwei Units. Der Fokus sollte jedoch hier auf das Interface der zu testenden Units liegen. Externe Abhängigkeiten zu Laufzeitumgebungen, externen Systemen o.ä. sind hier ausgeschlossen.

### Integrations-Tests

Diese Tests bringen Module das erste Mal in eine Laufzeitumgebung (z.B. Spring Boot, TomCat Webapplication) und prüfen, ob die Komponenten in einer Laufzeit-Umgebung lauffähig sind. Werden alle Objekte zum richtigen Zeitpunkt initialisiert? Wird die Konfiguration gefunden und geladen? Klappt das Zusammenspiel mit der Laufzeitumgebung? Funktioniert die Kommunikation zwischen externen Systemen?

Die Ausführung ist teuer, da bei den Tests eine Laufzeitumgebung erzeugt werden muss. Deswegen ist es nicht ratsam mehr als das oben genannte zu Testen. Die Ausführungsdauer ist auch der Grund, warum Frameworks, die immer einen Container brauchen - wie zum Beispiel Apache Camel - immer schwer gewichtig bleiben. Beispiel: Um einen Test für eine Camel Route zu implementieren, ist nicht nur viel Code zur Initialisierung erforderlich, sondern es kann die richtige Funktion der Route nur in einem Integrations-Test geprüft werden.

### Akzeptanz-Tests

Dieses Tests testen die fachlichen Funktionen des Systems. Optimaler weise wird die Fachlichkeit durch eine API und nicht durch die UI getestet. Aber das ist einfacher gesagt als getan. Nicht selten gibt es einen Anteil von Business Logik, der in der UI hinterlegt ist ("Architektur Smell"). Den würde man mit den Tests durch die API umgehen.

Tests durch die UI sind nicht nur teuer in der Ausführung, sondern auch teuer in der Wartung, da sich die UI für gewöhnlich öfter verändert. Abhilfe könnte man schaffen, indem die UI möglichst stabil gestaltet wird und Patterns wie z.B. [BEM](http://getbem.com/introduction/) verwendet werden. Aber es bleibt die teure Ausführung, Setup- und Wartungskosten beim Aufsetzen der Testfarm.

### System-Tests

Diese Tests sollen das gesamte System auf korrekte Ausführung prüfen. Eigentlich muss hier aber nur noch eines getestet werden: Ist mein System mit der richtigen Konfiguration initialisiert? Dazu zählt ja nicht nur die eigentliche Software, sondern auch alles drum herum: Datenbank, Application Server, Web Server, Load Balancer etc. Heutzutage lassen sich auch diese Komponenten sehr gut isoliert testen. Hier nur ein paar Methoden, die ich erfolgreich einsetzen konnte:

**Smoke-Tests**

Die Smoke-Tests sollen Schlüsselfunktionen auf Korrektheit testen und decken die sog. "80% Fälle" ab. Also die 80% der UseCases, die am häufigsten verwendet werden. Diese Tests sollen nur sicherstellen, dass das Wichtigste nach wie vor funktioniert.

**Health-Checks**

Funktioniert die Verbindung zur Datenbank? Ist mein Webservice vom Drittanbieter erreichbar? All das lässt sich mit Hilfe von Health-Checks bequem testen. Das erspart einem den u.U. manuellen Test über die UI, ob auch "genau die Datenquelle für das eine Eingabefeld im 4. Schritt des Checkouts" verfügbar ist. Sofern das angebundene System verfügbar ist, sollten bereits die Integrations-Tests alles andere über Tests abgedeckt haben.

Health-Checks bieten verschiedene Monitoring Systeme von Haus aus an. Ich habe jedoch die Erfahrung gemacht, dass es von Vorteil ist, wenn die Software selbst einen kurzen Check implementiert (z.B. die Verbindung zur Datenbank aufbauen), da die Infrastruktur von Monitoring Systemen und Software manchmal abweichen können.

**Regeln im nginx**

Ich arbeite in der Web-Entwicklung und da bin ich häufig auch mit [nginx](https://www.nginx.com/) Setups konfrontiert. Die im laufenden Betrieb zu testen heißt, dass einige Kunden kurzzeitig Fehler zu Gesicht bekommen oder der Server kurzfristig sogar ganz ausfällt. Eine Alternative ist es mit Hilfe von Hilfe von [Ansible](https://www.ansible.com/) und [Vagrant](https://www.vagrantup.com/) lokal eine VM zu erzeugen und dort die Regeln zu testen, ohne den Live-Betrieb zu stören.

Ich habe häufig [Locations](https://www.digitalocean.com/community/tutorials/understanding-nginx-server-and-location-block-selection-algorithms) in unterschiedlichen Formen. Mit Bibliotheken wie [request](https://www.npmjs.com/package/request) in [NodeJS](https://nodejs.org/en/) können Requests zusammengestellt, gesendet und anschließend die Antwort analysiert werden (z.B. Header, Caching). Somit kann ich viele Regeln automatisiert prüfen und fühle ich mich wesentlich sicherer, auch dann wenn größere Konfigurationsänderungen gemacht werden müssen.

**Docker Images**

Mit Hilfe von DockerSpec lassen sich Docker Images auf korrekte Funktion testen. Es ließe sich sogar test-getrieben ein Docker-Image entwickeln. Da die Ausführungszeit eines Durchlaufes meist mehrere Sekunden braucht, habe ich mich dagegen entschieden. Die Schritte zwischen **Red**\-**Green**\-**Refactor** sind also schon etwas größer. Es ist dennoch eine große Hilfe.

## Testentwicklung unter Zeitdruck

Wer kennt das auch? Du bist spät dran (warum auch immer) und willst oder musst noch das Feature fertig stellen. Das Gewissen hat schon angeklopft und ruft: "Eigentlich sollte ich jetzt dafür einen Test schreiben...!" Aber Du entscheidest Dich auf Grund der knappen Zeit den Test wegzulassen. "Das kann ich ja nachher noch machen..." Das Gewissen so: "Wir beide wissen, dass Du das nicht machst!!" Und Du so: "Doch! Diesmal schaffe ich das!" Viel später das Gewissen so: "Siehste!?!"

Mir geht es insbesondere dann so, wenn ein neues Framework, Technologie oder Sprache im Einsatz ist. Dann fehlt mir das notwendige Know-How, um die Tests zu implementieren und so vermute ich geht es vielen anderen auch. Test-getriebene Entwicklung ist dann einfach umzusetzen, wenn man schnell zum Ziel kommt und die kurzen Feedback-Zyklen erlebt. Muss man sich erst noch mit neuen Dingen auseinander setzen und diese Verstehen, so wird häufig der Weg des geringsten Widerstandes eingeschlagen, um zum Ziel zu kommen.

Die Lösung dafür ist also ganz einfach: Training, Training, Training. D.h. regelmäßiges Üben und immer wieder Verbessern der eigenen (Test-) Fertigkeiten. Solange bis auch unter Zeitdruck die Tests einigermaßen flüssig von der Hand gehen. Sofern ich jedoch noch kein Training hatte und ich unter Zeitdruck stehe, versuche ich wenigstens die Tests zu schreiben, in denen ich Übung habe.

## Manuelle Tests

Manuelle Tests lassen sich nicht vermeiden! Sie sollten sich jedoch auf [explorative Tests](http://www.satisfice.com/articles.shtml) beschränken.

Idealvorstellung? Unrealistisch? Träumer? Nein, ich sehe das ganz realistisch: Bei einer Testabdeckung von beispielsweise nur 40% muss ich die anderen 60% durch manuelle Tests abdecken und das eigentlich bei jeder Änderung. Schnelle Releasezyklen sind dann gar nicht mehr möglich. Selbst ein Release in einem Zwei-Wochen-Sprint wird dann sehr schwierig.

Und betrachtet: Bei einer Testabdeckung von 40%, nehme ich das Risiko auf, dass in den übrigen 60% des Codes Fehler versteckt sind, die ich nur durch Stochern im Nebel mit einem Grashalm finden kann.

## Agile Prinzipien

„Deliver frequently in short iterations“ und „Technical excellence" sind die beiden Prinzipien und damit die Motivation für TDD. Ohne dieses Vorgehen sind auch kleinere Änderungen an der Software nur mit einem hohen Zeitaufwand möglich.

_Das Bild ist von [yosuke muroya](https://www.flickr.com/photos/hamur0w0/) - vielen Dank dafür!_