---
marp: true
theme: default
paginate: true
footer: Übung Software-Architektur (Prof. Schneider), Gruppe ?
# Keine Nummer und Fußzeile auf der ersten Folie:
_paginate: false
_footer: " "
---

<!-- Das reserviert 30% der Folien-Breite für das Bild auf der rechten Seite. Das Bild an sich wird auf 80% Größe skaliert -->
![bg right:30% 80%](https://www.htwg-konstanz.de/fileadmin/pub/allgemein/Grafiken/logo/logo_pos.svg)

# Übung 7: Architekturbewertung

## eine Präsentation von Gruppe 2

- Gergana Germanova
- Daorsa Hasani
- Sonja Klein

---

## Recall: Rating of solution adequacy (1)

![](rating_gray.png) **N/A** means that the solution of the architecture driver has not (yet) been checked. It can also mean that the check was not possible as the architecture driver was stated but not agreed upon. **Das hier ist für die Übung KEINE gültige Option!**

![](rating_red.png) **NO** Solution Adequacy means there are major weaknesses in the solution or no solution may even be provided for the architecture driver.

![](rating_orange.png) **PARTIAL** Solution Adequacy means that the architecture driver is addressed but there are still weaknesses and risks that require further clarification or architectural rework.

---

## Recall: Rating of solution adequacy (2)

![](rating_yellow.png) **LARGE** Solution Adequacy means that the architecture driver is generally well addressed but with minor weaknesses or risks.

![](rating_green.png) **FULL** Solution Adequacy means there is confidence that the architecture driver is well addressed by the architecture decisions.

Als deutsche Begriffe können **KEINE**, **TEILWEISE**, **WEITGEHEND** und **VOLLSTÄNDIG** verwenden

---

## Bewertung Konzept 1 Security, Treiber 1

| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Sicherheit  |               |
| Szenario-ID      | S01        |               |
|| **Beschreibung** | **Quantifizierung**        |               
| Umgebung         | Ein Mitarbeiter nutzt die Car-u-Cation App | Erstnutzung des Systems
| Stimulus         | Der Mitarbeiter wird gebeten, ein Passwort festzulegen | 2 mal identische Eingabe |
| Antwort          | Das System bietet Vorschläge zur Sicherheit des Passworts an | Mindestens ein Sonderzeichen, Groß - und Kleinbuchstaben und mindestens eine Zahl |

---
Bewertung: ![](rating_yellow.png)  **WEITGEHEND**

Zum einen fehlt die Länge des Passwortes. 
Zum anderen ist die Quantifizierung der Umgebung eigentlich keine Quantifizierung sondern eine Beschreibung. Das ist nicht sehr schlimm, da man den Treiber trotzdem versteht, es ist jedoch anzumerken. 

Wir sind nicht davon überzeugt dass nur eine Frontendverschlüsselung ausreichend ist. In der Regel macht man die Verschlüsselung im Backend. Unser Vorschlag wäre es im Backend zu verschlüsseln um die Vorteile eines public ***und*** eines private Keys zu nutzen. 
Da wäre es sinnvoll noch einmal genauer zu recherchieren um die Entscheidung genauer begründen zu können.

Positiv aufgefallen ist die genaue Beschreibung warum Alternativen verworfen wurden.

---

## Bewertung Konzept Security, Zusammenfassung

Bewertung des Konzepts: ![](rating_yellow.png) **WEITGEHEND** 
Da wir nur einen Treiber haben, wird die Bewertung von diesem übernommen.

---

## Bewertung Konzept 2 Fehlertoleranz, Treiber 1

| Kategorisierung  | Hoch                        |               |
| ---------------- | -------------------------- | ------------- |
| Szenario-Name    | Fehlertoleranz |               |
| Szenario-ID      | F01       |               |
|| **Beschreibung** | **Quantifizierung**        |               |
| Umgebung         | Eine Mitarbeiterin benutzt die Car-u-Cation App um ein Video anzuschauen | Benutzerin ist ausgeloggt
| Stimulus         | Die Mitarbeiterin navigiert zu dem gewünschten Video und drück "play" | Länge des Videos: 12 Minuten|
| Antwort          | Das System lädt Teile des Videos vorraus, um lags zu vermeiden | Das System lädt maximal ein Viertel des Videos vor (3 Minuten)

---
Bewertung: ![](rating_green.png) **VOLLSTÄNDIG**

Auch hier gehört die Quantifzierung der Umgebung nicht in die Spalte der Quantifizierung sondern in die Beschreibung, aber auch hier verhindert dies nicht das Verständnis des Treibers.

Auch hier ist uns positiv aufgefallen, dass verworfene Alernativen erwähnt und erklärt wurden.

---

## Bewertung Konzept Fehlertoleranz, Zusammenfassung

Bewertung des Konzepts: ![](rating_green.png) **VOLLSTÄNDIG** 
Da wir nur einen Treiber haben, wird die Bewertung von diesem übernommen.

---

## Gesamtbewertung

- Konzept 1 Security: ![](rating_yellow.png) **WEITGEHEND** 
- Konzept 2 Fehlertoleranz: ![](rating_green.png) **VOLLSTÄNDIG** 

Gesamtbewertung: ![](rating_yellow.png) **WEITGEHEND** 
Da wir pro Konzept immer nur einen Treiber hatten und bei Konzept 2 (Fehlertoleranz) alles versändlich war, haben wir hier keine weitere Begründung. Bei Konzept 1 sollten unsere Anmerkungen jedoch überdacht werden.

---

## Empfehlungen/Auffälligkeiten
- Ist das Dokument wirklich nur für die Entwicklungsteams oder auch für den Nutzer? ( 1.5 Ziele des Dokuments) —> es wird ein weiteres Dokument für Nutzer erstellt 
- Treiber V01 —> Qualitätsattribut Stimulus unklar ? (3.2 Treiber ) —> 40 stunden Woche mal 52 Wochen
- Zweimal V01 als ID 
- Treiber B02 —> maximaler start der app nur für den Start oder auch das herunterladen (3.2 Treiber) —> beides Integriert, der erste Strat mit dem Herunterladen 

---

## Empfehlungen/Auffälligkeiten
- Treiber B01 / F01/ D01 usw. —> Quantifizierungen gehören eher zu Beschreibung der Umgebung 
- Wieso wurden diese Alternativen verworfen? GitHub, AWS Code Commit und Beanstalk (4.4 Code Orga) —> das stimmt, das könnte man hinzufügen
- Was sind die Gründe das sich die Firma gegen die Alternativen entschieden hat? 1&1 IONOS, PureHost, HostEurope, webgo (4.6 Technologien) —> das stimmt, das könnte man hinzufügen
- Bei den externen API genauer auf Kosten Ringehen —> das stimmt
