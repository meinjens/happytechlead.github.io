---
layout: post
title: Schlechter Code!? Na und?! Funktioniert doch!
tags: [clean code]
---

"Schlechter Code? Na und? Funktioniert doch!" Solche oder ähnliche Aussagen höre ich leider sehr oft. Ich vergleiche es oft mit einigen Schreibtischen, die mir während meinen Besuchen in Firmen auffallen: Verdörrte Pflanzen, Stapel von Papier und Ordner, Essensreste, leere Gläser, Cola-Flaschen und ähnliches. Leider sieht es im Code dort genauso oder ähnlich aus. Die Kollegen lassen sich meist nicht überreden ihren Saustall zu beseitigen. Macht nichts? "Sauber machen wir dann später, wenn wir fertig sind und dann noch Zeit haben."

Vor etwa zwei Jahren begann ein großes Unternehmen ein Softwareprojekt. Zunächst wurde die sogenannte "Architektur" festgelegt: Liferay, JSF, Spring, Weblogic und DB2. Anschließend verpflichtete man mehrere Framework-Spezialisten und startete mit der Entwicklung. Die ersten Prototypen funktionierten hervorragend. Nach etwa einem Jahr waren erste Teile der Anwendung fertig. Also wurde das Projekt fortgesetzt. Nach zwei Jahren wollte man dann so langsam zum Abschluß kommen. Aber immer wieder gab es Probleme. Die Anwendung war nicht schnell genug. Fehler in der Anwendung führten immer wieder zu Verzögerungen. Und letztendlich stand das ganze Projekt auf der Kippe.

Dies ist nur ein Beispiel von vielen Projekten, die ich miterlebt habe. Die Gründe, die für das Scheitern ermittelt worden sind, waren dann häufig:

*   das Management war nicht ausreichend
*   die Anforderungen haben sich ständig geändert
*   die Aufwandsschätzungen waren nicht zutreffend
*   die Prozesse haben nicht funktioniert

Aber sind das die wirklichen Gründe? Oder sind das nur die Auswirkungen, die man am Ende beobachtet, wenn das Kind bereits in den Brunnen gefallen ist?

Wenn es soweit gekommen ist, dass die offensichtlichen Auswirkungen eingetreten sind, werden oft die Berater und Experten ins Feld geschickt. Meist bleibt für sie nichts anderes übrig als den Tot des Projektes festzustellen. Die Obduktion der Projekte ergibt dann die wahren Todesursachen:

*   Niedrige oder keine Testabdeckung und / oder hohen manuellen Testaufwand
*   Zyklische Abhängigkeiten zwischen Modulen, Paketen, Klassen
*   Hohe Anzahl an Findings von Schwächen (Mit Hilfe von PMD, Findbugs, Checkstyle-Regeln)

Nun das alles kann man leicht messen. Vielleicht wurde es auch gemessen. Aber trotzdem werden gerne die oben genannten Gründe als Ursache für das gescheiterte Projekt genannt. Aber ich denke so lange können wir Entwickler uns nicht mehr in die Ausreden flüchten. Mal ehrlich:

> Der schlechte Code ist der Grund, warum viele solcher Projekte scheitern!

Natürlich ist das nicht der einzige Grund, aber aus meiner Sicht der Maßgebende. Warum ist der Code denn schlecht? Wie erkenne ich schlechten Code? Wie entsteht schlechter Code?

Der Code ist schlecht, wenn

*   er nur schwer lesbar und damit schlecht wartbar ist
*   durch Änderungen andere Funktionalitäten beeinflusst und sogar zerstört werden
*   die Implementierung so starr ist, dass sie eigentlich nicht mehr Software sondern schon eher Hardware genannt werden muss
*   die gleiche Funktionalität auf unterschiedliche Wege umgesetzt wird, anstatt ein vernünftiges OOD zu verwenden
*   die einfachen Wege zum Ziel verbaut sind und durch umständliche Mechanismen ersetzt wurden

## Wie erkenne ich schlechten Code?

Die Frage sollte man sich bereits früh im Projekt stellen. Denn wenn die Zeit erst einmal verbraucht ist, ist auch meist das Budget schon verbraucht. Leider kann man schlechten Code noch nicht direkt messen. Dazu muss man einen Blick in den Code werfen oder sogar mit ihm arbeiten. Alles was man direkt messen kann, ist jedoch ein gutes Indiz und sollte beim ersten Auftreten auf keinen Fall missachtet werden.

Man kann schlechten Code erkennen, wenn man darüber spricht. Oftmals hilft es schon, dass man den geschriebenen Code jemandem erklärt. Guter Code ist so einfach, dass selbst der Kunde die Funktionsweise des Codes versteht.

Ein anderer Weg kann sein, dass man den Code einem Kollegen gibt. Dieser bekommt die Aufgabe eine neue Funktion zu integrieren. Dabei sollte man über die verschiedenen Wege bzw. Probleme sprechen und gemeinsam Alternativen erarbeiten.

## Und wie entsteht schlechter Code?

Manchmal schon mit der zweiten Zeile Code. Zusammenfassend: Ich denke, dass wir Software-Entwickler noch nicht professionell genug verhalten.

*   Unsere Entwicklungszyklen sind viel zu lang:  
    Wir sitzen meist Stunden oder Tage an einem Problem ohne eine wirkliche Erfolgskontrolle.
*   Wir stürzen uns auf Frameworks:  
    In der Hoffnung, dass Sie uns das Denken und Arbeiten abnehmen, benutzen wir sie wo wir nur können ohne dabei den Sinn und Zweck genau zu hinterfragen.
*   Wir lassen Tests einfach unter den Tisch fallen:  
    Häufig bekomme ich die Ausrede zu hören: "Es war keine Zeit!" oder "Das kann man ja so gar nicht testen!"
*   Wir abstrahieren zu wenig in unserem Code:  
    Wir verlieren uns meistens in Details und verwenden wenig oder gar keine Zeit um uns über eine geeignete Abstraktion Gedanken zu machen. Die Lösungen sind dann genauso detailverliebt aber haben nicht mehr den Blick für das Wesentliche.
*   Anstatt wiederkehrende Aufgaben zu automatisieren, machen wir sie immer und immer und immer wieder zu Fuß:  
    Das erinnert an einen Hund, der ständig seinem Schwanz nachjagt oder einem Hamster in seinem Laufrad. Irgendwann müssen wir mal aus dem Kreis ausbrechen. Es spart sehr viel Zeit.
*   Wir arbeiten in agilen Teams und dennoch alleine:  
    Trotz Pair Programming fällt es uns dennoch schwer, dass wir gemeinsam vor einem Rechner an einem Problem arbeiten. Aber das hilft uns ungemein einen anderen Blickwinkel für das Problem zu bekommen.

Nun das sind alles keine neuen Erkenntnisse. Alles kalter Kaffee, den wir bereits schon tausend mal auf irgendwelchen Blogs, Konferenzen oder anderen Veranstaltungen gehört haben. Richtig!

Also warum fangen wir nicht endlich an, uns professionell zu verhalten?! Zeigt mal ein bisschen mehr Disziplin! Geht doch mal den langen Weg und nicht immer nur die Abkürzung! Habt ein wenig Rückrat und macht die Sachen gleich richtig - und nicht 10 Mal falsch! Die Theorie funktioniert auch tatsächlich in der Praxis - man muss sie nur mal konsequent durchziehen!

## Es liegt allein an Euch!

Robert C. Martin kann Euch helfen. Er sagt Euch zum Beispiel, wann ihr aufräumen sollt:

*   [Architecture - The Lost Years (Robert C. Martin)](http://youtu.be/WpkDN78P884)
*   [Agile Software Development (Robert C. Martin)](http://www.amazon.de/dp/0132760584)
*   [The Clean Coder (Robert C. Martin)](http://www.amazon.de/dp/0137081073)
*   [Clean Code (Robert C. Martin)](http://www.amazon.de/dp/0132350882)
*   [www.cleancoders.com (Robert C. Martin)](http://www.cleancoders.com/)