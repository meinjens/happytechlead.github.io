---
layout: post
title: Continuous Delivery: Zwischen Null und Hundert Prozent
tags: [devops, continuous delivery]
---

Moderne Projekte erfordern moderne Methoden. Continuous Delivery ist bereits fester Bestandteil. Moderne Methoden werden mit modernen Werkzeugen verknüpft. So wird Continuous Delivery oft in einem Atemzug mit Tools wie Puppet, Chef oder ähnlichen Tools aus dem Sektor "Infrastructure as Code" genannt.

Was jedoch, wenn moderne Werkzeuge nicht eingesetzt werden können oder wollen? Bevor man bei Null bleibt, gibt es immer noch andere Möglichkeiten. Ich möchte in diesem Artikel ein Beispiel zeigen, wie man mit relativ einfachen Mitteln ein Continuous Delivery umsetzen kann. Ich konzentriere mich dabei auf den Schritt "Build System".

[![Build - Test - Release](http://www.agile-engineering.de/wp-content/uploads/2013/12/build-test-release.png)](http://www.agile-engineering.de/wp-content/uploads/2013/12/build-test-release.png)

Schritte im Continuous Delivery: Build - Test - Release

## Ein einfaches Projekt-Beispiel

In einem Portal-Projekt mit Liferay geht es darum auf jedem System einen vollständigen Portalserver einzurichten. Da wären alle Entwickler-Rechner, Integrations-, Test- und Produktionssystem. Dazu sind auf den jeweiligen Maschinen folgende Schritte notwendig:

1.  Liferay Bundle runterladen
2.  Bundle entpacken
3.  setenv.sh mit Einstellungen zur JVM erweitern
4.  server.xml anpassen

Diese Schritte sind zwar noch recht übersichtlich, aber wenn man die Anzahl der Systeme summiert, kommt man schnell auf 5-10 Installationen mit sehr unterschiedlichen Konfigurationen. Und da ist noch nicht mal ein Clusterbetrieb mit eingerechnet.

## BUILD not the whole SYSTEM  

Wir greifen nun nicht auf die modernen Werkzeuge zurück, die die gesamte Infrastruktur aus Code erzeugen. Wir gehen davon aus, das wir das Basissystem auf herkömmliche Weise installiert bekommen:

*   installiertes Betriebssystem
*   eingebunden in die Netzwerk-Infrastruktur
*   installiertes JDK
*   installiertes und konfiguriertes Datenbank-System

Wenn wir also schon nicht das ganze System automatisch erzeugen können, dann doch bitte schön den eigentlichen Kern: Application Server + Anwendung + Konfiguration.

Dazu verwende ich ANT. Angereichert um ein einfaches Konfigurationmanagement ist es hervorragend geeignet, um die immer wiederkehrenden Installationen zu erledigen. Es ist dabei recht einfach und leicht zu erlernen.

## Konfigurationsmanagement mit ANT

Das Konfigurationsmanagement besteht aus mehreren Property-Dateien.

\[raw\]  
<property file="${automator.dir.config.environment}/env.${system}.properties" />  
<property file="${automator.dir.config.environment}/env.${user.name}.properties" />  
<property file="${automator.dir.config.environment}/env.${hostname}.properties" />  
<property file="${automator.dir.config.environment}/env.properties" />  
\[/raw\]

Das Laden der Properties in ANT ist so eingestellt, dass die Property, die zuerst gesetzt wird, nicht mehr überschrieben wird. Daraus ergibt sich eine Priorität für die verschiedenen Property-Dateien:

1.  Property mit dem Parameter -Dsystem={systemname}
2.  Property-Datei für den Benutzer (Dateiname: env.{username}.properties)
3.  Property-Datei für den Host (Dateiname: env.{hostname}.properties)
4.  Default-Property-Datei (Dateiname: env.properties)

Damit lassen sich die Konfigurationen für alle Systeme in Property-Dateien ablegen.

Alle Details zur Funktionsweise befinden sich in der Datei [build-common.xml](https://github.com/meinjens/automator/blob/master/includes/build-common.xml "build-common.xml")

## Module

Ich arbeite mit einem solchen Konfigurationmanagement in unzähligen Projekten. D.h. jedoch auch, dass für ähnliche Aufgaben immer wieder ähnliche Scripte entstanden sind.  Module sollen nun nach Möglichkeit diese Scripte ersetzen. Sie sollen dabei einfach hinein- und herausnehmbar sein.

Ein Modul ist für ein Teilsystem zuständig. Das kann ein Servlet Container, wie z.B. TomCat sein. Ein Modul besteht aus einem Verzeichnis mit einer Build- und Property-Datei. Die Build-Datei beinhaltet fest definierte Targets:

*   clean  
    Löschen der Build-Dateien
*   build  
    Erzeugen des Teilsystems
*   deploy  
    Installieren des Teilsystems
*   show-module-properties  
    Anzeigen der Properties für das Modul

[Beispiel eines Moduls](https://github.com/meinjens/automator/tree/master/modules/sample "Beispiel eines Moduls")

Die Ladereihenfolge der Module kann über die System-Properties gesteuert werden. Dazu werden die Modul-Verzeichnisse durch Komma getrennt angegeben:

\[raw\]  
##  
\## Modules to use for the system  
##  
system.modules=tomcat\_7\_liferay\_6\_2\_bundle,tomcat\_natives  
\[/raw\]

## automator

Das Gesamtprojekt heißt [automator](https://github.com/meinjens/automator "automator") Dort finden sich weitere Module in einer allerersten Version.