# vertrag-pruefen

Ein Claude Skill, der Verträge, AGB und andere juristische Dokumente
analysiert: Juristensprache wird in verständliches Deutsch übersetzt,
problematische Klauseln werden markiert, und am Ende steht eine klare
Empfehlung — unterschreiben, nachverhandeln oder ablehnen.

Enthält vertragsartspezifische Prüfpunkte für Freelance-/Werkverträge, NDAs,
Arbeitsverträge, Mietverträge und SaaS-Nutzungsbedingungen (deutsches Recht,
u. a. AGB-Kontrolle nach §§305 ff. BGB).

## Installation

**Claude Code / Claude Agent SDK (lokal):**
```bash
mkdir -p ~/.claude/skills/vertrag-pruefen
cp SKILL.md ~/.claude/skills/vertrag-pruefen/
```

**Cowork / claude.ai:**
Die `.skill`-Datei (Zip-Archiv aus `SKILL.md`) im Chat hochladen — Claude bietet
dann an, sie als Skill zu speichern.

## Verwendung

Vertragstext einfügen, PDF/Word-Datei hochladen oder Screenshot einfügen und
fragen: *"Prüfe diesen Vertrag"* oder *"Soll ich das unterschreiben?"*

## Hinweis

Das ist keine Rechtsberatung. Bei wichtigen Verträgen (Arbeitsvertrag,
größere Aufträge, Gesellschaftsverträge) zusätzlich eine Anwältin oder einen
Anwalt einbeziehen. Der Skill hilft beim Verstehen und beim Vorbereiten der
richtigen Nachfragen.

## Lizenz

MIT — siehe [LICENSE](LICENSE).
