# Übung 5: Deploymentgetriebene Zerlegung, Abbildung Runtime auf Devtime, Umsetzung von Qualitätsattributen

Team 2: Sonja Klein, Gergana Germanova, Daorsa Hasani

## Deployment

![](Deployment@Runtime.drawio.svg)

### Welche Ausführungsumgebungen gibt es? Z.B. Webbrowser, Mobilgerät, (Applikations‑)Server, Docker-Host, Cloud-Dienst XYZ, …
- Webbrowser und Mobilgerät. Mobilgerät haben wir nur OS weil wir die Beamten nur Apple Geräte nutzen werden um maximale Sicherheit zu gewährleisten und wir deshalb kein Android usw. anbieten müssen.
- Wir haben uns für die MicroServices Architektur entschieden, um unser System leicht austauschbar zu gestalten. 

### Welches Deployment-Artefakt wird dort zur Ausführung gebracht? Z.B. ZIP-Datei mit HTML-, CSS- und JS-Skript-Dateien für den Webclient, JAR-Datei mit dem Java-Code, Docker-Container mit Paketen XYZ und Dateien ABC, …
- Die Jar Dateien der MicroServices, die Mobile App Datei in der VM und die Cop2Cop Web App für den Browser.

### Welche Funktionalität wird in welchem Deployment-Artefakt realisiert?
- die Mobile App Datei und die Web App Datei realisieren das Frontend 
- die Cop2Cop_Gateway.jar realisiert ein Gateway mit welchem die Frontends kommunizieren
- die Microservices Jars realisieren einmal eine Userverwaltung, einmal eine Messagingverwaltung und einmal das Archiv. 

### - Wie viele Instanzen gibt es von den verschiedenen Ausführungsumgebungen? 
- Es gibt jede Ausführungsumgebung nur einmal.

### - Wie viele Datenbanken? 
- Wir haben 3 Datenbanken. (Archiv, User, Messages)

### - Wie viele Instanzen eines jeweiligen externen Systems? 
- Es gibt sehr viele Clients, es gibt einmal Twitter, einmal Word, einmal Maps.

### Wie sind die Abhängigkeiten zwischen den verschiedenen Nodes/Execution Environments/Systemen?
- Die Frontends nutzen Twitter um zu posten
- Die Frontends nutzen Maps um Directions/Location zu bekommen 
- Das Gateway spricht Word an, genau dann, wenn eines der Microservice Word nutzen möchte. 

## Abbildung Runtime auf Devtime

![](Funktionale_Zerlegung_Runtime.drawio.svg)

### Welche Programmiersprachen und Technologien wollen Sie verwenden? Es können auch mehrere sein für unterschiedliche Teile.
- Framework: SpringBoot benutzen wir für das ganze Backend, Java
- Maven für den Build
- Jenkins fürs Testen und Integrieren
- Frontend: Vue.js  und Vuetify.js

### Wie viele einzelne Projekte gibt es? Z.B. Projekt für Backend, Projekt für Mobile-Client, Projekt für Web-Client. Oder aber "Full-Stack" nur ein Projekt mit allem Code.
- für Frontend
  - Projekt für Frontend OS
  - Projekt für Frontend WebApp
- für Backend
  - Projekt für Gateway
  - Projekt für User
  - Projekt für Messaging
  - Projekt für Archive

### Wie wird der Code verwaltet? Ein Git-Repository? Mehrere Repositories?
- Über Git und für jedes Projekt ein Repository (insgesamt 6)

### Wie werden die einzelnen funktionalen Komponenten auf die Entwicklungszeit abgebildet? Eine Komponente = ein Modul? Oder mehrere Module pro Komponente? Gibt es Grund-Module oder Bibliotheken, in die Funktionalität zur Wiederverwendung ausgelagert werden kann? Es kann sich herausstellen, dass Sie die Komponenten aus der letzten Übungsabgabe in Komponenten auf Client- und Server-Seite unterscheiden müssen, falls Sie sich für eine Client-Server-Architektur entschieden haben.
- Eine Komponente entspricht in der Regel einem Modul. 
- Eine Ausnahme bildet hierbei aber die Gateway-Komponente. Diese enthält die Module Authentifizierung und Routing.

### Wie werden Module untergliedert? Stichwort Packages und Package-Struktur.
- src
  - main
    - java
      - rest
        - controller
      - services
        - service
        - mapper
      - DAO
        - repository
- ...

## Umsetzung von Qualitätsattributen

## Qualitätsattribute
### Archivierte Informationen werden nach 2 Jahren automatisch gelöscht (Datensicherheit - 10) 
- Umgebung: Die Daten von User 1 sind archiviert
  - Archivgröße > 20 GB 
- Stimulus: Daten des User 1 werden älter als 2 Jahre
  - Nachricht > 2 Jahre
- Antwort: Die Daten des User 1, die die 2 Jahre Grenze überschritten haben, werden innerhalb t gelöscht
  - t <= 1min

![](Archiv-Cron/Funktionale_Zerlegung_Runtime_Archiv_Cron.drawio.svg)


## Qualitätsattribute
### Archivierte Informationen werden vor fremden Dritten geschützt gespeichert (Sicherheit - 12) 
- Umgebung: Die Daten von User 1 sind archiviert
  - Archivgröße > 20 GB 
- Stimulus: Eine fremde dritte Person möchte die Daten von User 1 einsehen 
  - Eine Brute-Force Attack wird auf das Archiv ausgeübt
- Antwort: Die Daten des User 1 sind verschlüsselt und passwortgeschützt gespeichert, sodass ein fremder Dritter keinen Zugriff hat. Außerdem werden aktuelle Sicherheitsstandards eingehalten. 
  - Alle empfohlenen Sicherheitsstandards des BSI sind eingehalten

![](Archiv-Cron/Funktionale_Zerlegung_Runtime_Archiv_Sicher.drawio.svg)

  
## Designprinzipien
- Trennung der Zuständigkeiten: Durch die Microservices-Architektur 
- Kapselung: Durch die Microservices
- Divide and Conquer: Durch die Microservices

## Architektur-Trends
- Microservices: siehe Designprinzipien
- Wir werden mit einem DevOps Team arbeiten. → Es gibt nur ein Team, dh. das eine Team hat volle Zuständigkeit