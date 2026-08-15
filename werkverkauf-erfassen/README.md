# werkverkauf-erfassen

Ein Claude Skill für Künstler:innen, Fotograf:innen und andere, die
Originale oder limitierte Editionen verkaufen und dafür bereits eine Art
Werkkatalog führen (Obsidian, Markdown-Tabellen, CSV — egal welches Format).

Der Skill deckt genau die Lücke ab, die zwischen Produktions-/Content-Tracking
und Buchhaltung meistens klafft: ein Werk wird verkauft, aber "verkauft"
ist im Katalog gar kein vorgesehener Status, der Preis steht nirgendwo, und
die Rechnung wird von Hand aus dem Kopf zusammengetippt.

`werkverkauf-erfassen` liest zuerst dein bestehendes Katalogschema (Spalten,
Statuswerte, ID-Format), ergänzt es um Verkaufsstatus, Preis, Käufer,
Verkaufsdatum und Zahlungsstatus — ohne dein System zu überschreiben oder zu
duplizieren — schlägt bei Bedarf einen nachvollziehbaren Preis vor
(Fläche × Faktor, abgeleitet aus deinen eigenen Vergleichsverkäufen) und
bereitet die Daten so auf, dass ein Rechnungs-Skill sie direkt übernehmen
kann.

## Warum das ein eigener Skill ist, kein Teil des Katalog-Skills

Katalog-/Produktionspflege und Verkaufsabwicklung sind unterschiedliche
Momente im Workflow und meist auch unterschiedliche Personen (Künstler:in vs.
Galerie/Kund:in). Ein eigener, schmaler Skill triggert zuverlässiger als ein
Skill, der "alles rund ums Werk" machen soll.

## Installation

**Claude Code / Claude Agent SDK (lokal):**
```bash
mkdir -p ~/.claude/skills/werkverkauf-erfassen
cp SKILL.md ~/.claude/skills/werkverkauf-erfassen/
```

**Cowork / claude.ai:**
Die `.skill`-Datei (Zip-Archiv aus `SKILL.md`) im Chat hochladen — Claude
bietet dann an, sie als Skill zu speichern.

## Verwendung

Voraussetzung: irgendein bestehender Werkkatalog (auch ein einfacher). Dann
im Chat z. B.:

- *"CASTILLO DEL MAR ist verkauft an Familie Meier für 2.400 €."*
- *"Was sollte CAMBER kosten?"*
- *"Verkauf erfassen: [Werk], [Käufer], [Preis]."*

Beim ersten Einsatz fragt der Skill nach Basispreis/Faktor, falls noch keine
Vergleichsverkäufe im Katalog stehen — danach merkt er sich das über eine
kleine Konfig-Notiz im Katalogordner.

## Lizenz

MIT — siehe [LICENSE](LICENSE).
