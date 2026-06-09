---
title: "Harry Plotter (SK-720T)"
date: 2026-06-09T12:00:00+02:00
draft: false
categories: ["werkzeug"]
tags: ["internal"]
---

## Harry Plotter (SK-720T)

Zum Schneiden von designs aus entsprechender Folie mit einer maximalen Breite von 28 Zoll.

## Einrichtung und Verwendung

Um den Plotter zu bedienen haben wir im Moment mehr oder weniger zwei Möglichkeiten. Es gibt eine Software vom Hersteller, welche mit einem beigelegten Lizenzschlüssel genutzt werden kann. Dieser Schlüssel ist im Moment aber nicht vorhanden. Die Alternative ist das FOSS Programm [Inkcut](https://codelv.com/projects/inkcut/) mit welchem man SVG Dokumente ohne Große vorbereitung plotten kann.  

In der Werkstatt gibt es einen blauen Windows Laptop auf dem Inkcut und der Plotter eingerichtet sind und verwendet werden können.

### Einrichtung unter Windows

Um den Plotter unter Windows verwenden zu können, muss er als Drucker eingerichtet werden:

1. COM-Port des Druckers herausfinden.
1. In der Druckerliste unter Bluetooth und Geräte "Gerät hinzufügen"
1. "Fügen Sie ein neues Gerät manuell hinzu"
1. "Lokalen Drucker oder Netzwerkdrucker mit manuellen Einstellungen hinzufügen"
1. "Vorhandenen Anschluss verwenden" -> den entsprechenden COM-Port auswählen
1. Hersteller: "Generic", Drucker: "Generic / Text Only"
1. Eindeutigen Namen vergeben, Beispiel: "Harry Plotter"
1. Drucker nicht Freigeben
1. keine Testseite Drucken
1. Hier fertig

in Inkcut

1. ToDo

### Einrichtung unter Linux

Noch nicht vorgenommen.

### Einrichtung unter Mac

Noch nicht vorgenommen.

### Vor dem Schnitt

1. Schneidmaterial einlegen und festspannen.
1. Einmalig per Selbsttest den richtigen Schneiddruck für das Material finden.
1. Einmal "Leave"-Taste drücken, Schneidkopf an gewollte Ursprungsposition bewegen, "Origin"-Taste zum setzen den Ursprungs drücken.
1. SVG in Inkcut laden und positionieren
1. per "STRG+P" den Auftrag an den Plotter senden.
