---
layout: post
title: Datenerfassung mit dem TICK-Stack
bigimg: /assets/raspberry_pi_16505411300_96348fe980.jpg
tags: [raspberrypi, pondpi]
---

Eigentlich müsste es RIG Stack heißen. R steht für den Raspberry Pi, I für InfluxDB und G für Grafana. Aber gerade als ich meine Services mal wieder aktualisieren wollte, stieß ich auf den TICK Stack von Influxdata: T = Telegraf für das Sammeln von Daten von verschiedenen Datenquellen, I = InfluxDB für das schnelle schreiben von Daten, C = Chronograf zum Visualisieren der Daten und K = Kapacitor zum Entdecken von Anomalien in den Daten.

## Überblick

Das Gesamtsystem besteht aus mehreren Raspberry Pis, die die Daten erfassen und einem zentralen Server, der die Daten weiterverarbeitet. Die Raspberry Pis senden ihre Daten an einen zentralen Message Broker ([Mosquitto](http://mosquitto.org/)) [MQTT Protokoll](http://mqtt.org/). Telegraf abonniert die Nachrichten der Raspberry Pis und schreibt diese in die InfluxDB. Die Chronograf stellt die Daten in Diagrammen dar und der Kapacitor kann die Daten analysieren und ggf. Benachrichtigungen versenden.

## Raspberry Pi

Die [Erfassung der Daten ist in Python](https://github.com/meinjens/home-control-pi/blob/master/monitor/mqtt_client.py) programmiert und wird als systemd Service automatisch mit dem Start des Servers mitgestartet. In regelmäßigen Abständen werden die Daten ausgelesen und in strukturierte Topics geschrieben. Die Struktur ist wie folgt:

```
/<Auf welchem Raspberry Pi wird gemessen?>/sensors/<Welches Bauteil misst?>/<Was wird gemessen?>/
```

Wie ihr in dem Script sehen könnt, nehmen wir auch Messdaten auf, die der Raspberry Pi von Haus aus bereitstellt, wie z.B. CPU Temperatur, Stärke des WLAN Signals etc.. Ihr braucht also nicht unbedingt erst noch Sensoren einzubinden, damit ihr das ausprobieren könnt.

## Mosquitto

Der MQTT Broker Mosquitto ist relativ einfach zu [installieren und zu konfigurieren](http://mosquitto.org/man/mosquitto-conf-5.html). Der Dienst läuft auf einem zentralen Server. Ich habe das Speichern der Nachrichten auf der Platte aktiviert (persistence = true), aber zukünftig möchte ich darauf eher verzichten.

## Telegraf

Früher haben wir einen eigenen Subscriber Dienst in Python geschrieben, der die Daten dann in die InfluxDB schreibt. Dafür gibt es jetzt [Telegraf von Influxdata](https://influxdata.com/time-series-platform/telegraf/). Verschiedene Ein- und Ausgabe-Quellen können hier angebunden werden. Ich nutze den MQTT Consumer, um die Daten aus den Topics zu lesen und in die InfluxDB zu schreiben. Dazu habe ich dem Raspberry Pi das [Influx Line Protokoll](https://docs.influxdata.com/influxdb/v0.12/write_protocols/line/) beigebracht.

Hier die Konfiguration für den Consumer:

```bash

\[\[inputs.mqtt\_consumer\]\]  
servers = \["localhost:1883"\]  
qos = 0  
topics = \[  
"/#",  
\]  
metric\_buffer = 100000  
persistent\_session = true  
client\_id = "eigene client id vergeben"  
data\_format = "influx"

```

Das Zusammenspiel von Raspberry Pi, Mosquitto und Telegraf lässt sich im Debug Modus von Mosquitto gut überwachen können. Darin ließen sich alle Nachrichten und Verbindungen gut einsehen.

## InfluxDB

Die [InfluxDB](https://influxdata.com/time-series-platform/influxdb/) habe ich mit den Standard Optionen installiert und habe die Konfiguration nicht sonderlich eingeschränkt.

## Chronograf

Die Installation ist denkbar einfach. Im Gegensatz zu Grafana ist die Oberfläche von [Chronograf](https://influxdata.com/time-series-platform/chronograf/) eher rudimentär und mit weniger Funktionsumfang. Es lassen sich mit Hilfe der InfluxQL die zu visualisierenden Daten abfragen und darstellen. Mehr oder weniger war es das aber auch schon.

[![Chronograf-Dashboard](/assets/Chronograf-Dashboard-300x180.png)](/assets/Chronograf-Dashboard.png)

Im Vergleich zu Grafana muss es meiner Meinung nach noch ordentlich zulegen. Grafana hängt jedoch mit seiner InfluxDB Unterstützung etwas hinterher. Die Version 2.6 unterstützt nur InfluxDB 0.9 und die letzte Beta nur InfluxDB 0.11. Das ist also einer der Vorteile des TICK Stack - die Versionen passen zusammen.

## Kapacitor

Mit dem [Kapacitor](https://influxdata.com/time-series-platform/kapacitor/) möchte ich ungewöhnlich hohe Temperaturen der CPU melden. Da beide Raspberry Pis zwar in einem wetterfesten Gehäuse verbaut sind, sind sie trotzdem der Sonne ausgesetzt.

Die Installation war wieder denkbar einfach. Die Konfiguration etwas schwieriger. Die InfluxDB muss in der kapacitor.conf korrekt angegeben werden. Dann kann man beginnen: Task konfigurieren, Demo Daten aufnehmen, Task mit den Daten testen und nach dem Feintuning den Task aktivieren. Ich bin im wesentlichen [dem Tutorial](https://docs.influxdata.com/kapacitor/v0.12/introduction/getting_started/) gefolgt und habe nur den Task auf meine Bedürfnisse angepasst.

Der Task sieht bei mir so aus:  
```
stream  
|from().database('telegraf').retentionPolicy('default')  
.measurement('cpu\_temperature')  
.groupBy('host')  
|alert()  
.id('{{ .Name }}/{{ index .Tags "host" }}')  
.message('{{ index .Tags "host" }} hat {{ .Level }} Level: Die Temperatur beträgt {{ index .Fields "value" }}°C.')  
.crit(lambda: "value" > 60)  
.log('/tmp/alerts.log')  
.slack()  
```

Übersetzt bedeutet das Script: Schau dir das Messreihe cpu\_temperature an und gruppiere das nach den Hosts. Sobald der Wert die 70 Grad überschreitet, schreibe dies in ein Log und benachrichtige mich über Slack darüber. Damit die Benachrichtung über Slack funktioniert muss man einen Webhook in Slack konfigurieren und dies in die kapacitor.conf eintragen.

## Das geht!

Geschafft! Sobald die Temperatur den kritischen Wert übersteigt, meldet sich der kapacitor mit einer Nachricht im Chat!

[![slack-message](/assets/slack-message-300x53.png)](/assets/slack-message.png)