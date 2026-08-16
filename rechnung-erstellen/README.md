# rechnung-erstellen
<img width="1440" height="260" alt="Design ohne Titel (4)" src="https://github.com/user-attachments/assets/d47fea75-248b-4612-8414-814e8cbd9170" />

Ein Claude Skill, der aus wenigen Angaben (Empfänger, Leistung, Betrag) eine
saubere, nach deutschem Recht (§14 UStG) vollständige PDF-Rechnung erzeugt —
ohne Vorlage, ohne zusätzliche Software.

Deckt ab: Kleinunternehmer (§19 UStG), Reverse Charge bei B2B-EU-Ausland,
korrekte Pflichtangaben, deutsches Zahlen- und Datumsformat.

## Installation

**Claude Code / Claude Agent SDK (lokal):**
```bash
mkdir -p ~/.claude/skills/rechnung-erstellen
cp SKILL.md ~/.claude/skills/rechnung-erstellen/
```

**Cowork / claude.ai:**
Die `.skill`-Datei (Zip-Archiv aus `SKILL.md`) im Chat hochladen — Claude bietet
dann an, sie als Skill zu speichern.

## Verwendung

Einfach im Chat: *"Erstelle eine Rechnung an [Kunde] über [Leistung] für [Betrag]."*
Der Skill fragt nur nach, wenn Empfänger oder Beträge fehlen. Eigene
Geschäftsdaten (Anschrift, Steuernummer, IBAN) am besten einmal in einer
Projektnotiz (z. B. `CLAUDE.md`) hinterlegen, damit sie nicht jedes Mal neu
angegeben werden müssen.

## Hinweis

Dieser Skill ersetzt keine Steuerberatung. Für komplexere Fälle (z. B.
innergemeinschaftliche Lieferungen, Bauleistungen mit §13b UStG) zusätzlich
fachlichen Rat einholen.

## Lizenz

MIT — siehe [LICENSE](LICENSE).
