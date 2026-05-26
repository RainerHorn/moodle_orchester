# Moodle Kurs Builder — Paperclip Company

## Import

```bash
npx companies.sh add ./moodle-kurs-builder
```

oder:

```bash
pnpm paperclipai company import \
  --from ./moodle-kurs-builder \
  --target new \
  --new-company-name "Moodle Kurs Builder" \
  --include company,agents
```

## Agenten (8)

| Agent | Ebene | Aufgabe |
|---|---|---|
| Chief Orchestrator | CEO | Gesamtsteuerung, Freigaben, Koordination |
| QA Director | Director | Qualitaetspruefung, Vetorecht, Freigabe |
| Curriculum Designer | Specialist | Modulstruktur, Lernziele, Kompetenzraster |
| Didaktik Designer | Specialist | Lernpfad, Aktivierung, Modulablauf |
| Gamification Designer | Specialist | XP, Badges, Freischaltlogik |
| Content Producer | Specialist | Texte, Story, Aufgaben, Beispiele |
| Assessment Engineer | Specialist | Quiz, Feedback, Bewertungsraster |
| Moodle Builder | Specialist | Moodle-Aktivitaeten, Completion, Mapping |

## Workflows

1. **Kurs neu entwerfen** — Orchestrator → Curriculum → Didaktik → Gamification → Content + Assessment → Moodle Builder → QA
2. **Einzelmodul** — Orchestrator → Didaktik → Content + Assessment → Moodle Builder → QA
3. **Quizpaket** — Orchestrator → Curriculum → Assessment → QA → Moodle Builder
4. **Browser-Assist** — Orchestrator → Moodle Builder → QA → Browser-Assist

## Skills (8)

- course-planning
- module-blueprint
- content-production
- quiz-generation
- gamification-setup
- moodle-mapping
- qa-review
- browser-assist