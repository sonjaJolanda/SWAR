---
marp: true
theme: default
paginate: true
footer: Übung Software-Architektur 2 -  (Prof. Schneider), Gruppe 2
# Keine Nummer und Fußzeile auf der ersten Folie:
_paginate: false
_footer: " "
---

# Übung 3, Architektur-Treiber

Team 2: Gergana Germanova, Daorsa Hasani, Sonja Klein 

---

## Geschäftsziele

- Effiziente Kommunikation zwischen Bediensteten 
- Automatisierung von Berichterstellung 
- Genauen und automaitisierten Austausch von Wegbeschreibungen 
- Sicherheit vor unbefugten Dritten 
- Export von der App ins EU-Ausland 
  
---

## Rahmenbedingungen 

- Übereinstimmung mit den Gesetzen und Richtlinien für den Öffentlichen Dienst
- Vorgaben vom Auftraggeber 

---

## Wichtige funktionale Anforderungen 1

- Als *Mitarbeitender in der Polizeistelle*, möchte ich *einzelne Bilder auf Twittter posten können*, damit *ich der Öffentlichkeit effizienter Informationen bereitstellen kann*
- Als *Bediensteter*, möchte ich *selektierte Photos und Nachrichten exportieren können*, damit *ich sie leicht in Polizeiberichte importieren kann*.
- Als *Bediensteter*, möchte ich *dass nach zwei Jahren alle archivierte Daten gelöscht werden*, damit *ich keine unnötige Daten auf mein Messenger haben*.

---

## Wichtige funktionale Anforderungen 2

- Als *Bediensteter*, möchte ich *dass niemand Unberechtigtes meine Nachrichten sehen kann*, damit *ich Informationen austauschen kann und trotzdem meine gesetzlichen Anforderungen einhalte*.
- Als *Bedienstete*, möchte ich *die Möglichkeit haben Nachrichten zu verschicken und zu bekommen*, damit *ich mit anderen kommunizieren kann*.

---

## Qualitätsattribute
### zuverlässige Zustellung von Text-Nachrichten innerhalb von 2ms (Performanz - 1) 
- Umgebung:App wird benutzt von verschiedenen Usern, welche Nachrichten austauschen 
  - Useranzahl > 1000
- Stimulus: User 1 sendet eine Nachricht an User 2 
  - gesendete Nachricht < 5Kb
- Antwort: User 2 erhält die Nachricht auf dem Chatbereich innerhalb t
  - t <= 2ms

---

## Qualitätsattribute
### zuverlässige Zustellung von Mediendateien innerhalb von 1m (Performanz - 2) 
- Umgebung:App wird benutzt von verschiedenen Usern, welche Nachrichten austauschen 
  - Useranzahl > 1000
- Stimulus: User 1 sendet eine Mediendatei (Photo, Video, Sprachnachricht) an User 2 
  - gesendete Nachricht < 3Mb
- Antwort: User 2 erhält die Mediendatei auf dem Chatbereich innerhalb t
  - t <= 1 m

---

## Qualitätsattribute
### zuverlässige Zustellung eines Standortes innerhalb von 1m (Zuverlässigkeit - 3) 
- Umgebung:User 1 befindet sich in einem ländlichen Gebiet. Die verfügbare Bandbreitenverbindung ist auf UMTS-HSPA beschränkt.
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s
- Stimulus: User 1 sendet Standort an User 2 
  - gesendete Standortnachricht < 3Mb
- Antwort: User 2 erhält den Standort auf dem Chatbereich innerhalb t
  - t <= 1 m

---

## Qualitätsattribute
### zuverlässige Wegbeschreibung zu einem empfangenem Standort ohne Fehlleitung (Zuverlässigkeit - 4) 
- Umgebung:User 1 befindet sich in einem ländlichen Gebiet. Die verfügbare Bandbreitenverbindung ist auf UMTS-HSPA beschränkt.
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s
- Stimulus: User 1 möchte zu einem empfangenen Standort geleitet werden
  - empfangener Standort hat eine Genauigkeit von einem Radius < 30m 
- Antwort: User 2 erhält die Wegbeschreibung in einem seperaten Fenster der Applikation
  - jede Wegbeschreibung führt zum Ziel (empfangener Standort) 

---

## Qualitätsattribute
### effizienteste Wegbeschreibung zu einem empfangenem Standort (Effizienz - 5) 
- Umgebung:User 1 befindet sich in einem ländlichen Gebiet. Die verfügbare Bandbreitenverbindung ist auf UMTS-HSPA beschränkt.
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s
- Stimulus: User 1 möchte zu einem empfangenen Standort geleitet werden
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s
- Antwort: User 2 erhält die kürzester Weg-Wegbeschreibung in einem seperaten Fenster der Applikation
  - es wird immer die im-Moment-kürzester-Weg-Wegbeschreibung von allen Alternativen angezeigt

---

## Qualitätsattribute
### zuverlässige Zustellung von Standort innerhalb von 1m (Zuverlässigkeit - 6) 
- Umgebung:User 1 befindet sich in einem ländlichen Gebie. Die verfügbare Bandbreitenverbindung ist auf UMTS-HSPA beschränkt.
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s
- Stimulus: User 1 sendet eine MedienDatei(Photo, Video, Sprachnachricht) an User 2 
  - gesendete Nachricht < 3Mb
- Antwort: User 2 erhält die Nachricht auf dem Chatbereich innerhalb t
  - t <= 1 m

---

## Qualitätsattribute
### Anzeigen von Online-Offline Informationen innerhalb von 1sek (Performanz - 7) 
- Umgebung: User 1 hat die Applikation mit dem Chatbereich des Users 2 geöffnet
  - Useranzahl > 1000
- Stimulus: User 2 öffnet die Applikation und wechselt somit von 'Offline' zu 'Online'. 
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s
- Antwort: User 1 sieht den Aktuellen Zustand innerhalb t
  - t <= 1sek

---

## Qualitätsattribute
### Medien und Nachrichten werden innerhalb von 1sek exportiert (Performanz - 8) 
- Umgebung: User 1 hat die Applikation mit dem Chatbereich des Users 2 und einer darin enthaltenen Mediendatei geöffnet
  - Useranzahl > 1000
- Stimulus: User 1 möchte diese Mediendatei exportieren um sie in einen Polizeibericht hinzuzufügen
  - gesendete Mediendatei < 3Mb
- Antwort: User 1 erhält die exportierte Datei innerhalb t
  - t <= 1sek

---

## Qualitätsattribute
### generierte Informationen werden automatisch archiviert (Datensicherheit - 9) 
- Umgebung: User 1 hat die Applikation und den Chatbereich mit User 2 geöffnet 
  - Useranzahl > 1000 
- Stimulus: User 1 sendet eine Nachricht an User 2
  - gesendete Nachricht < 5kb
- Antwort: Die neu generierten Informationen werden in einem Archiv gespeichert innerhalb t
  - t <= 1min

---

## Qualitätsattribute
### Archivierte Informationen werden nach 2 Jahren automatisch gelöscht (Datensicherheit - 10) 
- Umgebung: Die Daten von User 1 sind archiviert
  - Archivgröße > 20 GB 
- Stimulus: Daten des User 1 werden älter als 2 Jahre
  - Nachricht > 2 Jahre
- Antwort: Die Daten des User 1, die die 2 Jahre Grenze überschritten haben, werden innerhalb t gelöscht
  - t <= 1min

---

## Qualitätsattribute
### Mediendateien werden innerhalb von 20 sek auf Twitter gepostet (Performanz - 11) 
- Umgebung: User 1 hat den Chatbereich mit User 2 und eine darin enthaltene Mediendatei geöffnet 
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s, Useranzahl > 1000
- Stimulus: User 1 möchte diese Mediendatei auf Twitter teilen
  - gesendete Mediennachricht < 3Mb
- Antwort: Die Mediendatei wird innerhalb t auf Twitter veröffentlicht
  - t <= 20 sek

---

## Qualitätsattribute
### Archivierte Informationen werden vor fremden Dritten geschützt gespeichert (Sicherheit - 12) 
- Umgebung: Die Daten von User 1 sind archiviert
  - Archivgröße > 20 GB 
- Stimulus: Eine fremde dritte Person möchte die Daten von User 1 einsehen 
  - Eine Brute-Force Attack wird auf das Archiv ausgeübt
- Antwort: Die Daten des User 1 sind verschlüsselt und passwortgeschützt gespeichert, sodass ein fremder Dritter keinen Zugriff hat. Außerdem werden aktuelle Sicherheitsstandards eingehalten. 
  - Alle empfohlenen Sicherheitsstandards des BSI sind eingehalten

---

## Qualitätsattribute
### Eine Gruppe wird erstellt und alle eingeladenen User werden innerhalb 1sek benachrichtigt (Performanz - 13) 
- Umgebung: User 1 hat den Chatbereich der Applikation offen
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s, Useranzahl > 1000
- Stimulus: User 1 erstellt eine neue Gruppe mit den Teilnehmern User 1, User 2 und User 3 
  - Gruppengröße > 2 User
- Antwort: User 2 und User 3 werden innerhalb t benachrichtigt, dass sie nun Teil der neu erstellten Gruppe sind
  - t <= 1 sek

---

## Qualitätsattribute
### Eine Gruppe wird erstellt und alle eingeladenen User können die Inhalte des Chats innerhalb 1sek sehen (Zuverlässigkeit - 14) 
- Umgebung: User 1 und User 2 ist Teil der Gruppe A und hat den Chatbereich dieser Gruppe geöffnet
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s, Useranzahl der Gruppe > 1000
- Stimulus: User 1 sendet eine Nachricht in die Gruppe A
  - gesendete Nachricht < 2kb
- Antwort: User 2 erhält die Nachricht innerhalb t ohne Verlust
  - t <= 1 sek

---

## Qualitätsattribute
### zuverlässige Zustellung von Audios innerhalb von 2ms (Performanz - 1) 
- Umgebung: App wird benutzt von verschiedenen Usern, welche Nachrichten austauschen 
  - Useranzahl > 1000
- Stimulus: User 1 sendet eine Audiodatei an User 2 
  - gesendete Nachricht < 5Kb
- Antwort: User 2 erhält die Audiodatei auf dem Chatbereich innerhalb t
  - t <= 2ms

---


# Übung 2, Wireframes und Usability Test

Team 2: Gergana Germanova, Daorsa Hasani, Sonja Klein 

---

## Figma

https://www.figma.com/file/DgyKwBguhKAP7Pa8NMEmHo/Cop-2-Cop-Nachricht-schreiben?node-id=0%3A1 

Test Prototype: https://www.figma.com/proto/DgyKwBguhKAP7Pa8NMEmHo/Cop-2-Cop-Nachricht-schreiben?node-id=2%3A291&scaling=scale-down&page-id=0%3A1&starting-point-node-id=2%3A291 

---

#### User Story 2, *Nachrichten erhalten/versenden*

Als *Bedienstete*, möchte ich *die Möglichkeit haben Nachrichten zu verschicken und zu bekommen*, damit *ich mit anderen kommunizieren kann*.

---

#### User Story 2, *Nachrichten erhalten/versenden*
## Akzeptanzkriterien:
- Man kann die Tastatur schließen, indem man irgendwo auf dem Chat klickt 
- Man kann von einem spezifischen Chat immer  mit dem Pfeil oben rechts zurück zu der Chat Übersicht 
- Wenn man das Nachrichtenfenster anklickt wird aus dem Sprachnachrichtenbutton ein Sende-Button
- Wenn man das Nachrichtenfenster anklickt wird die Tastatur geöffnet 
  
---

#### User Story 2, *Nachrichten erhalten/versenden*
## Akzeptanzkriterien:
- Wenn ich auf einen Buchstaben von der Tastatur klicke erscheint er mir im Schreibfenster
- Wenn ich den Senden Button klicke:
  - Nachricht verschwindet von Schreibfenster
  - Nachricht erscheint im Chatverlauf
  - Nachricht wird versandt
  
---

#### User Story 2, *Nachrichten erhalten/versenden*
## Nicht-fuktionalen Anforderungen:

- Eine unerfahrene Nutzer*in soll innerhalb von 4 Klicks eine Nachricht versenden können 
- Eine erfahrene Nutzer*in soll innerhalb von 1 min eine Standort verschickenn können 
- Eine erfahrene Nutzer*in soll bei geöffnete App max 7 Klicks brauchen um sein Profilbild zu ändern
- Eine unerfahrene Nutzer*in soll innerhalb von 1 min eine ungelesen Nachricht öffnen 



