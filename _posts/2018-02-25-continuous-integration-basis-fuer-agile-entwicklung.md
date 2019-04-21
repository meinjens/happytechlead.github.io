---
layout: post
title: Continuous Integration - Basis für agile Entwicklung
bigimg: /assets/bienenwabe_14389091497_2ef54d37c7.jpg
tags: [become agile]
---

Agil sein, bedeutet, von einem stabilen Zustand in kurzer Zeit in einen neuen stabilen Zustand wechseln zu können. Damit ein Team agil sein kann, ist es notwendig die Arbeitsweise darauf auszurichten. Ein klassisch organisiertes Team mit lang laufenden Entwicklungszyklen und -praktiken wird es deshalb nie von jetzt auf gleich in die agile Welt schaffen. Ein erster Schritt in die agile Welt ist die Entwicklungszyklen auf kontinuierliche Integration mit kurzen Feedbackzeiten umzustellen.

## Continuous Integration

Damit kontinuierliche Integration in einem agilen Team gut funktioniert sollte folgendes gegeben sein:

*   Änderungen werden kontinuierlich in ein Softwarerelease eingearbeitet.  
    D.h. immer sobald ein Feature, Bugfix oder sonstiger Change fertig ist.
*   Die Einarbeitung der Änderung in die Software kann in kurzer Zeit geschehen.  
    D.h. innerhalb weniger Minuten steht das System mit dem neuen Softwarestand zur Verfügung.
*   Um die Zeit kurz zu halten sind immer wiederkehrende Aufgaben (voll) automatisiert.  
    Dazu zähle ich Build, Test und Deployment.
*   Die Zeit für die Nachvollziehbarkeit von Fehlern sollte gering sein.  
    D.h. dass ggf. Features isoliert testbar gemacht, Testergebnisse gut aufbereitet, Logs schnell einsehbar, Fehlermeldungen aussagekräftig gemacht und die Software genug robust gemacht werden müssen.
*   Continuous Integration System und Zielsysteme sollte für die Entwickler zugänglich sein  
    D.h. alle Systeme sollten durch die Entwickler veränderbar sein können. So ist eine zwischengeschaltete IT Abteilung mit aufwendigen IT Prozessen ein Killer für Continuous Integration, da die IT Prozesse und die Trennung zwischen Entwicklung und Deployment die Feedbackzeiten enorm erhöhen.

## Code Repository

Damit Änderungen kontinuierlich in die Software eingearbeitet werden können, ist es notwendig, dass in einem gemeinsamen Code Repository gearbeitet wird. Dabei müssen neue Features oder Bugfixes isoliert entwickelt werden können, damit sich die Änderungen nicht ggf. untereinander beeinflussen. Neue Features müssen einfach in den Hauptstrang der Entwicklung integriert werden können.

Für die Entwicklung in den Mainstream Programmiersprachen ist es dringend empfehlenswert auf eine Versionsverwaltung wie [Git](https://git-scm.com/) zu setzen. Zusätzliche Werkzeuge wie [Gitlab](https://about.gitlab.com/) bieten ähnliche Funktionalitäten wie Github. Es ist das quasi Standardwerkzeug für jede moderne Entwicklungsplattform. Ältere Versionsverwaltungen wie CVS oder SVN haben ausgedient! Bitte migrieren!

## Branching Model

Damit die Änderungen übersichtlich und einfach integrierbar bleiben, gibt es verschiedene Möglichkeiten wie man den Entwicklungsprozess gestalten kann. [Vincent Driessen beschreibt in seinem Blog-Artikel eine Variante wie man Feature Branches](http://nvie.com/posts/a-successful-git-branching-model/) einsetzen kann. Wir haben dieses Modell im Team ausprobiert und festgestellt, dass man dies durchaus noch schlanker gestalten kann. So nutzen wir derzeit den Master Branch sehr wenig bis gar nicht und entwickeln auf dem develop Branch die Software weiter. Die Verwendung von Feature Branches ist dagegen ein tägliches Arbeitsmittel. Ist ein Feature fertiggestellt, so erfolgt ein Merge Request mit Code Review. Nach Annahme des Merge Requests wird automatisch die neue Version gebaut und steht potentiell für ein Deployment zur Verfügung.

Jedes Team sollte für sich herausfinden, welches Branching Model es auswählt. Je einfacher desto besser. Lieber klein anfangen und dann Schritt für Schritt verbessern. So bietet es sich an, zunächst nur mit Feature Branches zu starten, wenn man noch ungeübt mit den Werkzeugen und Verfahren ist. Zielstellung ist, dass der Arbeitsablauf weniger den Fortschritt behindert sondern die saubere Integration mehr fördert.

## Automatisierung des Builds

Der Build sollte zentral auf einem Continuous Integration System (z.B. [Jenkins](https://jenkins.io/)) laufen. Es bietet sich dort auch an die statische Code Analyse (z.B. [SonarQube](https://www.sonarqube.org/)) zu integrieren und die Findings zentral zu verwalten bzw. wieder zu verteilen.

## Automatisierung der Tests

Welche Tests sollten automatisiert werden? Meine Antwort: Möglichst alle.

*   **Unit-Tests** - Tests der einzelnen Units (z.B. Klassen)  
    Diese Tests lassen sich meist gut automatisieren, da sie von den meisten Build-Systemen (Maven, Gradle, grunt gulp o.ä.) unterstützt werden.
*   **Komponenten-Tests** - Tests des Zusammenspiels mehrerer Units  
    Auch diese Tests lassen sich ähnlich wie Unit Tests implementieren und gut mit dem Build-System automatisiert ausführen. Viele Entwickler unterscheiden häufig nicht zwischen Unit und Komponenten Tests. Da sie von der Laufzeit ähnlich schnell sein sollten, muss man hier build-organisatorisch auch keine Unterscheidung machen.
*   **Integrations-Tests** - Tests in denen Komponenten innerhalb von Frameworks, Containern o.ä. getestet werden  
    Diese Tests laufen meist schon etwas länger, da erst noch ein Container o.ä. initialisiert werde muss, damit diese Tests starten können. Es bietet sich deshalb an, diese Tests aus dem Standard Build Prozess zu deaktivieren und eher auf einem Continuous Integration System laufen zu lassen. Dies sollten auch nur einige wenige Tests sein, da die Ausführung teuer ist, d.h. die Implementierung und Ausführung braucht viel Zeit.
*   **Akzeptanz-Tests** - Fachliche Tests, die das System über eine API testen  
    Diese Tests bieten eine sehr gute Möglichkeit das gesamte System systematisch auf die korrekte Ausführung zu prüfen, ohne den umständlichen Weg über die UI zu gehen.
*   **System-Tests** - Tests die gegen eine vollständig eingerichtete und laufende Umgebung testen  
    Diese Tests sind sowohl in der Entwicklung und Wartung als auch in der Ausführung teuer. Deshalb sollten das nur noch sowas wie Smoke Tests - ein kurzer Probelauf - sein. Trotzdem lassen sich diese Tests automatisieren und gut als letzter Check vor einem Deployment einsetzen.
*   **Performance-Tests** - Tests des gesamten Systems auf Ladeverhalten  
    Es lohnt sich absolut auch diese Tests zu automatisieren. So bekommt man schnell ein verändertes Performance Verhalten schnell mit und kann viel besser reagieren, anstatt sich am Ende eines Projektes in eine aufwendige Analyse zu stürzen. Die Ausführung solcher Tests kann teuer sein. D.h. eine Ausführung sollte vielleicht einmal pro Nacht erfolgen.
*   **Last-Tests** - Tests, die das System an die Lastgrenze bringen  
    Diese Tests werden wohl nur gelegentlich ausgeführt. Eine Automatisierung kann dennoch sinnvoll sein, um das Setup und die Durchführung der Tests nicht jedes Mal von Neuem zu beginnen.

Je höher der Grad der Automatisierung desto schneller kann sich eine Software verändern. Je mehr manuelle Tests durchgeführt werden müssen, desto länger braucht das Team um sicher zu sein, dass nach einer Veränderung alles funktioniert.

## Nachvollziehbarkeit in der Entwicklung

Nachvollziehbarkeit ist wichtig, wenn ich ein Feature entwickle. Ich benötige dazu eine isolierte Umgebung, damit ich sicher sein kann, dass ausschließlich mein Tun und Handeln Auswirkung auf die Software hat. Ist dies nicht gegeben, dann laufe ich Gefahr, dass sich mehrere Änderungen überlagern und ich u.U. einem Fehler hinter jage, den ich gar nicht verursacht habe.

Eine lokale Entwicklungsumgebung halte ich daher für unverzichtbar.

*   Das ist der kürzeste Weg von der Entwicklung bis zum Deployment
*   Es gibt keinen Einfluss durch andere Entwickler oder Anwender
*   Ich kann ein Gesamtsystem zu Laborbedingungen herstellen, ohne andere zu stören

Ich stelle gern ein Feature in meiner Entwicklungsumgebung soweit fertig, dass ich das anderen Kollegen zeigen kann. Gemeinsam kann man dann an der Lösung gemeinsam weiter arbeiten, Fehler finden und reproduzieren oder das Feature abnehmen.

## Nachvollziehbarkeit und Robustheit in der Ausführung

Nachvollziehbarkeit ist aber auch bei der Fehlersuche wichtig. Häufige Ursachen vom Schritt der lokalen Entwicklung zum Continuous Integration System sind - meiner Erfahrung nach - fehlende Konfiguration, andere Daten in Fremdsystemen oder Fehler in Schnittstellen zu Fremdsystemen. Deswegen ist der erste Schritt die eigene Software robust und gesprächig zu gestalten, damit solche Fehler sofort auffallen.

Die Logausgaben geben Aufschluss über eine fehlende Konfiguration oder es gibt Standardwerte bei fehlender Konfiguration (Diese werden natürlich auch im Log kommuniziert). Da Schnittstellen im Allgemeinen immer potentiell fehleranfällig sind, bietet es sich hier auch an ein besonderes Augenmerk auf das Fehlverhalten der Schnittstelle zu legen. Das Team muss in der Lage sein, schnell auszuschließen, dass es sich um einen Fehler in der Schnittstelle handelt.

Werkzeuge, wie [Kibana](https://www.elastic.co/de/products/kibana), unterstützen den Entwickler an Logs von mehreren Servern gleichzeitig zu kommen und mit ihnen zuarbeiten. [Netdata](http://my-netdata.io/) und [Prometheus](https://prometheus.io/docs/instrumenting/exporters/) helfen die Gesundheit des Systems im Auge zu behalten. Vielleicht lohnt es sich auch eigene Werkzeuge zu entwickeln, um wiederkehrende Fehler oder besonders kritische Fehlersituationen zu vermeiden (z.B. Ausgabe einer Liste aller installierten Module in einer Software mit Versionsnummer).

## Direkt ohne Umwege

Das Team sollte direkten Zugriff auf das Continuous Integration System sowie auf alle Systeme bekommen auf denen das Software System läuft. Warum? Weil es manchmal notwendig ist, sich direkt auf die Maschinen einzuloggen um einen Fehler zu finden und zu reproduzieren.

Häufig steht meine Meinung gegen unzählige IT Regularien oder künstlich aufgebaute Hürden (z.B. Abteilungsgrenzen). Fertiggestellte Software "über den Zaun werfen" und hoffen, dass sie läuft, ist schon lange nicht mehr zeitgemäß. Dies verlängert die Feedback Zeiten und verhindert somit eine schnelle Entwicklung. Die Teams in der heutigen Zeit sollten ohnehin so aufgestellt sein, dass auch die Kompetenz für einen regelkonformen Betrieb vorhanden ist.

## Agile Prinzipien

"Deliver frequently in short iterations" ist für mich an dieser Stelle das vorrangige agile Prinzip. Continuous Integration ist die agile Praktik, die ein agiles Vorgehen überhaupt erst ermöglicht.

_Das Bild ist von [Riccardo Meneghini](https://www.flickr.com/photos/foto_olio/) - vielen Dank dafür!_