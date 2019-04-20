---
layout: post
title: SSL Zertfikate prüfen
tags: [devops]
---

Zur Installation von neuen SSL-Zertifikaten bleibt es nicht aus, die korrekte Installation auch zu prüfen. Meiner Ansicht ist der beste Weg direkt mit SSL das Zertifkat zu validieren. Dabei werden auch jede Menge Informationen zum Zertifikat ausgegeben.

openssl s\_client -connect <domain:443>