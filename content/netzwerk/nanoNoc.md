---
title: "NanoNoc"
date: 2020-01-26T23:11:13Z
draft: false
tags: ["foo", "bar"]
categories: ["netzwerk"]
---
{{< info name="NanoNoc" img="/netzwerk/nanonoc.jpeg" contact="fpfle" >}}
### Komponenten

* Edge Router X sfp
* Raspberry pi (Unifi Controller (10.0.0.2))
* Raspberry pi (filesharing)
* TP-Link Pocket (für Wlan uplink)
* Unifi Switch 8 60W POE
* 4x unifi Mesh Ap
* 1x unifi Ac Lite
* 1x Zyxel 24x1G Ethernet 4xSFP+

### Netz

10.0.0.0/16:
 *  Router: 10.0.0.1
 *  Unifi-Controller 10.0.0.2

### Beschreibung

Das miniNoc ist ein kleines Rack, dass im Space als auch auf veranstalltungen ein Kebel und Funknetz bereit stellt. Über den Router können mehrere Uplinks verbunden werden über die dann geloadbalenced werden. 