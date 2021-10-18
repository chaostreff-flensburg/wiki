---
title: "Wie benutzte ich das Wiki"
date: 2020-01-26T23:11:13Z
draft: false
tags: ["needtobeupdated"]
categories: ["anleitung"]
---
{{< info name="Hugo Wiki"  contact="soeren" >}}
Das Wiki ist eine [Hugo](https://gohugo.io/) Seite die mit einer [Github Action](https://github.com/chaostreff-flensburg/wiki/actions) gebaut wird und auf Github Pages liegt.

### Vorbereitung Linux / Mac

Clone das Repository von [Github](https://github.com/chaostreff-flensburg/wiki) auf deinen Rechner.

```
git clone git@github.com:chaostreff-flensburg/wiki.git
```

danach kannst du die [Markdown](https://guides.github.com/features/mastering-markdown/) Datein im "content" folder anpassen. Wenn du damit fertig bist pushe die änderungen, die wiki seite wird nach einigen Sekunden automatisch aktualisiert.

### Vorbereitung Windows

*comming soon*

### Eine Seite bearbeiten oder anlegen.

Du kannst im content Ordner eine neue Seite anlegen in dem du eine neue Datei mit der Endung ".md" anlegst. Wichtig ist das du am anfang der Datei folgende zeilen einfügst und bearbeitest

```
---
title: "XXXX"
date: 2020-01-26T23:11:13Z
categories: ["XXXX"]
---
```

Ändere die Werte basierend auf dem titel und der categorie, du kannst eine neue categorie nutzten oder auf der Startseite dir eine der bestehenden wie z.B. "verein" oder "werkzeug" aussuchen. Die Kategorie MUSS klein geschrieben werden.

Unter den zweiten --- kannst du den Inhalt der Seite schreiben, schaue dir am besten anderen Seiten aus der selben Kategorie als Beispiel an.

## Infobox
Die Infobox soll für Profile und Projektseiten genutzt werden. Es handelt sich hierbei um die Box die auf der rechten Seite angezeigt wird.

{{<gist kekskurse 726028597eaac1e3aa91fc92fabd35d6 >}}

Es gibt folgende Parameter

* **name** -> Name der Person oder des Projektes
* **img** -> URL zu einem Bild, komplette url
* **twitter** -> Twitter Name (ohne @ oder http, nur der name) 
* **webpage** -> Webpage Name (ohne http, es wird automatisch auf https weitergeleitet)
* **mail** -> E-Mail adresse
* **instagram** -> Instagram Nutzername (ohne @ oder http)
* **ort** -> Wo es sich im Space befindet (nicht für Personen gedacht)
* **contact** -> Liste von Ansprechpartner, durch ein kommer getrennt (nicht für Personen gedacht)

## Design 

### Ordner Stuktur
Ist dem Layout total egal. Es macht Sinn die Categorien in den Ordner wiederzuspiegeln für schönere URLs und ein einfaches finden der infos im git.

### Menü
Das Menü auf der linken Seite wird automatisch generiert aus allen Categorien (`categories`) die es so gibt. Es ist nicht möglich die Reinfolge zu beineinflussen oder einzelne Categorien nicht anzuzeigen. Es öffnen sich automatisch die Menüpunkte von den Categoriern die dem aktuell angezeigtem Artikel entsprechen.

### Startseite

In cer `config.toml` werdne die linklen beiden Spalten configuriert. Die dritte Spalte beinhaltet alle Categorien die es nicht in die ersten beiden geschaft haben.

