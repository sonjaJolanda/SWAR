---
marp: true
theme: default
paginate: true
footer: Übung Software-Architektur 2 -  (Prof. Schneider), Gruppe 2
# Keine Nummer und Fußzeile auf der ersten Folie:
_paginate: false
_footer: " "
---

# Übung 2 , Anforderungen

Team 2: Gergana Germanova, Daorsa Hasani, Sonja Klein 

---

## Stakeholder
- Deutschlandweit die Bediensteten aller Polizeireviere
  - Streifenbedienstete 
  - Leitstellenpersonal
  - Pressestelle der Polizei
  - IT Abteilung der Polizei
  - ...  
- Presse allgemein
- Bevölkerung
- EU-Ausland Polizeireviere für evtl. Erweiterung

---

## Endbenutzertypen
- Streifenbedienstete 
- Leitstellenpersonal
- Pressestelle der Polizei

---

## Entwicklungsteam 1
- Projektmanager
- Projektmanager (teilzeit aus der IT Abteilung der Polizei)?

---
## Entwicklungsteam 2

- SCRUM-TEAM
  - Scrum-Master
  - Produkt-Owner 
  - Developers
    - Back-End x 2
    - Front-End x 2
    - Full-Stack x 1
    - DevOps x 1(macht einer der Entwickler zusätzlich)
    - QA x 1
    
2,5 Leute zur Verfügung als Puffer
    
---
## Entwicklungsteam 3

Wir haben uns entschieden das System neu zu entwickeln. Wir haben spezifische Anforderungen und die Komplexität des Systems durch eventuelle Sicherheitsanforderungen ist uns noch nicht bekannt. Daher finden wir die Scrum-Vorgehnsweise am passenden. 

Die Überlegung ein System einzukaufen wurde verworfen, da unsere systemspezifischen Anforderungen(Sicherheit, ...) nicht getroffen werden könnten. Ein großer möglicher Zeitaufwand könnte außerderm auf uns zukommen, wenn wir unsere spezifischen Anforderungen in ein bestehendes System einbauen wollen. 

---

## Benutzeranforderungen
---

### **Benutzeranforderungen: Nachrichten**

#### User Story 1, *Push Nachrichtenmeldungen*

Als *Bedienstete*, möchte ich *über neue Nachrichten informiert werden*, damit *ich zeitnah auf dieser reagieren kann*.

#### User Story 2, *Nachrichten erhalten/versenden*

Als *Bedienstete*, möchte ich *die Möglichkeit haben Nachrichten zu verschicken und zu bekommen*, damit *ich mit anderen kommunizieren kann*.

---

### **Benutzeranforderungen: Nachrichten**

#### User Story 3, *Audio-Nachrichten*

Als *Bediensteter*, möchte ich *durch Audios Informationen mit anderen Bediensteten austauschen können*, damit *der Informationsaustausch noch einfacher gelingt*.

#### User Story 4, *Videos und Fotos versenden*

Als *Bedienstete*, möchte ich *die Möglichkeit haben Videos und Bilder zu verschicken und zu bekommen*, damit *ich mehr als nur durch Text kommunizieren kann*.

---

### **Benutzeranforderungen: Nachrichten**

#### User Story 5, *Online/Offline Bezeichnung*

Als *User*, möchte ich *sehen können, wer online ist*, damit *ich eine Übersicht habe wen ich schnell erreichen kann*.

#### User Story 6, *Standort-Sharing*

Als *Bediensteter*, möchte ich *Standort sowie deren Wegbeschreibungen teilen und einsehen*, damit *ich schnell an Orte kommen kann oder ich schnell erreicht werde*.

---

### **Benutzeranforderungen: Export**

#### User Story 7, *Posts auf Twitter erstellen*

Als *Mitarbeitender in der Polizeistelle*, möchte ich *einzelne Bilder auf Twittter posten können*, damit *ich der Öffentlichkeit effizienter Informationen bereitstellen kann*.

#### User Story 8, *Chat Nachrichten/Photos exportieren*

Als *Bediensteter*, möchte ich *selektierte Photos und Nachrichten exportieren können*, damit *ich sie leicht in Polizeiberichte importieren kann*.

---

### **Benutzeranforderungen: Achivierung**

#### User Story 9, *automatische Archivierung*

Als *Bediensteter*, möchte ich *alle meine Daten zwei Jahren lang in einer Archive gespeichert haben*, damit *ich auf eventuelle wichtige Informationen zugreifen kann*.

#### User Story 10, *archivierte Nachrichten nach zwei Jahren löschen*

Als *Bediensteter*, möchte ich *dass nach zwei Jahren alle archivierte Daten gelöscht werden*, damit *ich keine unnötige Daten auf mein Messenger haben*.

---

### **Benutzeranforderungen: Benutzerverwaltung**

#### User Story 11, *Gruppenerstellung*

Als *Bedienstete*, möchte ich *Gruppen erstellen oder beitreten können*, damit *ich mit meinem Team Informaitonen leicht teilen kann*.

#### User Story 12, *Rollen*

Als *Nutzer*, möchte ich *sehen können welche Rollen meine Kommunikationspartner besitzen*, damit *ich angemessen mit diesen umgehen kann*.


#### User Story 13, *Gruppeneinteilung*

Als *Leitender*, möchte ich *Teams/Gruppen erstellen können*, damit *Nachrichten gesammelt eine Personengruppe erreichen können*.

---

### **Benutzeranforderungen: Sonstiges**

#### User Story 14, *Web-Erweiterung*

Als *Bediensteter*, möchte ich *auf alle (oder nur die wichtigsten) Funktionen auch in einem Webbrowser zugreifen können*, damit *diese Funktionen auch ohne mobildes Endgerät zur Verfügung stehen*.

#### User Story 15, *Sicherheit*

Als *Bediensteter*, möchte ich *dass niemand Unberechtigtes meine Nachrichten sehen kann*, damit *ich Informationen austauschen kann und trotzdem meine gesetzlichen Anforderungen einhalte*.

---

## Systemanforderungen

Push Nachrichtenmeldungen (User Story 1)
> ### Anforderung 1.1, *Push-Nachrichten aktiviert*
> **Given:** Ein anderer User2 (Bediensteter) hat eine Nachricht an den User1 gesendet <br>
> **When:** User 1 hat Push-Nachrichten erlaubt <br>
> **Then:** User 1 soll Push-Nachricht auf seinem Smartphone erhalten

---
## Systemanforderungen

Push Nachrichtenmeldungen (User Story 1)
> ### Anforderung 1.2, *Push-Nachrichten deaktiviert*
> **Given:** Ein anderer User2 (Bediensteter) hat eine Nachricht an den User1 gesendet <br>
> **When:** User 1 hat Push-Nachrichten nicht erlaubt <br>
> **Then:**  User 1 soll keine Push-Nachricht auf seinem Smartphone erhalten

> ...

---
## Systemanforderungen

Nachrichten versenden/erhalten  (User Story 2)
> ### Anforderung 2.1, *Nachrichten-Button*
> **Given:** die App ist geöffnet <br>
> **When:** User 1 möchte eine neue Nachricht versenden <br>
> **Then:** User 1 kann auf einen Button klicken um eine neue Nachricht zu verfassen

---
## Systemanforderungen

Nachrichten versenden/erhalten  (User Story 2)
> ### Anforderung 2.2, *Nachrichten-Keyboard*
> **Given:** die Neue-Nachricht-Verfassen-Bereich ist geöffnet <br>
> **When:** User 1 möchte einen Text verfassen <br>
> **Then:** Ein Keyboard öffnet sich durch welches man einen dann angezeigten text verfassen kann

---
## Systemanforderungen

Nachrichten versenden/erhalten  (User Story 2)
> ### Anforderung 2.3, *Nachrichten-Status gesendet*
> **Given:** User1 hat eine Nachricht gesendet und hat den Chat geöffnet <br>
> **When:** Nachricht wurde erflogreich gesendet <br>
> **Then:**  User 1 soll ein Hacken sehen 

---
## Systemanforderungen

Nachrichten versenden/erhalten  (User Story 2)
> ### Anforderung 2.4, *Nachrichten-Status erhalten*
> **Given:** User1 hat eine Nachricht gesendet und hat den Chat geöffnet <br>
> **When:** Nachricht wurde bei User 2 erfolgreich erhalten <br>
> **Then:**  User 1 soll zwei Hacken sehen 

---
## Systemanforderungen

Nachrichten versenden/erhalten  (User Story 2)
> ### Anforderung 2.5, *Nachrichten-Status gelesen*
> **Given:** User1 hat eine Nachricht gesendet und hat den Chat geöffnet <br>
> **When:** Nachricht wurde von User 2 geslesen<br>
> **Then:**  User 1 soll zwei farbige Hacken sehen 

> ...