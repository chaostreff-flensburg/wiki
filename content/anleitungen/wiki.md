---
title: "Wie benutzte ich das Wiki"
date: 2020-01-26T23:11:13Z
draft: false
tags: ["needtobeupdated"]
categories: ["anleitung"]
---

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

