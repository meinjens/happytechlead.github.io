---
layout: post
title: SSL Zertfikate prüfen
tags: [devops, linux tipps]
---

Zur Installation von neuen SSL-Zertifikaten bleibt es nicht aus, die korrekte Installation auch zu prüfen. Meiner Ansicht ist der beste Weg direkt mit SSL das Zertifkat zu validieren. Dabei werden auch jede Menge Informationen zum Zertifikat ausgegeben.

```bash
openssl s_client -connect <domain:443>
```

_Update (21.04.2019)_

Diverse Tools im Internet bieten die Möglichkeit die installierten SSL Zertifikate zu prüfen. Sie helfen dabei die Server sicher zu konfigurieren und Mechanismen for [OCSP Stapling](https://de.wikipedia.org/wiki/Online_Certificate_Status_Protocol_stapling) zu prüfen.

* [https://www.ssllabs.com/ssltest/](https://www.ssllabs.com/ssltest/)
* [https://github.com/nabla-c0d3/sslyze](https://github.com/nabla-c0d3/sslyze)
* [https://github.com/ssllabs/research/wiki/Assessment-Tools](https://github.com/ssllabs/research/wiki/Assessment-Tools)