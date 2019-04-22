---
layout: post
title: Solid principles
bigimg: /assets/
tags: [raspberrypi, pondpi, ansible]
---

> The only way going fast, is to go well. - Uncle Bob

## S - Single Responsibility Principle

> _A class should have one, and only one, reason to change._

*   Verantwortlichkeit hinsichtlich Änderungen:
    *   Was kann sich ändern?
        *   Zu welchem Zeitpunkt?
        *   Von welchem Stakeholder motiviert?
        *   In welchem Zeitintervall?
    *   Welche Gründe kann es geben um die Klasse zu ändern?
    *   Wie viele Änderungen der Anforderungen können an die Klasse gestellt werden?
    *   Für wie viele Stakeholder erfüllt die Komponente ihre Anforderungen?
*   Prinzip ähnlich wie Seperation of Concerns
*   Lässt sich einfach auch auf andere Dinge wie Klassen übertragen
*   Smell sind unkretete Namen wie Manager, Helper, Utils o.ä.

## O - Open Closed Principle

> _You should be able to extend a classes behavior, without modifying it._

*   Vergleichbar mit dem Strategy Pattern
*   Smell:
    *   Wenn ich eine Funktion hinzufügen will und erstmal andere Funktionen verändern muss.
    *   Hardcoded Referenzen zu konkreten Implementierungen
    *   Switch-Case / If-then-else
    *   High-Level-Klassen brauchen Low-Level-Klassen zur Compile-Zeit
*   Should: Ich möchte eine Funktion erweitern, also füge ich nur neuen Code hinzu.

## L - Liskov Substitution Principle

> _Derived classes must be substitutable for their base classes._

*   Smell:
    *   Type Checks innerhalb des Codes und Ausführung von Ausnahmen
    *   Vererbungsstruktur zweier Klassen, die überhaupt nichts gemeinsam haben
    *   Namen überprüfen, ob diese zur eigentlichen Aufgabe passen

## I - Interface Seggregation Principle

> _Make fine grained interfaces that are client specific._

*    Smell:
    *   Breites Interface mit sehr vielen Methoden
    *   Klassen implementieren ein Interface und die meisten Methoden sind leer implementiert.

## D - Dependency Inversion Principle

> _Depend on abstractions, not on concretions._

*   High level modules should not depend upon low level modules. Both should depend upon abstractions.
*   Abstractions should not depend upon details. Details should depend upon abstractions.
*   Verhindert, dass bei Änderung eines Details, alles noch mal gebaut werden muss, weil alles von einander abhängt.
*   Smell:
    *   Bei einer Änderung muss die gesamte Anwendung neu gebaut werden.