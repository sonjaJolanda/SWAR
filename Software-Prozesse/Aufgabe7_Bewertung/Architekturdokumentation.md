# Übung 5, Architektur-Dokumentation <!-- omit in toc -->

Team 4: Maren Mutter, Andreas Ritter 

- [1. Einleitung](#1-einleitung)
  - [1.1. Geschäftskontext](#11-geschäftskontext)
  - [1.2. Systemübersicht](#12-systemübersicht)
  - [1.3. Randbedingungen (Constraints)](#13-randbedingungen-constraints)
  - [1.4. Stakeholder](#14-stakeholder)
  - [1.5. Ziele des Dokuments](#15-ziele-des-dokuments)
- [2. Systemkontext und Domäne](#2-systemkontext-und-domäne)
  - [2.1. System-Kontext-Abgrenzung](#21-system-kontext-abgrenzung)
- [3. Architekturtreiber (Funktion und Qualität)](#3-architekturtreiber-funktion-und-qualität)
  - [3.1. Wesentliche funktionale Anforderungen](#31-wesentliche-funktionale-anforderungen)
  - [3.2. Qualitätsattribute](#32-qualitätsattribute)
- [4. Systemdekomposition](#4-systemdekomposition)
  - [4.1. Lösungsansatz und zentrale Architekturentscheidungen](#41-lösungsansatz-und-zentrale-architekturentscheidungen)
  - [4.2. Systemstruktur](#42-systemstruktur)
  - [4.3. Datenmodell](#43-datenmodell)
  - [4.4. Code-Organisation (Abbildung Laufzeit auf Entwicklungszeit)](#44-code-organisation-abbildung-laufzeit-auf-entwicklungszeit)
  - [4.5. Deployment und Betrieb](#45-deployment-und-betrieb)
  - [4.6. Technologien](#46-technologien)
- [5. Architekturkonzepte](#5-architekturkonzepte)
  - [5.1. Konzept 1 Security](#51-konzept-1-security)
  - [5.1.1. Architektur-Treiber](#511-architektur-treiber)
    - [5.1.2. Lösungsidee](#512-lösungsidee)
    - [5.1.3. Design-Entscheidungen](#513-design-entscheidungen)
    - [5.1.4. Verworfene Alternativen](#514-verworfene-alternativen)
  - [5.2. Konzept 2 Fehlertoleranz](#52-konzept-2-fehlertoleranz)
  - [5.2.1. Architektur-Treiber](#521-architektur-treiber)
    - [5.2.2. Lösungsidee](#522-lösungsidee)
    - [5.2.3. Design-Entscheidungen](#523-design-entscheidungen)
    - [5.2.4. Verworfene Alternativen](#524-verworfene-alternativen)
- [6. Risiken und technische Schulden](#6-risiken-und-technische-schulden)
- [7. Ausblick und Pläne für die Zukunft](#7-ausblick-und-pläne-für-die-zukunft)
- [8. Glossar](#8-glossar)

## 1. Einleitung

In der Einleitung schaffen wir ein grundlegendes Verständnis über das System für den Leser. Wir beschreiben den Geschäftskontext mit dem System zugrunde liegenden Geschäftszielen, geben eine Übersicht auf oberster Ebene über das System, nennen zu berücksichtigende Randbedingungen und relevante Stakeholder. Darüber hinaus erläutern wir die Ziele dieses Dokuments.

### 1.1. Geschäftskontext

Unser System soll speziell für die deutsche Automobilindustrie sein. Das System soll den Mitarbeiter*innen der Automobilitätsindustrie Assistenz sein, um sich weiterzubilden, sich auszutauschen, neue Trends kennenzulernen und Infos über Arbeitsvorgänge zu erhalten.  

Mithilfe der Applikation können Arbeitsfehler vermieden und die Produktion effizienter gestaltet werden. Bisher existierte kein geeignetes Medium, um Wissen innerhalb des Unternehmens diesbezüglich auszutauschen. Es soll aber auch der Wissensaustausch innerhalb der Unternehmen erleichtert werden, damit deren Produktivität verbessert wird. Langfristig sollen auch Schulungskosten mithilfe der Plattform reduziert werden. Als lokaler IT-Dienstleister wurden wir beauftragt, da wir uns auf kundenspezifische Individualsoftware spezialisiert haben.  

Unsere Geschäftsziele sind es, innerhalb der nächsten fünf Jahre zu den fünf meistgenutzten Apps der Automobilindustrie Deutschlands zu gehören und uns daraufhin ab 2025 auf den europäischen Markt auszubreiten. Das System wird in Zukunft auch für Drittanbieter nutzbar gemacht, um die Reichweite zu erhöhen. 

### 1.2. Systemübersicht

Das System soll eine Video-Plattform sein, auf der die User Videos hochladen und anschauen können. Dies sind die Kern-Funktionen, die den größten Nutzen ausmachen. Die User sind hier die Mitarbeiter*innen der deutschen Automobilindustrie. Um die Anmeldung zu erleichtern, möchten wir das Login mithilfe der Firmenaccounts ermöglichen.  

Da Videos die Hauptfunktionalität darstellen, beinhalten sie neben der offensichtlichen mp4 Datei auch weitere Informationen, wie den User, der es hochgeladen hat, den Videotitel und eine Video-Beschreibung.  

Um die Interaktion der User auf dem System zu gewährleisten, wollen wir zusätzlich als Kern-Funktion einen Kommentar- und Like-Funktion einbauen. Außerdem können Videos aus der App direkt geteilt oder auch im Firmen-Intranet eingebettet werden.   

### 1.3. Randbedingungen (Constraints)

 Wesentliche Einschränkungen von Car-u-Cation:  

- über 1000000 Nutzer sollen System nutzen  
- Videos können auch offline ohne Internet angeschaut werden  
- nicht öffentlich gekennzeichnete Videos können nur innerhalb derselben Firma angeschaut werden  
- ein Firmenaccount muss für den Login verwendet werden  
- alle Daten sollen in Deutschland gespeichert werden 

### 1.4. Stakeholder

- Interne und externe Stakeholder 
  - Betreibende der Plattform "Car-u-cation" 
  - Auftraggeber*innen (Geschäftsführung): Gibt die Entwicklung in Auftrag 
- Direkte Stakeholder
  - Teilnehmende Automobilkonzerne  
  - Mitarbeiter*innen der teilnehmenden Automobilkonzerne 
- Indirekte Stakeholder 
  - (Automobilindustrie) 
  - Serverdienstleister*innen 

### 1.5. Ziele des Dokuments

Dieses Dokument richtet sich an unser Entwicklungsteam. Es soll verstehen, wieso wir uns für welche Architekturprinzipien entschieden haben, welche wir verworfen haben und welche Key-Punkte uns bei der Entwicklung des Systems wichtig sind.  

Die Inhalte dieses Dokuments dienen als Entwurf und Ideensammlung, gemeinsam mit dem Entwicklungsteam können die genannten Punkte noch überarbeitet und spezifiziert werden. 

## 2. Systemkontext und Domäne

Wir beschreiben in diesem Kapitel, in welchem Kontext das System eingesetzt wird.

### 2.1. System-Kontext-Abgrenzung

Anders als in anderen Architekturdokumentationen haben wir uns hier beabsichtigt für nur eine User-Rollen entschieden. Die Rolle Consumer, welche Videos anschaut und die Rolle Uploader, welche Videos hochlädt, können jeweils die andere Rolle einnehmen und haben somit keine direkt differenzierbaren Funktionalitäten. 
Eine genaue Beschreibung der System-Kontext-Abgrenzung kann der untenstehenden Notiz entnommen werden.

![system-kontext](Übung04-Architektur/../../Übung04-Architektur/System-Kontext.svg)

## 3. Architekturtreiber (Funktion und Qualität)

In den folgenden Kapiteln wird ein Überblick über die wichtigsten Anforderungen für das System gegeben, welche die Ausgestaltung der Architektur beeinflussen. Diese Anforderungen, genannt Architekturtreiber, umfassen  funktionale Anforderungen und Qualitätsanforderungen (in diesem Kapitel beschrieben) sowie Geschäftsziele und Randbedingungen (bereits in Kapitel 1 beschrieben).

### 3.1. Wesentliche funktionale Anforderungen

- Über die App lassen sich Videos abspielen/hochladen und herunterladen 
- Es werden automatisch Videos mit ähnlichem Inhalt vorgeschlagen  
- Videos können bereits im Vollbildmodus geliked und Kommentiert werden  
- Car-u-Cation ermöglicht es, dass Videos auf Wunsch nur von bestimmten Gruppen gesehen werden können 
- User können sich über ihren Firmenaccount mit Benutzername und Passwort anmelden 

### 3.2. Qualitätsattribute


| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Verfügbarkeit |               |
| Szenario-ID      | V01        |               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Ein User ist mehrmals pro Woche in der App eingeloggt | ca. 260-mal in Jahr
| Stimulus         | Der User schaut sich während der Arbeitszeit Videos an, um damit zu lernen | 40 * 52 = 2.080 |
| Antwort          | Die Car-u-Cation App ist erreichbar und lässt sich ohne Einschränkung bedienen | 99,9% Verfügbarkeit (2,08h dowm-time pro Jahr während der Arbeitszeit) |


| Kategorisierung  | Hoch                           |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Leistungseffizienz |               |
| Szenario-ID | L01
||**Beschreibung** | **Quantifizierung** | |               |
| Umgebung         | Der User hat eine DSL-Verbindung (x) | x = 50 Mbits/s
| Stimulus         | User lädt ein Video hoch | Größe des Videos 280MB |
| Antwort          | Das Video ist in t Sekunden hochgeladen und zum anschauen bereit| t = 45s |

| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Benutzbarkeit  |               |
| Szenario-ID      | B02      |               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Ein Mitarbeiter eines Automobilherstellers möchte Car-u-Cation nutzen um Videos anzusehen | User ist nicht eingeloggt
| Stimulus         | Mitarbeiter Lädt die App im Appstore herunter | Maximale Zeit zum Start der App: 3 Minuten |
| Antwort          | Das System bietet die Möglichkeit, Benutzerfreundlich Videos zu sehen | Maximal 3 Clicks nach öffnen der App |

| Kategorisierung  | Hoch                   |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Security |               |
| Szenario-ID      | S03|               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Ein nicht angemeldeter Nutzer öffnet Car-u-cation |  |
| Stimulus         | Dieser sucht nach Videos einer bestimmten Kategorie |"Konstuktion Motorblock", 10 Videos pro Seite |
| Antwort          | Es werden nur Videos angezeigt, die als öffentlich gekennzeichnet sind | |


| Kategorisierung  | Hoch                           |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Benutzbarkeit |               |
| Szenario-ID      | B01|               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Ein angemeldeter Nutzer hat ein Tutorial-Video gefilmt und geschnitten.|  |
| Stimulus         | Ein Video wird von einem Benutzer hochgeladen. | Qualität 1080p |
| Antwort          | Das Video soll in niedrigeren Auflösungen verfügbar sein. Das System skaliert das hochgeladene Video automatisch auf niedrigere Auflösungen herunter | Max. Auflösung=Upload Auflösung des Nutzers Sklaierung auf Qualität 720p, 480p, 240p |



| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Security zum Gruppenbeitritt |               |
| Szenario-ID      | S02       |               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Ein Mitarbeiter möchte einer Unternehmens-Gruppe beitreten ||
| Stimulus         | Der Mitarbeiter wird gebeten, sich über die Unternehmens-Plattform anzumelden | Anhand von Mail-Name wird innerhalb von 3s die korrespodierende Unternehmensplattform gesucht |
| Antwort          | Das System ermöglicht erst dann Zugriff zu den Gruppenspezifischen Videos, wenn der Mitarbeiter sich erfolgreich auf Unternehmensplattform anmelden konnte.



| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Datenintegrität |               |
| Szenario-ID      | D01       |               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Car-u-Cation wird von einer Mitarbeiterin benutz | In eingeloggtem Zustand
| Stimulus         | Die Mitarbeiterin gibt in den Einstellungen an, dass ihre Email Adresse für andere Nutzer verborgen bleiben soll | Einstellungen sind über 3 Clicks erreichbar |
| Antwort          | Das System blendet ihre Mail Adresse aus, welche sonst unter ihrem Benutzername sichtbar wäre | Ausblendung innerhalb 0,1 Sekunden nach Einstellung 



| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Verständlichkeit |               |
| Szenario-ID      | V01       |               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Der User hat eine DSL-Verbindung (x) | x = 50 Mbits/s
| Stimulus         | Der User filtert Videos nach Sprache | Eine Sprache wird ausgewählt |
| Antwort          | Die Anwendung zeigt schnellstmöglich (x Sekunden) die gesuchten Inhalte an | x = 3s



| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Kapazität |               |
| Szenario-ID      | K01       |               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Der User hat eine (schlechte) DSL-Verbindung (x) | x = 25 Mbits/s
| Stimulus         | Der User startet ein Video | Das Video hat eine Qualität von 1440p |
| Antwort          | Die Anwendung zeigt das Video automatisch in einer niedrigeren Qualität an | 360p



| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Funktionale Angemessenheit |               |
| Szenario-ID      | FA01       |               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Die App wird von einem Mitarbeiter aus dem Management benutzt | Tx-Rate = 170Mbit/s
| Stimulus         | Der User schreibt ein Kommentar unter ein Video | Kommentar besteht aus 200 Chars |
| Antwort          | Kommentar wird bei Klick auf Button unter den anderen Kommentaren angezeigt | TRUE (innerhalb von max. 3 Sekunde)



| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Nachweisbarkeit |               |
| Szenario-ID      | N01       |               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Eine Mitarbeiterin benutzt die Car-u-Cation App | Benutzerin ist eingeloggt
| Stimulus         | Die Mitarbeiterin lädt ein Video auf die Plattform hoch | Eine VideoID pro Video |
| Antwort          | Das System erzeugt einen Datenbankeintrag, der die VideoID der UserID zuweist | Das System erzeugt maximal eine UserID pro VideoID

| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Barrierefreiheit |               |
| Szenario-ID      | B01       |               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Ein Nutzer benutzt die Car-u-Cation App | Benutzerin ist eingeloggt
| Stimulus         | Der Nutzer lädt ein Video ohne Untertitel hoch  | Eine VideoID pro Video, Untertitel Ja/Nein|
| Antwort          | Das System erzeugt automatisch einen Untertitel anhand der hochgeladenen Tonspur | Innerhalb von 3sek/minute Video

| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Fehlertoleranz |               |
| Szenario-ID      | F01       |               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Eine Mitarbeiterin benutzt die Car-u-Cation App um ein Video anzuschauen | Benutzerin ist ausgeloggt
| Stimulus         | Die Mitarbeiterin navigiert zu dem gewünschten Video und drück "play" | Länge des Videos: 12 Minuten|
| Antwort          | Das System lädt Teile des Videos vorraus, um lags zu vermeiden | Das System lädt maximal ein Viertel des Videos vor (3 Minuten)

| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Verfügbarkeit |               |
| Szenario-ID      | V02       |               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Eine Mitarbeiterin besitzt ein altes Anroid Handy | Modelljahr: 2015
| Stimulus         | Die Mitarbeiterin lädt die App herunter und drückt auf "Anmelden" | | 
| Antwort          | Die App öffner sich und lässt sich auch mit diesem Betriebssystem bedienen | Auf bis zu 6 Jahre alter Software kompatibel

## 4. Systemdekomposition

In den Unterabschnitten dieses Kapitels beschreiben wir, wie die grundlegende Lösungsstrategie für das System ist, welche wichtigen Entscheidungen für das System getroffen wurden und warum und wie das System nach Funktionalität, Daten und Deployment gegliedert ist.

### 4.1. Lösungsansatz und zentrale Architekturentscheidungen

Grundsätzlich ist unser System sehr Frontend lastig. Unser Hauptziel ist es, eine gute User Experience zu bieten und schnell, einfach und übersichtlich zu sein.  

Da wir keine komplizierten Berechnungen, Datenobjekte oder Controller haben, wird sich die Komplexität des Backends in Grenzen halten. Grundsätzlich müssen wir das beim Entwerfen eines Designkonzepts und bilden eines Entwicklungsteams beachten. 

Wir haben uns daher für das Designprinzip "Separation of concerns" entschieden. Aufgrund der Aufteilung des Development-Teams in Mobile Anwendung, Browser-App und Backend sehen wir hier die beste Einteilung der Verantwortlichkeiten. Auf die genaue Aufteilung und die nötige Manpower gehen wir an einer anderen Stelle des Dokuments ein.  

### 4.2. Systemstruktur

Im folgenden Diagramm (Functions@Devtime) wird beschrieben, wie die funktionale Dekomposition des Systems zur Laufzeit im Sinne der Komponenten aussieht. 
Das System wurde hierzu in zwei “Layer” aufgeteilt. Ein Layer ist ein logischer (horizontaler) Container für Komponenten und ermöglicht es, gemeinsame Zugriffsregeln für alle in der Schicht enthaltenen Komponenten zu definieren.  
In der Schicht User Interface (UI) befinden sich die verschiedenen Displays, welche einem User bei Benutzung der Applikation, Car-u-Cation, angezeigt werden.  
User Display ist die Anzeige eines Benutzerprofils und interagiert mit der externen Komponente Account Service um Informationen des Nutzers zu erhalten. 
Login Display ist die Oberfläche, welche dem User beim Login-Prozess angezeigt wird. Eine Anmeldung in das System erfolgt über den jeweiligen Firmenaccount der Mitarbeiter*innen. Die notwendigen Daten hierfür werden ebenfalls von der Komponente Account Service bezogen.  
Video Display interagiert mit dem Video Service und fordert eine ID um ein eindeutiges Video angezeigt zu bekommen.  
Da in Car-u-Cation auch die Möglichkeit besteht, explizit nach bestimmten Videos zu suchen, gibt es eine Komponente Search Display, die ebenfalls mit der Video Service Komponente kommuniziert.  
Die externen Systeme (Account- und Video Service) sind in dem Layer “Business Services” angesiedelt. 

![data-function](Übung04-Architektur/../../Übung04-Architektur/Data-and-Function-at-Runtime.svg)

### 4.3. Datenmodell

Im Folgenden sind die grundlegenden Daten aufgelistet, die in Car-u-Cation existieren. Es gibt jeweils requests (Anfragen) welche eine Komponente stellt (VideoRequest, SearchRequest, UserRequest und UserDisplayRequest). Die Antworten (Response) enthalten dann die Meta Daten zu einem Video oder einem User (siehe Schaubild Data@Runtime). 

![data](Übung04-Architektur/../../Übung04-Architektur/Data-at-Runtime.svg)

### 4.4. Code-Organisation (Abbildung Laufzeit auf Entwicklungszeit)

Ähnlich der Systemstruktur haben wir auch unseren Code Organisiert. Der Code ist auch hier in zwei Pakete Front- und Backend geteilt und eine Komponente entspricht einem Modul, also haben wir dafür einen Service im Frontend und einen Controller im Backend.  

Auch eine Versionskontrolle soll zum Einsatz kommen, um die Zusammenarbeit des Entwicklungsteams zu erleichtern. In der Vergangenheit hat sich GitLab hierfür durchgesetzt, verworfen wurden Alternativen, wie GitHub, AWS Code Commit und Beanstalk. Da wir Frontend und Backend getrennt betrachten halten wir es für sinnvoll, jeweils ein getrenntes Repository zu verwenden. 

![function](Übung04-Architektur/../../Übung05-Deployment/Functions-at-Devtime.svg)

### 4.5. Deployment und Betrieb

Car-u-Cation kann zum einen direkt im Web Browser aufgerufen werden, wird aber auch separat als Mobile App angeboten. Grund dafür ist zum einen, dass jedem User eine bestmögliche User Experience geboten werden soll, zum anderen bietet es die Möglichkeit auch Offline Videos laden zu können.  
Das Backend, welches über eine Java Virtual Machine läuft, bekommt über Schnittstellen die aus dem Front End angefragten Daten und stellt diese zur Verfügung. 

![system-kontext](Übung04-Architektur/../../Übung05-Deployment/Deployment-at-Runtime.svg)

### 4.6. Technologien

Was die Technologien angeht, haben wir uns im Frontend für Sails.js als MVC Webframework und Vue.js als reines JS Webframework entschieden, da wir die Technologien aus Lehrveranstaltungen kennen und sich unser junges Entwicklungsteam unter anderem bestehend aus Werkstudierenden mithilfe von umfangreichen Dokumentationen und Tutorials leicht einlernen kann.  

Im Backend wollen wir Java mit dem Spring Boot Framework nutzen, da auch hier schon viel Grundwissen im Team besteht und wir hier am meisten Potential sehen.  

Das folgende Schaubild zeigt die Technologien, die wir als externe Systeme verwenden wollen. Basierend auf unser Systemkonzept sind wir da auf die folgenden drei Technologien gekommen: 

Für die Anmeldung in das System mit Firmenaccounts brauchen wir eine Anbindung an die entsprechenden Accounts mit Accountinformationen, und das wollen wir mit der Account API ermöglichen. Die Datenspeicherung wollen wir gerne an einen Dienstleister abgeben, der vorzugsweise im EU-Raum, am liebsten aber in Deutschland sitzt. Nach einer Recherche haben wir uns unter anderem wegen der vielen Inklusivleistungen, individuellen Leistungspakete und keinen Einrichtungsgebühren für den deutschen Rechenzentrumsdienstleister all-inkl entschieden. Die Firma hat sich bei uns aus vielen Gründen gegen die Alternativen 1&1 IONOS, PureHost, HostEurope und webgo durchgesetzt.

![system-kontext](Übung04-Architektur/../../Übung05-Deployment/System-Kontext.svg)

## 5. Architekturkonzepte

In diesem Kapitel beschreiben wir, wie Sie die von den Architekturtreibern geforderten Funktions- und Qualitätsziele erreichen.

### 5.1. Konzept 1 Security

### 5.1.1. Architektur-Treiber

| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Sicherheit  |               |
| Szenario-ID      | S01        |               |
|| **Beschreibung** | **Quantifizierung**        |               
| Umgebung         | Ein Mitarbeiter nutzt die Car-u-Cation App | Erstnutzung des Systems
| Stimulus         | Der Mitarbeiter wird gebeten, ein Passwort festzulegen | 2 mal identische Eingabe |
| Antwort          | Das System bietet Vorschläge zur Sicherheit des Passworts an | Mindestens ein Sonderzeichen, Groß - und Kleinbuchstaben und mindestens eine Zahl |




#### 5.1.2. Lösungsidee

Um ein sicheres Login zu gewährleisten und das entsprechenden Qualitätsattribut umzusetzen, führen wir einen Secure Login Service ein. Dieser wird sich im Frontend befinden und zum einen die Passwörter verschlüsselt an das Backend schicken und zum anderen sichere Passwortvorschläge gibt. 

![quality-attribute Security](Übung04-Architektur/../../Übung05-Deployment/QualityAttributes-at-Devtime_Security.svg)

#### 5.1.3. Design-Entscheidungen

Aktuell ist es nicht geplant für dieses Konzept externe Frameworks oder Technologien zu benutzen. Wir werden die Möglichkeit der Hash-Passwörter und Passwortvorschläge eigens in unserem Frontend implementieren. 


#### 5.1.4. Verworfene Alternativen

Der Secure Login Service könnte auch im Backend untergebracht werden. Diese Idee haben wir aber verworfen. Aus Grund der Effizienz (der Login Service ist auch im Frontend) und für die maximale Sicherheit, ist es wichtig die Passwörter schon im Frontend zu verschlüsseln. 

### 5.2. Konzept 2 Fehlertoleranz
### 5.2.1. Architektur-Treiber

| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Fehlertoleranz |               |
| Szenario-ID      | F01       |               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Eine Mitarbeiterin benutzt die Car-u-Cation App um ein Video anzuschauen | Benutzerin ist ausgeloggt
| Stimulus         | Die Mitarbeiterin navigiert zu dem gewünschten Video und drück "play" | Länge des Videos: 12 Minuten|
| Antwort          | Das System lädt Teile des Videos vorraus, um lags zu vermeiden | Das System lädt maximal ein Viertel des Videos vor (3 Minuten)

#### 5.2.2. Lösungsidee

Um zu garantieren, dass ein Video ohne Probleme abgespielt werden kann wird ein zusätzlicher Caching Video Service implementiert. Dadurch sollen Teile des Videos vorgeladen werden und es kommt, unabhängig von der Länge des Videos zu keinen lags mehr, welche durch dieses Problem entstanden sind.

![quality-attribute Fehlertoleranz](Übung04-Architektur/../../Übung05-Deployment/QualityAttributes-at-Devtime_Fehlertoleranz.svg)


#### 5.2.3. Design-Entscheidungen

Der Caching Video Service wird im Frontend implementiert und kommuniziert mit dem Video Play Service, welcher die vorgeladenen Videos benutzt und dem im Backend implementierten Video Controller, welcher die Daten von dem externen Speicher Service anfragt.  

#### 5.2.4. Verworfene Alternativen

Auch hier war zunächst die Idee, diesen Service im Backend zu implementieren, wurde dann aber verworfen und die Entscheidung ist auf die Implementierung im Frontend gefallen: 
Grund hierfür ist, dass wenn das Video gecached wird und die Verbindung zum Backend abbrechen sollte, dieses nicht abgerufen werden kann. Somit wäre die funktionale Eignung dieses Service nicht gegeben.  
Durch die Implementierung im Frontend hat der User immer die Möglichkeit, ein bereits vorgeladenes Video anzuschauen. 

## 6. Risiken und technische Schulden

Durch die Abhängigkeit zu externen Systemen sind hier die größten Risikopotentiale – vor allem die externe Speicherung ist zum einen Kostenintensiv und könnte in Zukunft von unserem Team übernommen werden um komplette Kontrolle über die Daten zu haben.  

## 7. Ausblick und Pläne für die Zukunft

Für die Zukunft ist geplant, die Speicherung der Daten in unsere Verantwortung zu nehmen und sich nach und nach von den externen Systemen loszukoppeln. Dafür ist wichtig, das Team um einige Developer zu vergrößern.  
Das Team wird dann intensiv auf DevOps Methoden eingeschult, da wir hier großes Potenzial sehen, um die Qualität der Zusammenarbeit, aber auch den Output der geleisteten Arbeit zu verbessern. 

Für das System ist geplant eine Untertab für Shortclips zu entwickeln. Dadurch wollen wir parallel zu der Funktion als Lernplattform auch Möglichkeiten zur alltäglichen Unterhaltung bieten, sodass wir den Nutzen über die Arbeitszeit hinaus gestalten können. 

## 8. Glossar

Hier definieren wir Begriffe, die der Zielgruppe beim Lesen des Dokuments unklar sein könnten.

_Versionskontrolle_: Ein System, dass zur Erfassung von Änderungen an Dokumenten oder Dateien verwendet wird.

_GitLab_: Webanwendung zur Versionsverwaltung für Softwareprojekte.

_MVC_: Model-View-Controller ist ein Modell zur Unterteilung einer Software in die drei Komponenten Datenmodell, Präsentation und Programmsteuerung. Kann als Architektur- ,oder Entwurfsmuster eingesetzt werden. 

_Lag_: Eine erhöhte Verzögerungszeit in Computernetztwerken, die meist bei Problemen mit einer Server-Client-Verbindung auftreten, wenn Datenpakete unerwartet lange Zeit benötigen.

_Cache_: Bezeichnet in der Informationstechnik einen schnellen Pufferspeicher, der Zugriffe auf ein langsames Hintergrundmedium, oder aufwendige Neuberechnungen zu vermeinden hilft.
