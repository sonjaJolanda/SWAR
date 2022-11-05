# Kleine Übersicht über Markdown

Hier wollen wir ein bisschen Markdown lernen. 

## Das ist eine Überschrift der Ebene 2

Das ist **fett**, *kursiv* und ~durchgestrichen~. Außerdem kann man so `Text in Festbreitenschrift` darstellen oder als ganzer Block über

```
Das hier bleibt so.
    auch mit Leerzeichen am Anfang
    und *Sternchen*
```

Code kann man durch Angabe der Sprache farblich hervorheben:

```java
public class Hello {
  public static void main(String[] args) {
    System.out.println("Hello SWAR!");
  }
}
```

Listen gehen so:

* So macht man Bullet-Points
* noch einer
* und noch einer

So macht man eine Liste mit Nummerierung:

1. ein Punkt
2. noch ein Punkt
3. der letzte

Man kann auch Dinge verlinken, z.B. die [HTWG](https://www.htwg-konstanz.de).

Aber auch [andere Dokumente](Allgemein.md).

Man kann auch Bilder aus dem Web einbinden:

![Gantt-Diagramm](https://www.htwg-konstanz.de/fileadmin/pub/allgemein/Bilder/Bilder_Quadrate_490x490px/490x490px_Studium-u-Forschung/010067_WIN_WEB_490x490.jpg)

Unterstützt werden JPG, PNG und SVG.

<!-- Das hier ist ein Kommentar, der hinterher nicht dargestellt wird. Praktisch für Anmerkungen beim Korrekturlesen, etc. -->

### Tabellen

Bei Tabellen handelt es sich um eine Erweiterung, die aber auch von GitLab und GitHub unterstützt wird.

Überschrift 1  | Überschrift 2 | Überschrift 3 |
---------------|---------------|---------------|
erste Zeile    | Hier steht was| Lorem ipsum dolor sit amet.
zweite Zeile   | und hier auch | Lorem ipsum dolor sit amet, consetetur.