# Skill: Quiz Generation (Moodle XML)

## Zweck

Generierung Moodle-kompatibler Quizfragen fuer handlungsorientierte
Lernsituationen nach SchuCu-BBS 2024.

***

## Fragetypen und Standards

| Typ | Einsatz | Optionen | Feedback |
|---|---|---|---|
| Multiple Choice | Fachkompetenz pruefen | mind. 4 | Je Option + allgemein |
| Richtig/Falsch | Nur eindeutige Sachverhalte | 2 | Je Option |
| Lueckentext | Fachbegriffe aus Fachkompetenz | - | Allgemein |
| Kurzantwort | Offene Fachfragen | Musterloesung | Bewertungshinweis |

- Min. 5 Fragen je Lernsituations-Quiz
- ID-Schema: `[LS-Nr]-[Phasenkuerzel]-[Nr]` z.B. `LS02-INFO-01`

***

## Phasenkuerzel

| Phase | Kuerzel |
|---|---|
| Informieren/Analysieren | INFO |
| Planen | PLAN |
| Entscheiden | ENT |
| Durchfuehren | DURCH |
| Ueberprufen/Kontrollieren | PRUEF |
| Reflektieren | REFL |

***

## LLM-Prompt: Quizfragen generieren

Vorlage zum Kopieren:

    Erstelle 5 Multiple-Choice-Fragen fuer Phase [Phasenname]
    der Lernsituation [Titel].

    Handlungskompetenz Fach:
      Wissen:       [Liste aus Lernsituations-Blueprint]
      Fertigkeiten: [Liste aus Lernsituations-Blueprint]

    Anforderungen:
    - 4 Antwortoptionen, 1 eindeutig korrekt
    - Distraktoren plausibel, keine offensichtlich falschen Aussagen
    - Feedback je Option: 1-2 Saetze (warum richtig / warum falsch)
    - Allgemeines Feedback: vollstaendige Erklaerung der richtigen Loesung
    - Sprache: zielgruppengerecht, eindeutig, kein Doppelsinn
    - Ausgabe: vollstaendiges Moodle XML (4.x), direkt importierbar
    - ID-Schema: [LS-Nr]-[Phasenkuerzel]-01 bis 05

***

## Moodle XML Referenz-Template

**Dateiname:** `quiz-ls[nr].xml`

**Import-Pfad:** Kurs > Mehr > Fragensammlung > Import > Format: Moodle XML

### 1. Datei-Rahmen

```xml
<?xml version="1.0" encoding="UTF-8"?>
<quiz>

  <!-- Fragen als question-Elemente hier einfuegen -->

</quiz>
```

### 2. Multiple Choice

```xml
<question type="multichoice">
  <name><text>LS01-PRUEF-01</text></name>
  <questiontext format="html">
    <text><![CDATA[<p>Fragetext einfuegen.</p>]]></text>
  </questiontext>
  <generalfeedback format="html">
    <text><![CDATA[<p>Vollstaendige Erklaerung der richtigen Loesung.</p>]]></text>
  </generalfeedback>
  <defaultgrade>1</defaultgrade>
  <penalty>0.3333333</penalty>
  <hidden>0</hidden>
  <single>true</single>
  <shuffleanswers>1</shuffleanswers>
  <answernumbering>abc</answernumbering>

  <answer fraction="100" format="html">
    <text><![CDATA[<p>Richtige Antwort</p>]]></text>
    <feedback format="html">
      <text><![CDATA[<p>Richtig. Begruendung warum korrekt.</p>]]></text>
    </feedback>
  </answer>

  <answer fraction="0" format="html">
    <text><![CDATA[<p>Falsche Antwort 1</p>]]></text>
    <feedback format="html">
      <text><![CDATA[<p>Falsch. Erklaerung warum diese Option nicht korrekt ist.</p>]]></text>
    </feedback>
  </answer>

  <answer fraction="0" format="html">
    <text><![CDATA[<p>Falsche Antwort 2</p>]]></text>
    <feedback format="html">
      <text><![CDATA[<p>Falsch. Erklaerung warum diese Option nicht korrekt ist.</p>]]></text>
    </feedback>
  </answer>

  <answer fraction="0" format="html">
    <text><![CDATA[<p>Falsche Antwort 3</p>]]></text>
    <feedback format="html">
      <text><![CDATA[<p>Falsch. Erklaerung warum diese Option nicht korrekt ist.</p>]]></text>
    </feedback>
  </answer>

</question>
```

### 3. Richtig / Falsch

```xml
<question type="truefalse">
  <name><text>LS01-PRUEF-02</text></name>
  <questiontext format="html">
    <text><![CDATA[<p>Aussage, die bewertet werden soll.</p>]]></text>
  </questiontext>
  <generalfeedback format="html">
    <text><![CDATA[<p>Erklaerung der richtigen Loesung.</p>]]></text>
  </generalfeedback>
  <answer fraction="100">
    <text>true</text>
    <feedback format="html">
      <text><![CDATA[<p>Richtig. Begruendung.</p>]]></text>
    </feedback>
  </answer>
  <answer fraction="0">
    <text>false</text>
    <feedback format="html">
      <text><![CDATA[<p>Falsch. Begruendung.</p>]]></text>
    </feedback>
  </answer>
</question>
```

### 4. Kurzantwort

```xml
<question type="shortanswer">
  <name><text>LS01-REFL-01</text></name>
  <questiontext format="html">
    <text><![CDATA[<p>Offene Fachfrage hier einfuegen.</p>]]></text>
  </questiontext>
  <generalfeedback format="html">
    <text><![CDATA[<p>Musterantwort und Bewertungshinweis fuer Lehrkraft.</p>]]></text>
  </generalfeedback>
  <usecase>0</usecase>
  <answer fraction="100">
    <text>Musterloesung</text>
    <feedback format="html">
      <text><![CDATA[<p>Richtig. Hinweis zum Bewertungsspielraum.</p>]]></text>
    </feedback>
  </answer>
</question>
```

***

## Qualitaets-Checkliste je Fragensatz

- [ ] Fragen beziehen sich auf Handlungskompetenz (nicht auf Trivialwissen)
- [ ] Distraktoren plausibel und fachlich korrekt formuliert
- [ ] Feedback je Option vorhanden (nicht nur richtig/falsch)
- [ ] Allgemeines Feedback erklaert die vollstaendige Loesung
- [ ] ID-Schema eingehalten: [LS-Nr]-[Phasenkuerzel]-[Nr]
- [ ] Min. 5 Fragen je Lernsituation
- [ ] Phasen gleichmaessig beruecksichtigt (nicht nur PRUEF)
- [ ] XML valide: mit Moodle-Import-Tool geprueft
- [ ] Kategorie im Import korrekt gesetzt: [Kursname]/[LS-Titel]