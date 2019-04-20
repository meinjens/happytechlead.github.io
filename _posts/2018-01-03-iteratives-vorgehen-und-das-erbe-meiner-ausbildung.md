---
layout: post
title: Iteratives Vorgehen und das Erbe meiner Ausbildung
tags: [become agile]
---

Ich habe mir öfters schon mal die Frage gestellt, wie man ein agiles Mindset entwickeln oder etablieren kann. Früher war meine Antwort sicherlich: Dazu lass uns mal einen Workshop machen! Mittlerweile hat sich das Gefühl breit gemacht, dass eine Vielzahl von unterschiedlichen Erfahrungen notwendig sind, um eine Veränderung der Einstellung zu bewirken.

Ich möchte in meinem Blog über verschiedene Erfahrungen reflektieren, um auf die Entwicklung meines agilen Mindsets zurück zu blicken. Vielleicht findet sich ja der ein oder andere wieder und somit auch Tipps wie man agiler werden kann.

## Lehrjahre und die ersten Gehversuche

Ich hatte eine Ausbildung mit hierarchischen Strukturen kennengelernt. Die Aufgaben kamen oft vom Chef oder den Ausbildern. Meist war es so, dass ich eine Aufgabe bekommen habe, diese habe ich dann abgearbeitet und das Ergebnis dem Aufgabengeber zur Abnahme vorgelegt. Danach gab es dann die nächste Aufgabe und so weiter. Mit dem schrittweisen Vorgehen war ich erfolgreich. Es hat mich zuverlässig zum gewünschten Ziel geführt.

Als ich meinen ersten Job angefangen habe, versuchte ich dieses Muster beizubehalten. Ich bekam eine Aufgabe, erledigte diese Aufgabe und ließ meinen Chef das Ergebnis prüfen. "Nervst Du mich jetzt ständig wegen jedem kleinen Pups?!" so in etwa der Wortlaut. Stark verunsichert, fing ich also an das gerade Gelernte wieder zu vergessen und ein neues Verhalten zu etablieren. Ich ließ die kleinen Abnahmen der Aufgaben einfach weg. Ich sammelte mehrere Aufgaben und schnürte größere Pakete. Was vorher wenige Stunden waren, wurden dann Tage.

"Hättest Du mir das früher gezeigt, dann hätte ich Dir sagen können, dass Du auf dem Holzweg bist!" musste ich dann sinngemäß vernehmen. Meine Aufgabenpakete waren also schon zu groß geworden. Ich hatte den richtigen Zeitpunkt für die Abnahme beim Aufgabengeber verpasst.

Ich lernte extreme Programming kennen. Dort war ein inkrementelles Vorgehen und regelmäßige Reflektion nebst Abnahme fest verankert. Ich probierte diese Methode in Kundenprojekten aus. "Wieso geht das denn noch nicht?", "Was bekomme ich hier gezeigt?" und "Das ist ja noch ziemlich buggy!" bekam ich dann von den Kunden zu hören. Meine Aufgabenpakete hatten jetzt ein ganz anderes Problem: Sie waren nicht in sich geschlossen, so dass die Funktionalität in kurzer Zeit umsetzbar, testbar und einen Wert für den Kunden darstellte.

## I.N.V.E.S.T. aber wie?

Eine Richtlinie wie [I.N.V.E.S.T.](https://de.wikipedia.org/wiki/INVEST_(Eselsbr%C3%BCcke))  half schon mal weiter, um zu erkennen, ob ein Inkrement gut geschnitten war, oder nicht. Trotzdem blieben weitere Fragen offen: horizontaler Schnitt vs. vertikaler Schnitt? Technischer vs. Fachlicher Schnitt? Das Problem ist meiner Meinung nach die Sichtweise auf die Problemdomäne.

Ein Beispiel: Ein neues Portal soll entwickelt werden. Es wird das erste Inkrement gesucht: Welche Funktion kommt zuerst? Die Startseite? Eine Contentseite? Eine Minisite mit Start und Landingpage mit Kontaktmöglichkeit?  Aber ein fachlicher Schnitt besorgt uns bei diesen Beispielen viel zu große Inkremente. Also doch klassisch eine Art Vorbereitungsphase mit horizontalem Schnitt, die klassischen Schichten, bis die Basis gelegt ist?

In den Beispielen wird für den Kunden ein viel zu großer Wert gleich im ersten Schritt angepeilt. Eine schlichte Startseite mag dem Kunden eigentlich schon zu wenig vorkommen, aber überlegt man welche Tätigkeiten damit verbunden sind, kann das sehr schnell den Rahmen eines 2 Wochen Sprints sprengen:

*   Fachliches Konzept als Wireframes für das Portal erstellen
*   Design Konzept entwickeln und ausarbeiten, so dass die Entwickler damit arbeiten können
*   UI / Theme o.ä. implementieren
*   CMS installieren / konfigurieren
*   Inhalte erzeugen und einstellen

## Warum nicht mit der Fehlerseite anfangen?

Ich hatte mir überlegt, was ist das aller kleinste Inkrement, dass für den Kunden einen Wert hat: Der Kunde möchte im Fehlerfall darüber informiert werden, dass auf dem Server oder mit seiner Anfrage etwas nicht in Ordnung ist. Zugegeben ist der Wert nicht sonderlich groß, aber dafür steckt bereits jede Menge in diesem Inkrement:

Um die Fehlerseite auszuliefern, benötigt es die erste Infrastruktur Komponente: den Webserver. Die Seite wird statisch ausgeliefert, aber erste Grundlagen in der UI können bereits gelegt werden. Sofern man nicht einfachen Text ausgeben möchte, kann man bereits für die Fehlerseite ein Design entwickeln und sich bereits über Farbkonzepte und grundlegenden Aufbau Gedanken machen. Hier als Beispiel die [Fehlerseite von Airbnb](https://www.airbnb.com/500), die aus meiner Sicht ein gutes erstes Inkrement sein könnte.

Ein nächster Schritt könnte sein, die Anbindung an ein CMS mit pflegbarer 404 Seite. Dann eine Startseite mit News, wo über die kommende Site informiert wird. Dann ein paar Landing-Pages mit eingebundenen 3rd Party Services und so weiter und so weiter.

Mir hat es geholfen beim Finden der Inkremente zunächst an die Fehler- oder Sonderfälle zu denken, die sehr spezifisch sind. Diese müssen früher oder später ohnehin implementiert werden. Also warum nicht damit anfangen?! Man kann ähnlich wie bei der test-getriebenen Entwicklung diese spezifischen Funktionen dann Schritt für Schritt erweitern und generalisieren. Der Vorteil ist, dass die viele spezifischen Fälle erstmal einfacher herzustellen sind und gleichzeitig kann man bereits erste Erfahrungen mit der Funktionalität sammeln.

## Das Erbe meiner Ausbildung

Inkrementelles Vorgehen ist seit meiner Ausbildung nicht mehr wegzudenken. Die richtige Größe der Inkremente ist dabei mein Schlüssel zum Erfolg. Die Inkremente sollten so groß sein, dass sie in einem Sprint erledigt werden können. Das schafft Motivation und minimiert das Risiko das Projektziel zu Verfehlen.

Folgende Fragen helfen mir dabei Inkremente kleiner zu bekommen:

*   Warum braucht der Kunde diese Funktion? Was hat der Kunde von der Funktion? Welche Teilfunktionen stecken dahinter?
*   Was wäre der einfachste (Fehler-) Fall? Was passiert im Fehlerfall?
*   Brauchen wir das System XY jetzt schon? Können wir schwer gewichtige Entscheidungen nicht auf später vertagen, bis wir mehr über die Problemdomäne wissen?

Aber selbst heute sind meine Inkremente nicht selten zu groß. Deshalb weiter: Üben, Üben, Üben.