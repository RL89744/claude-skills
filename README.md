## claude-skills
<img width="3840" height="2160" alt="siednji-leon-37DAG6YAqWk-unsplash" src="https://github.com/user-attachments/assets/a45eb453-bfa8-4731-a4ce-29c1e124adea" />

Eine Sammlung von [Claude Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) —
wiederverwendbare Anleitungen, die Claude (Claude Code, Claude Agent SDK,
Cowork, claude.ai) bei bestimmten Aufgaben triggert und konsequent nach
demselben Ablauf abarbeiten lässt.

## Skills in diesem Repo

### Geschäft und Recht

| Skill | Zweck |
|---|---|
| [`rechnung-erstellen`](rechnung-erstellen/) | Rechtskonforme PDF-Rechnung (§14 UStG) aus wenigen Angaben erzeugen, Kleinunternehmer und Reverse Charge inklusive |
| [`vertrag-pruefen`](vertrag-pruefen/) | Verträge und AGB analysieren, problematische Klauseln markieren, klare Empfehlung zur Unterzeichnung |
| [`werkverkauf-erfassen`](werkverkauf-erfassen/) | Verkauf eines Kunstwerks im bestehenden Werkkatalog erfassen, Preis vorschlagen, Daten für eine Rechnung vorbereiten |

### Text und Recherche

| Skill | Zweck |
|---|---|
| [`ki-spuren-entfernen`](ki-spuren-entfernen/) | Deutschen Texten die typischen KI-Muster austreiben, 23 katalogisierte Tells mit Beispiel und Alternative |
| [`schnellrecherche`](schnellrecherche/) | Ein Thema aus mehreren Quellen prüfen und als kompakten, belegten Überblick ausgeben, Widersprüche inklusive |

### Chat und Wissen

| Skill | Zweck |
|---|---|
| [`chat-compaction`](chat-compaction/) | Langen Chat zu einem Handover-Block verdichten, der in einem neuen Chat tokensparend weiterläuft |
| [`chat-in-obsidian-speichern`](chat-in-obsidian-speichern/) | Den laufenden Chat als strukturierte Notiz im Obsidian-Vault ablegen, Entscheidungen und offene Punkte statt Volltranskript |
| [`modell-wahl`](modell-wahl/) | Empfiehlt Haiku, Sonnet oder Opus für die anstehende Aufgabe und benennt die Kostenfaktoren, die schwerer wiegen als die Modellwahl |

Alle Skills sind deutschsprachig.

Jeder Ordner enthält eine `SKILL.md` (die eigentliche Anleitung, die Claude
lädt) und eine eigene `README.md` mit Installations- und Verwendungshinweisen.
Manche Skills bringen zusätzlich einen Ordner `references/` mit ausgelagerten
Details mit, den Claude erst bei Bedarf nachlädt.

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
Steuer- und Vertragsrecht, deutsche Zahlen-/Datumsformate, deutsche
Sprachmuster). Sie ersetzen keine Steuer- oder Rechtsberatung.

Einzelne Skills verweisen aufeinander oder auf Skills, die nicht Teil dieses
Repos sind. Die jeweilige `README.md` sagt im Abschnitt *Konfiguration*, was
vor der ersten Nutzung angepasst werden muss.
