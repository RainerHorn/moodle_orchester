# Skill: Quiz Generation (Moodle XML)

## Zweck
Generierung von Moodle-kompatiblen Quizfragen nach SchuCu-BBS 2024.

## Fragen-Standards
- Bezug zur Handlungskompetenz (Fach + Personal)
- Phasenzuordnung (welche Handlungsphase wird geprueft?)
- Feedback je Antwort (nicht nur richtig/falsch)
- Sprache: zielgruppengerecht, eindeutig

## Fragetypen

### Multiple Choice (bevorzugt)
- 4 Optionen, 1 klar richtig
- Falsche Optionen: plausible Distraktoren, keine Nonsens-Antworten
- Feedback: Begruendung warum richtig/falsch

### Lueckentext
- Fachbegriffe aus Handlungskompetenz Fachkompetenz
- Kein willkuerliches Ausblenden

### Kurzantwort
- Offene Fachfrage
- Musterloesung mit Bewertungshinweis

## Moodle XML Vorlage

```xml
<?xml version="1.0" encoding="UTF-8"?>
<quiz>
  <question type="multichoice">
    <name><text>[Frage-ID: LS-Nr. + Phase + Nr.]</text></name>
    <questiontext format="html">
      <text><![CDATA[<p>[Fragetext]</p>]]></text>
    </questiontext>
    <generalfeedback format="html">
      <text><![CDATA[<p>[Allgemeines Feedback]</p>]]></text>
    </generalfeedback>
    <answer fraction="100" format="html">
      <text><![CDATA[<p>[Richtige Antwort]</p>]]></text>
      <feedback format="html">
        <text><![CDATA[<p>[Warum richtig]</p>]]></text>
      </feedback>