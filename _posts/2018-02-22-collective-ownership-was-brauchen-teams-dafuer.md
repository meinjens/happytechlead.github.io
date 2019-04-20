---
layout: post
title: Collective Ownership - Was brauchen Teams dafür?
tags: [tdd, test driven development]
comments: true
---

<p>Collective Ownership steht für gemeinsam die Eigentümerschaft für die Software übernehmen. Ich habe mich schon häufig gefragt, wie man eine gemeinsame Verantwortlichkeit für etwas etabliert. Im Rahmen einer Collective Ownership für ein Softwareprodukt sollte dies doch schön greifbar für alle Kollegen sein!? Dennoch habe ich festgestellt, dass es auf ähnliche Probleme heraus läuft, wie gemeinsam die Büro-Küche sauber zu halten und sich dafür verantwortlich zu füllen.<!--more--></p>
<h2>Collective Ownership</h2>
<p>Dies beschreibt aus meiner Sicht die Möglichkeit, dass jeder aus dem Team jeden Code und sogar das Design des Systems verändern kann. Alle Änderungen fließen wieder zurück ins Team. Es gibt keinen Mastermind / Chefarchitekt / Lead Developer, der irgendwelche Änderungen erst absegnen muss. Das gesamte Team dient als Architekturboard und diskutiert Änderungen im Systemdesign.</p>
<p>Aber das geht noch weiter. Jeder fühlt sich für den Code bzw. das Systemdesign verantwortlich. Wird eine Schwachstelle entdeckt, kümmert sich derjenige um die Behebung im gesamten System. Jeder hat das Interesse, dass der Code täglich verbessert wird, dass er allen gemeinsam verabredeten Qualitätsstandards entspricht. Jeder hilft dem anderen den Code zu verstehen und Fragen zu klären.</p>
<p>Was braucht also ein Team, damit es all das tun kann?</p>
<h2>Gemeinsames Qualitätsverständnis</h2>
<p>Das Qualitätsverständnis ist bei jedem Menschen unterschiedlich. So habe ich bei meinen Projekten Kollegen erlebt, dass das Qualitätsverständnis von "läuft" bis hin zu "darf noch nicht mal ein Warning im SonarQube" reicht. Ich glaube, das hat mit den bereits gemachten Erfahrungen und eigenen Ansprüchen zu tun, die jeder Entwickler an sich selbst stellt. In Teams halte ich es deshalb für enorm wichtig, ein gemeinsames Qualitätsverständnis zu erarbeiten und immer weiter zu verfeinern. Nicht selten bleiben die Qualitätsansprüche ein Streitpunkt, eben weil die Vorstellungen weit auseinander gehen.</p>
<p>Zum gemeinsamen Qualitätsverständnis zähle ich:</p>
<ul>
<li>Qualitätsziele und -szenarien</li>
<li>Coding Conventions</li>
<li>Typische Patterns in der Software</li>
<li>Festhalten von Design Entscheidungen</li>
</ul>
<h2>Gemeinsames Architekturverständnis</h2>
<p>Damit die Zielrichtung der Architektur des Systems klar und deutlich ist, müssen die Qualitätsziele und -szenarien im Team bekannt sein. Sie schaffen die Basis für die gemeinsame Arbeit und die Architektur des Systems. Aus meiner Sicht reicht es dabei nicht aus einfach nur die grobe Idee (vgl. Kapitel <a href="http://docs.arc42.org/section-4/" target="_blank" rel="noopener">Solution Strategy im arc42</a>) der Architektur im Team zu verbreiten. Dazu gehören auch die Feinheiten (vgl. Kapitel <a href="http://docs.arc42.org/section-8/" target="_blank" rel="noopener">Übergreifende Konzepte im arc42</a>).</p>
<h2>Gemeinsame Architekturentwicklung</h2>
<p>Die Architektur kennen ist der erste Schritt. Die Architektur bzw. das System Design weiter zu entwickeln, folgt gleich danach. Dazu gehört aus meiner Sicht, dass man sich intensiv mit den übrigen Bereichen des arc42 auseinander setzt. Insbesondere ist es notwendig sich in den verschiedenen Sichten der Architektur zu orientieren. Das ist die Voraussetzung dafür, dass man in der Lage ist, die Architektur sinnvoll weiter zu entwickeln.</p>
<p>Die eigentliche Weiterentwicklung findet dann wieder im Team statt. Jemand aus dem Team zeigt Problem ein Problem auf, verschiedene mögliche Lösungen werden gemeinsam diskutiert und am Ende entscheidet sich das Team für eine Lösung. Die Entscheidung und Lösung wird wieder im gemeinsamen Architekturdokument festgehalten und die Lösung dann umgesetzt.</p>
<h2>Gleicher Informationsstand</h2>
<p>Eine solche offene Architekturentwicklungskultur setzt voraus, dass allen die gleichen Informationen und Informationsquellen zur Verfügung stehen. Informationen dürfen nicht nur einzelnen wenigen zur Verfügung gestellt werden, sondern müssen im Team geteilt werden.</p>
<h2>Wer hat hier den Hut auf?</h2>
<p>"Ja, aber ich will einen zentralen Ansprechpartner für die Architektur." - Ja den kann das Team wählen. Es sollte jemand sein, der die Architektur gut kommunizieren kann. Der Ansprechpartner kann dazu dienen, sämtliche Aspekte der Architektur zu erläutern und zu erklären. Er kann dazu dienen neue Anforderungen an die Architektur aufzunehmen. Er sollte jedoch nicht vorschnell Entscheidungen treffen, die eigentlich besser im Team getroffen werden können.</p>
<p>Wer hat hier den Hut auf? Es ist niemand explizit für Codequalität, Architektur etc. verantwortlich. Niemand besitzt das offizielle Mandat: "Dein expliziter Auftrag ist es, dass Du Dich um .... kümmerst." Was passiert nun in einem Team mit gemeinsamer Verantwortlichkeit? Ich habe die Erfahrung gemacht, dass sich dann die Kollegen Verantwortung übernehmen, die ohnehin gerne Verantwortung übernehmen. D.h. solche Mitarbeiter kümmern sich um das Thema. Sie treiben das Thema voran und bringen das Thema bei den Kollegen in Fokus.</p>
<p>Sind die Kollegen, die sich kümmern immer die Besten für den Job? Manchmal passt es und manchmal auch nicht. Wichtig ist es meines Erachtens, dass die Kollegen, die sich kümmern nicht von den anderen Kollegen im Regen stehen gelassen, sondern unterstützt werden. Und die Kollegen, die sich kümmern, sollten immer wieder ihr Team mit einbeziehen. Auch wenn es Kümmerer gibt bleibt es eine Teamaufgabe.</p>
<h2>Disziplin und Durchhaltevermögen</h2>
<p>Die Arbeit an einem gemeinsamen Regelwerk oder einer gemeinsamen Dokumentation liegt vielen Teams überhaupt nicht. Jedenfalls habe ich noch kein Team kennengelernt, dass mit einem Architekturdokument so konsequent gearbeitet hat, wie ich mir das idealerweise vorstelle. Vielleicht liegt es daran, dass die Dokumentation noch zuweit weg vom Code liegt. Vielleicht ist das Verständnis dafür noch zu gering.</p>
<p>Ich werde zukünftig ein paar andere Werkzeuge ausprobieren (z.B. verteilte ASCIIdoc Files um die Dokumentationen nah an den Code zu bekommen).</p>
<h2>Agile Prinzipien</h2>
<p>"Self organizing teams" und "Technical excellence" sind für mich die beiden Prinzipien, die am besten zu der Praktik Collective Ownership passen.</p>