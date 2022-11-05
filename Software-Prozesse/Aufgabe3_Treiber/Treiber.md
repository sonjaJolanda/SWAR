# Übung 2, Architektur-Treiber

Team 2: Gergana Germanova, Daorsa Hasani, Sonja Klein 

## Geschäftsziele

- Effiziente Kommunikation zwischen Bediensteten 
- Automatisierung von Berichterstellung 
- Genauen und automaitisierten Austausch von Wegbeschreibungen 
- Sicherheit vor unbefugten Dritten 
- Export von der App ins EU-Ausland 
  
## Rahmenbedingungen 

- Übereinstimmung mit den Gesetzen und Richtlinien für den Öffentlichen Dienst
- Vorgaben vom Auftraggeber 

## Wichtige funktionale Anforderungen

- Als *Mitarbeitender in der Polizeistelle*, möchte ich *einzelne Bilder auf Twittter posten können*, damit *ich der Öffentlichkeit effizienter Informationen bereitstellen kann*
- Als *Bediensteter*, möchte ich *selektierte Photos und Nachrichten exportieren können*, damit *ich sie leicht in Polizeiberichte importieren kann*.
- Als *Bediensteter*, möchte ich *dass nach zwei Jahren alle archivierte Daten gelöscht werden*, damit *ich keine unnötige Daten auf mein Messenger haben*.
- Als *Bediensteter*, möchte ich *dass niemand Unberechtigtes meine Nachrichten sehen kann*, damit *ich Informationen austauschen kann und trotzdem meine gesetzlichen Anforderungen einhalte*.
- Als *Bedienstete*, möchte ich *die Möglichkeit haben Nachrichten zu verschicken und zu bekommen*, damit *ich mit anderen kommunizieren kann*.

## Qualitätsattribute

TODO: Sie können die Attribute entweder in Tabellenform aufschreiben oder mit Stichpunkten. Für beides finden Sie hier eine Vorlage. Wählen Sie die, mit der Sie besser zurechtkommen.

### zuverlässige Zustellung von einfachen Nachrichten innerhalb von 2ms (Performanz - 1) 
- Umgebung:App wird benutzt von verschiedenen Usern, welche Nachrichten austauschen 
  - Useranzahl > 1000
- Stimulus: User 1 sendet eine Nachricht an User 2 
  - gesendete Nachricht < 5Kb
- Antwort: User 2 erhält die Nachricht auf dem Chatbereich innerhalb t
  - t <= 2ms

### zuverlässige Zustellung von Mediendateien innerhalb von 1m (Performanz - 2) 
- Umgebung:App wird benutzt von verschiedenen Usern, welche Nachrichten austauschen 
  - Useranzahl > 1000
- Stimulus: User 1 sendet eine Mediendatei (Photo, Video, Sprachnachricht) an User 2 
  - gesendete Nachricht < 3Mb
- Antwort: User 2 erhält die Mediendatei auf dem Chatbereich innerhalb t
  - t <= 1 m

### zuverlässige Zustellung eines Standortes innerhalb von 1m (Zuverlässigkeit - 3) 
- Umgebung:User 1 befindet sich in einem ländlichen Gebiet. Die verfügbare Bandbreitenverbindung ist auf UMTS-HSPA beschränkt.
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s
- Stimulus: User 1 sendet Standort an User 2 
  - gesendete Standortnachricht < 3Mb
- Antwort: User 2 erhält den Standort auf dem Chatbereich innerhalb t
  - t <= 1 m

### zuverlässige Wegbeschreibung zu einem empfangenem Standort ohne Fehlleitung (Zuverlässigkeit - 4) 
- Umgebung:User 1 befindet sich in einem ländlichen Gebiet. Die verfügbare Bandbreitenverbindung ist auf UMTS-HSPA beschränkt.
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s
- Stimulus: User 1 möchte zu einem empfangenen Standort geleitet werden
  - empfangener Standort hat eine Genauigkeit von einem Radius < 30m 
- Antwort: User 2 erhält die Wegbeschreibung in einem seperaten Fenster der Applikation
  - jede Wegbeschreibung führt zum Ziel (empfangener Standort) 

### effizienteste Wegbeschreibung zu einem empfangenem Standort (Effizienz - 5) 
- Umgebung:User 1 befindet sich in einem ländlichen Gebiet. Die verfügbare Bandbreitenverbindung ist auf UMTS-HSPA beschränkt.
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s
- Stimulus: User 1 möchte zu einem empfangenen Standort geleitet werden
  - .
- Antwort: User 2 erhält die kürzester Weg-Wegbeschreibung in einem seperaten Fenster der Applikation
  - es wird immer die im-Moment-kürzester-Weg-Wegbeschreibung von allen Alternativen angezeigt

### zuverlässige Zustellung von Standort innerhalb von 1m (Zuverlässigkeit - 6) 
- Umgebung:User 1 befindet sich in einem ländlichen Gebie. Die verfügbare Bandbreitenverbindung ist auf UMTS-HSPA beschränkt.
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s
- Stimulus: User 1 sendet eine MedienDatei(Photo, Video, Sprachnachricht) an User 2 
  - gesendete Nachricht < 3Mb
- Antwort: User 2 erhält die Nachricht auf dem Chatbereich innerhalb t
  - t <= 1 m

### Anzeigen von Online-Offline Informationen innerhalb von 1sek (Performanz - 7) 
- Umgebung: User 1 hat die Applikation mit dem Chatbereich des Users 2 geöffnet
  - Useranzahl > 1000
- Stimulus: User 2 öffnet die Applikation und wechselt somit von 'Offline' zu 'Online'. 
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s
- Antwort: User 1 sieht den Aktuellen Zustand innerhalb t
  - t <= 1sek

### Medien und Nachrichten werden innerhalb von 1sek exportiert (Performanz - 8) 
- Umgebung: User 1 hat die Applikation mit dem Chatbereich des Users 2 und einer darin enthaltenen Mediendatei geöffnet
  - Useranzahl > 1000
- Stimulus: User 1 möchte diese Mediendatei exportieren um sie in einen Polizeibericht hinzuzufügen
  - gesendete Mediendatei < 3Mb
- Antwort: User 1 erhält die exportierte Datei innerhalb t
  - t <= 1sek

### generierte Informationen werden automatisch archiviert (Datensicherheit - 9) 
- Umgebung: User 1 hat die Applikation und den Chatbereich mit User 2 geöffnet 
  - Useranzahl > 1000 
- Stimulus: User 1 sendet eine Nachricht an User 2
  - gesendete Nachricht < 5kb
- Antwort: Die neu generierten Informationen werden in einem Archiv gespeichert innerhalb t
  - t <= 1min

### Archivierte Informationen werden nach 2 Jahren automatisch gelöscht (Datensicherheit - 10) 
- Umgebung: Die Daten von User 1 sind archiviert
  - Archivgröße > 20 GB 
- Stimulus: Daten des User 1 werden älter als 2 Jahre
  - Nachricht > 2 Jahre
- Antwort: Die Daten des User 1, die die 2 Jahre Grenze überschritten haben, werden innerhalb t gelöscht
  - t <= 1min

### Mediendateien werden innerhalb von 20 sek auf Twitter gepostet (Performanz - 11) 
- Umgebung: User 1 hat den Chatbereich mit User 2 und eine darin enthaltene Mediendatei geöffnet 
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s, Useranzahl > 1000
- Stimulus: User 1 möchte diese Mediendatei auf Twitter teilen
  - gesendete Mediennachricht < 3Mb
- Antwort: Die Mediendatei wird innerhalb t auf Twitter veröffentlicht
  - t <= 20 sek

### Archivierte Informationen werden vor fremden Dritten geschützt gespeichert (Sicherheit - 12) 
- Umgebung: Die Daten von User 1 sind archiviert
  - Archivgröße > 20 GB 
- Stimulus: Eine fremde dritte Person möchte die Daten von User 1 einsehen 
  - Eine Brute-Force Attack wird auf das Archiv ausgeübt
- Antwort: Die Daten des User 1 sind verschlüsselt und passwortgeschützt gespeichert, sodass ein fremder Dritter keinen Zugriff hat. Außerdem werden aktuelle Sicherheitsstandards eingehalten. 
  - Alle empfohlenen Sicherheitsstandards des BSI sind eingehalten

### Eine Gruppe wird erstellt und alle eingeladenen User werden innerhalb 1sek benachrichtigt (Performanz - 13) 
- Umgebung: User 1 hat den Chatbereich der Applikation offen
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s, Useranzahl > 1000
- Stimulus: User 1 erstellt eine neue Gruppe mit den Teilnehmern User 1, User 2 und User 3 
  - Gruppengröße > 2 User
- Antwort: User 2 und User 3 werden innerhalb t benachrichtigt, dass sie nun Teil der neu erstellten Gruppe sind
  - t <= 1 sek

### Eine Gruppe wird erstellt und alle eingeladenen User können die Inhalte des Chats innerhalb 1sek sehen (Zuverlässigkeit - 14) 
- Umgebung: User 1 und User 2 ist Teil der Gruppe A und hat den Chatbereich dieser Gruppe geöffnet
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s, Useranzahl der Gruppe > 1000
- Stimulus: User 1 sendet eine Nachricht in die Gruppe A
  - gesendete Nachricht < 2kb
- Antwort: User 2 erhält die Nachricht innerhalb t ohne Verlust
  - t <= 1 sek

### zuverlässige Zustellung von Audios innerhalb von 2ms (Performanz - 1) 
- Umgebung: App wird benutzt von verschiedenen Usern, welche Nachrichten austauschen 
  - Useranzahl > 1000
- Stimulus: User 1 sendet eine Audiodatei an User 2 
  - gesendete Nachricht < 5Kb
- Antwort: User 2 erhält die Audiodatei auf dem Chatbereich innerhalb t
  - t <= 2ms

---

#### Schneider: Nutzung bei beschränkter Bandbreite (S1.LimitedBandwidth)

- Umgebung: Ein Nutzer in einem ländlichen Gebiet nutzt die Logistik-App. Die verfügbare Bandbreitenverbindung ist auf UMTS-HSPA beschränkt. 
  - Netzwerkgeschwindigkeit < 7,2 Mbit/s
- Stimulus: Der Nutzer möchte sich die verfügbaren Transportaufträge in seiner Gemeinde anzeigen lassen.
  - Anzahl Aufträge < 10
- Antwort: Die App zeigt alle verfügbaren Transportaufträge innerhalb von t an
  - t < 0,5s

### Beispiel 2: Schneider: als Tabelle

| Kategorisierung  |                                                                                                                                     |                                                                                                                                 |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Szenario-Name    | Prägnanter,  kurzer Name                                                                                                            |                                                                                                                                 |
| Szenario-ID      | Eindeutige Kennung                                                                                                                  |                                                                                                                                 |
| **Beschreibung** | **Quantifizierung**                                                                                                                 |                                                                                                                                 |
| Umgebung         | Kontext und/oder Ausgangssituation, die auf dieses Szenario zutrifft                                                                | Messbare Effekte, die die Umgebung betreffen                                                                                    |
| Stimulus         | Das Ereignis, der Auslöser oder die Bedingung, die sich aus diesem Szenario ergeben                                                 | Messbare Effekte, die den Stimulus (Auslöser) betreffen                                                                         |
| Antwort          | Die erwartete Reaktion des Systems auf das Szenario-Ereignis (Black-Box-Ansicht, die keine Einschränkungen für das Design vorsieht) | Messbare Effekte, die auf die Reaktion zutreffen, Messbare Indikatoren, dass das Szenario durch die Architektur umgesetzt wurde |
