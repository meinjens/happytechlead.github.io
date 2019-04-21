---
layout: post
title: 10 Minutes to go
bigimg: /assets/schneckenrennen_9010600618_bd8d776632.jpg
tags: [become agile]
---

Was kann man alles in 10 Minuten schaffen? Einen Kaffee ziehen, kurz auf Toilette, die Beine vertreten, schnell was klären, gerade mal Mails checken, am Handy spielen, in einer Zeitschrift blättern, zum Automaten und Süßigkeiten kaufen, Kollegen von der Arbeit ablenken, mal eben eine Frage stellen usw. usw. Ich könnte die Liste mit Dingen, die ich erledige, während mein Laptop die Software baut, noch sehr weit ausbauen. Aber welcher Build ist schon in 10 Minuten fertig?

## Feedback Loop

Ich kann mich noch gut an die alten Zeiten erinnern. Den Build-Prozess angeworfen und dann heißt es warten. Nach 45 bis 60 Minuten hatte ich teilweise schon vergessen, welche Änderungen ich alle mit eingebaut oder welche Versionsnummer ich vergeben hatte. Denn ich sitze ja nicht einfach nur rum und warte, sondern beschäftige mich parallel mit anderen Dingen, um die Zeit sinnvoll zu nutzen. Mein Fokus ist aber nicht mehr da.

Ich komme schnell voran, sobald Build und Deployment ebenfalls schnell ablaufen. Die Ablenkungen sinken, wenn ich keine Gelegenheit bekomme, zwischendurch etwas anderes machen zu können. Je kürzer die Feedback Loop, desto besser, auch beim Deployment. Dabei sind mir 10 Minuten schon viel zu lang.

## Das 1x1 für Manager

Ich habe es während meiner Laufbahn noch nicht erlebt, dass sich ein Manager für die Dauer des Build-Prozesses interessiert. Das wundert mich ein wenig, da dort ein hohes Potential für unnütze Zeitfresser verborgen ist. Mal angenommen wir haben ein Team von 5 Entwickler. Angenommen jeder Entwickler benutzt den Build-Prozess etwa 5 mal am Tag. Ein Durchlauf dauert 15 Minuten.

Das ergibt 5 x 5 x 15 Min = 375 Min => 6,25 Std pro Tag => 31,25 Std pro Woche.

D.h. die aufgefressene Zeit kommt fast an die eines Mitarbeiters heran, der sich 75% der Zeit mit nichts anderem beschäftigt. Ich finde das erschreckend unproduktiv. Und ich schätze mal, dass jeder Entwickler den Build mehr als 5 mal pro Tag verwenden möchte.

## Divide and Conquer

Häufig habe ich beobachtet, dass der der Build-Prozess zu Beginn des Projektes entwickelt und danach nie wieder angepasst wird. Er braucht mit fortschreitendem Projekt immer länger. Ich steige also in die Details ein und stelle mir ein paar Fragen:

Wird nur die Änderung gebaut? Wird immer alles gebaut? Ein schneller Build-Prozess baut nur die Änderungen und fügt dann die bestehenden Teile, die bereits gebaut sind einfach nur zusammen. Der Build, der vielleicht initial mal angelegt wurde, sollte dahingehend angepasst werden nur die Änderungen zu bauen.

Welche Tests werden zum Build-Zeitpunkt ausgeführt? Schnelles Stoßgebet, dass es nur Unit-, Komponenten- oder API-basierte Akzeptanztests sind. Alles andere dauert meist viel zu lange und ist besser ausgelagert aufgehoben. Integrations-, Systemtests und alles was in etwa diesen Charakter hat, sind langlaufende Tests, die nicht bei jeden Build mitlaufen müssen, da sie weniger die Funktionalität sondern mehr die Systemkonfiguration testen sollen.

Welche zusätzlichen Codechecks werden ausgeführt? Ich falle gedanklich auf die Knie beim Anblick von Findbugs, Checkstyle und PMD im Build-Prozess. Wieso muss hier alles reglementiert werden? Weil sich sonst keiner dran hält? Damit nur toller Code eingecheckt wird? Ich halte es für schlecht eine "Bremse" in den Regelprozess einzubauen. Ich gehe mal davon aus, dass jeder Entwickler mit dem ich arbeite, selber daran interessiert ist, seine Codequalität angemessen zu gestalten. Deswegen reicht es meines Erachtens aus einen asynchronen Prüfmechanismus zur Hilfe zu nehmen (z.B. SonarQube) und die Ergebnisse in einen CodeReview mit einzuarbeiten.

Was macht der Build-Prozess sonst noch? Alle Mechanismen, die vom Standard abweichen, sind für mich die typischen Smells. Warum? Na, weil es das Meiste in der Welt der Build-Systeme bereits gibt. Viele individuell erweiterte Mechanismen lassen sich durch Standards ablösen. Diese sind dann schneller, besser getestet, fehlerfreier, erweiterbarer, wartungsfreier, mehr Know-How vorhanden usw.

## Stumpfe Arbeit eliminieren, Müll beseitigen, fehleranfällige Dinge automatisieren

Ich habe auch schon oft erlebt, dass zum Bauen der Software viele manuelle Schritte notwendig waren. Klar, dass da auch der ein oder andere Fehler passieren kann. Stumpfe Arbeiten, wie Kopieren von Dateien, Einstellen von Deploymentartefakten etc. lassen sich meist sehr gut automatisieren. Ziel meiner Builds sind meist so wenig manuelle Tätigkeiten wie möglich machen zu müssen.

Mein Idealfall sieht so aus, dass nach dem angenommenen Merge Request die gesamte Build Pipeline bis zum Ende durchläuft und die Software in wenigen Minuten auf dem Server deployed ist.

## Agile Prinzipien

Agil heißt für mich von einem stabilen zustand in einen stabilen Zustand zu wechseln. Bei einer Iterationslänge von 2 Wochen sollte man sich also mit möglichst wenig administrativen Kleinkram aufhalten. Und das was am meisten aufhält ist ein schlechter Buildprozess. Deswegen lohnt sich hier aus meiner Sicht immer zu investieren und zu optimieren.

_Das Bild ist von [Paolo Valdemarin](https://www.flickr.com/photos/paolovalde/) - vielen Dank dafür!_