---
layout: post
title: System-Setup mit Ansible
tags: [raspberrypi, pondpi, ansible]
---

Das Setup der Raspberry Pis habe ich nun schon mehrfach durchführen müssen. In meinem letzten Job habe ich ein schönes Tool gefunden, womit ich das Setup reproduzierbar in Code gießen kann: Ansible.

[Ansible](https://www.ansible.com/) ist ein Automatisierungs Tool für IT Infrastrukturen. Mit Hilfe des Tools richte ich das Betriebssystem der beiden Raspberry Pis ein.

![](http://meinjens.de/wp-content/uploads/2018/09/ansible-setup.png)

Setup der Raspberry Pis mit Ansible

Ansible ist in Python implementiert. Deswegen ist Windows als Kontrollmaschine nicht gut geeignet. Auf [Windows 10 lässt sich jedoch Linux als Subsystem](https://docs.microsoft.com/en-us/windows/wsl/install-win10) nutzen.

Das Ansible Projekt liegt im Ordner [_setup_](https://github.com/meinjens/pondpi/tree/master/setup)   
Hier ein kurzer Überblick über das Projekt-Layout des Moduls:

setup  
  +-- callback\_plugins/        (Plugin-Verzeichnis)  
  +-- group\_vars/              (Variablen für Server-Gruppen)  
  +-- host\_vars/               (Variablen für einzelne Server)  
  +-- roles/                   (Verzeichnis für die Ansible Rollen)  
  |   ansible.cfg              (Ansible Einstellungen für das Projekt)  
  |   setup\_base.yml           (Playbook für das Basis Setup aller Pis)  
  |   setup\_controlstation.yml (Playbook zum Setup der Kontrolstation)  
  |   setup\_researchship.yml   (Playbook zum Setup des Bootes)

Mit verschiedenen Rollen werden die Dienste auf den Raspberry Pis installiert und konfiguriert, wie z.B. einen DHCP-Server. Folgende Rollen nutzen wir für die Installation der beiden Pis:

## Base Rolle

Die Base Rolle führt Basiseinstellungen auf den Raspberry Pis durch, wie z.B. Updates, Hardware Setup.

ansible-playbook setup\_base.yml

## Accesspoint Rolle

Diese Rolle installiert alle Dienste, die zum Betrieb des Pis als Accesspoint notwendig sind. Für die WLAN Verbindungen nutzen wir den Dienst [HostAPD](https://packages.debian.org/de/stretch/hostapd). Für den DHCP-Server nutzen wir [DNSmasq](https://packages.debian.org/stretch/dnsmasq).

Zur Installation oder Wartung wird lediglich das entsprechende Playbook ausgeführt. Beispiel:

ansible-playbook setup\_controlstation.yml

## Weitere Schritte

Die nächsten Rollen, die ich implementiere, installieren die Test-Tools, nginx, Flask Server usw. Die Rollen findet ihr ebenfalls im [Github-Repository vom PondPi](https://github.com/meinjens/pondpi/tree/master/setup).