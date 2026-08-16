---
name: chat-in-obsidian-speichern
description: Den laufenden Chat als strukturierte Notiz im Obsidian-Vault unter Chats/ ablegen. Aktivieren bei "/chat-in-obsidian-speichern", "speicher den Chat", "Chat in Obsidian sichern", "Chat-Log anlegen", "das Gespräch im Vault ablegen", "sichere die Session", "Chat-Backup", "pack das in den Vault" oder wenn am Ende einer Session festgehalten werden soll, was besprochen und entschieden wurde. NICHT für die Kompaktierung eines Chats zur Fortsetzung in einem neuen Fenster und nicht für inhaltliche Fachnotizen, die an ihren Sachort im Vault gehören.
---

# Chat in Obsidian speichern

Schreibt den aktuellen Chat als strukturierte Notiz nach `Chats/YYYY-MM-DD_Kurztitel.md`
im Vault. Kein Volltranskript, sondern eine lesbare Zusammenfassung, die in sechs
Monaten noch verständlich ist.

## Konfiguration

Vor der ersten Nutzung anpassen:

```
VAULT   = /Pfad/zu/deinem/Obsidian-Vault
ORDNER  = Chats
```

Ist der Pfad nicht gesetzt, einmal danach fragen und den User bitten, ihn hier
einzutragen, statt bei jedem Aufruf erneut zu fragen.

## Ablauf

### 1. Datum bestimmen

Nie aus dem Kontext raten, sondern `date +%F` ausführen. Bei Sessions über Mitternacht
gilt das Datum des Session-Beginns, falls der User nichts anderes sagt.

### 2. Vault-Zugriff herstellen

Je nach Laufzeitumgebung unterschiedlich. In dieser Reihenfolge probieren, beim ersten
Erfolg aufhören:

1. **Direkt** — `Read`/`Write` auf den Vault-Pfad. Der Normalfall für Claude Code und
   lokal laufende Sessions.
2. **Über eine Datei-Bridge** — läuft die Session in einer Cloud-Sandbox (z. B. Cowork
   im Cloud-Modus), den Vault über die verfügbaren Device-Tools ansprechen und den
   Ordner bei Bedarf einmal anfordern.
3. **Kein Zugriff** — Notiz trotzdem bauen, als Datei ausliefern und in einem Satz
   sagen, wohin sie im Vault gehört. Nicht mehrfach retryen.

### 3. Titel bilden

`YYYY-MM-DD_Kurztitel.md`, Kurztitel in Title-Case mit Bindestrichen statt Leerzeichen,
zwei bis fünf Wörter, benennt die Sache und nicht die Tätigkeit.

Gut: `2026-08-16_Backup-Strategie-und-Rsync-Fehler.md`
Schlecht: `2026-08-16_Chat.md`, `2026-08-16_Wir-haben-ueber-Backups-gesprochen.md`

Umlaute und Sonderzeichen im Dateinamen vermeiden (`ue`, `oe`, `ae`, kein `/`, `:`, `>`),
in der Überschrift sind sie erlaubt.

### 4. Duplikat prüfen, vor dem Schreiben

Zielordner auf Dateien mit dem heutigen Datum durchsehen.

- **Gleiches Thema, gleicher Tag:** bestehende Notiz nicht überschreiben, sondern einen
  Abschnitt `## Nachtrag — <Stichwort>` anhängen und `updated:` im Frontmatter
  hochsetzen. Offene Punkte oben zusammenführen statt doppelt zu führen.
- **Anderes Thema, gleicher Tag:** neue Datei mit anderem Kurztitel.
- **Namenskollision bei identischem Titel:** `-2`, `-3` anhängen.

Nie eine bestehende Notiz überschreiben. Im Zweifel anhängen.

### 5. Notiz schreiben

Struktur und Frontmatter siehe `references/vorlage.md`.

Beim Schreiben über eine Shell Python statt `echo`/`cat` benutzen, sonst zerlegt die
Shell den Markdown-Inhalt an Backticks, Anführungszeichen und `$`:

```bash
python3 - <<'PYEOF'
from pathlib import Path
p = Path("/Pfad/zum/Vault/Chats/DATEINAME.md")
p.write_text("""...Inhalt...""", encoding="utf-8")
print("geschrieben:", p)
PYEOF
```

Enthält der Text selbst `"""`, stattdessen die Notiz erst lokal anlegen und die Datei
dann an ihren Zielort kopieren.

### 6. Bestätigen

Ein bis zwei Sätze: Dateiname, ob neu angelegt oder ergänzt, Zahl der offenen Punkte.
Den Inhalt der Notiz nicht nochmal im Chat wiederholen, er steht ja drin.

## Was reinkommt

Entscheidungen und ihre Begründung. Was tatsächlich umgesetzt wurde, mit Datei- und
Notiznamen. Verworfene Ansätze samt Grund, denn der ist später mehr wert als das
Ergebnis. Offene Punkte als Checkboxen.

## Was draußen bleibt

Höflichkeitsfloskeln und der Gesprächsverlauf als solcher. Vollständige Code-Blöcke,
Prompts oder Textentwürfe, die schon woanders im Vault liegen, stattdessen verlinken.
Zwischenstände, die im selben Chat wieder überholt wurden, außer die Korrektur selbst
ist die Pointe. Secrets, Tokens, Passwörter und API-Keys gehören nie in den Vault,
stattdessen ein Hinweis wie "Token erzeugt, muss widerrufen werden".

## Verlinkung statt Duplikation

Betrifft die Session ein bestehendes Projekt oder eine bestehende Notiz, im
`links:`-Feld und im Text als `[[Wikilink]]` darauf verweisen. Vorher prüfen, dass die
Zielnotiz wirklich so heißt. Tote Wikilinks sind schlimmer als keine.

Ist in der Session etwas mit eigenständigem Wiederverwendungswert entstanden, etwa ein
Recherche-Ergebnis, ein Kontakt oder eine Entscheidungsgrundlage, gehört das als eigene
Notiz an seinen Sachort im Vault. Die Chat-Notiz verlinkt dann nur darauf.

## Qualitätscheck vor der Rückmeldung

- [ ] Datum per `date` geholt, nicht geraten
- [ ] Frontmatter vollständig, `created` und `updated` gesetzt
- [ ] Tags folgen der im Vault etablierten Taxonomie
- [ ] alle Wikilinks zeigen auf existierende Notizen
- [ ] keine Secrets im Text
- [ ] offene Punkte sind Checkboxen, keine Fließtext-Absichtserklärungen
- [ ] Datei liegt wirklich im Vault, nachgelesen statt angenommen
