## Überschrift 2 claude-skills
<img width="3840" height="2160" alt="siednji-leon-37DAG6YAqWk-unsplash" src="https://github.com/user-attachments/assets/a45eb453-bfa8-4731-a4ce-29c1e124adea" />

Eine Sammlung von [Claude Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) —
wiederverwendbare Anleitungen, die Claude (Claude Code, Claude Agent SDK,
Cowork, claude.ai) bei bestimmten Aufgaben triggert und konsequent nach
demselben Ablauf abarbeiten lässt.

## Skills in diesem Repo

| Skill | Zweck | Sprache |
|---|---|---|
| [`rechnung-erstellen`](rechnung-erstellen/) | Rechtskonforme PDF-Rechnung (§14 UStG) aus wenigen Angaben erzeugen — Kleinunternehmer, Reverse Charge inklusive | Deutsch |
| [`vertrag-pruefen`](vertrag-pruefen/) | Verträge und AGB analysieren, problematische Klauseln markieren, klare Empfehlung zur Unterzeichnung | Deutsch |
| [`werkverkauf-erfassen`](werkverkauf-erfassen/) | Verkauf eines Kunstwerks im bestehenden Werkkatalog erfassen, Preis vorschlagen, Daten für eine Rechnung vorbereiten | Deutsch |

Jeder Ordner enthält eine `SKILL.md` (die eigentliche Anleitung, die Claude
lädt) und eine eigene `README.md` mit Installations- und Verwendungshinweisen.

## Installation

**Claude Code / Claude Agent SDK (lokal):**

```bash
mkdir -p ~/.claude/skills/<skill-name>
cp <skill-name>/SKILL.md ~/.claude/skills/<skill-name>/
```

Danach lädt Claude Code den Skill automatisch, sobald eine passende Anfrage
kommt (siehe `description` im Frontmatter jeder `SKILL.md`).

**Cowork / claude.ai:**

Die `SKILL.md` des gewünschten Ordners als `.skill`-Datei (ZIP-Archiv mit
`SKILL.md` als Inhalt) im Chat hochladen. Claude bietet dann an, sie zu
speichern.

## Funktionsweise eines Skills

Ein Skill besteht aus einem YAML-Frontmatter (`name`, `description`) und einer
Markdown-Anleitung. Die `description` ist der Trigger: Claude gleicht
eingehende Anfragen dagegen ab und lädt den Skill, wenn sie passt. Ein Skill
löst genau eine klar abgegrenzte Aufgabe — das macht das Triggerverhalten
vorhersehbar.

## Lizenz

MIT — siehe [LICENSE](LICENSE). Gilt für alle Skills in diesem Repo.

## Hinweis

Diese Skills sind für den deutschsprachigen Raum geschrieben (deutsches
Steuer- und Vertragsrecht, deutsche Zahlen-/Datumsformate). Sie ersetzen
keine Steuer- oder Rechtsberatung.
