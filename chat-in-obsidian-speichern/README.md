# chat-in-obsidian-speichern

Ein Claude Skill, der das laufende Gespräch als strukturierte Notiz in einem
Obsidian-Vault ablegt. Kein Volltranskript, sondern eine Zusammenfassung, die
in sechs Monaten noch verständlich ist: worum es ging, was umgesetzt wurde,
welche Entscheidungen gefallen sind und was offen bleibt.

Deckt ab: Ablage nach `Chats/YYYY-MM-DD_Kurztitel.md`, Obsidian-Frontmatter mit
Tag-Taxonomie, Wikilinks auf betroffene Notizen, Nachtrag statt Dublette bei
mehreren Sessions am selben Tag, Vault-Zugriff lokal wie über eine Datei-Bridge.

## Wozu

Chats sind flüchtig. Was in einer langen Session entschieden wurde, ist zwei
Wochen später nicht mehr auffindbar, und die Begründung für eine verworfene
Variante ist meist wertvoller als das Ergebnis selbst. Der Skill schreibt genau
das mit, im selben Format wie der Rest des Vaults, ohne dass man jedes Mal
erklären muss, wie die Notiz auszusehen hat.

Was bewusst draußen bleibt: Gesprächsverlauf und Floskeln, Code-Blöcke und
Entwürfe, die schon woanders im Vault liegen (die werden verlinkt), sowie
Tokens, Passwörter und andere Secrets.

## Installation

**Claude Code / Claude Agent SDK (lokal):**

```bash
mkdir -p ~/.claude/skills/chat-in-obsidian-speichern
cp -r SKILL.md references ~/.claude/skills/chat-in-obsidian-speichern/
```

**Cowork / claude.ai:**

`SKILL.md` und den Ordner `references/` als `.skill`-Datei (ZIP-Archiv) packen
und im Chat hochladen. Claude bietet dann an, sie als Skill zu speichern.

```bash
zip -r chat-in-obsidian-speichern.skill chat-in-obsidian-speichern/
```

## Konfiguration

Zwei Stellen anpassen, sonst läuft der Skill nicht sinnvoll:

1. **Vault-Pfad** in `SKILL.md`, Abschnitt *Konfiguration*:

   ```
   VAULT   = /Pfad/zu/deinem/Obsidian-Vault
   ORDNER  = Chats
   ```

2. **Tag-Taxonomie** in `references/vorlage.md`. Dort steht eine Beispiel-Tabelle
   mit `domain-*`-Tags. Die durch die eigene ersetzen, sonst erfindet Claude bei
   jedem Aufruf neue und der Vault franst aus. Wer keine Taxonomie fährt,
   streicht den Abschnitt und lässt nur freie Themen-Tags stehen.

Wer bereits eine `CLAUDE.md` im Vault hat, verweist dort auf den Skill, statt das
Notizformat ein zweites Mal zu beschreiben. Sonst driften beide Beschreibungen
auseinander.

## Verwendung

Im Chat: *"Speicher den Chat in Obsidian"*, *"Chat-Log anlegen"*, *"pack das in
den Vault"* — oder direkt `/chat-in-obsidian-speichern`.

Der Skill holt sich das Datum selbst, prüft den Zielordner auf eine bestehende
Notiz zum selben Thema am selben Tag und hängt in dem Fall einen Abschnitt
`## Nachtrag` an, statt eine zweite Datei anzulegen. Fehlt der Vault-Zugriff,
baut er die Notiz trotzdem und liefert sie als Datei aus.

## Abgrenzung

Nicht zu verwechseln mit einer Chat-Kompaktierung, die ein Gespräch für die
Fortsetzung in einem neuen Fenster verdichtet. Dieser Skill schreibt fürs Archiv,
nicht für den nächsten Kontext. Inhaltliche Fachnotizen mit eigenständigem
Wiederverwendungswert gehören ebenfalls nicht hierher, sondern an ihren Sachort
im Vault. Die Chat-Notiz verlinkt dann nur darauf.

## Hinweis

Der Skill schreibt in den Vault. Ein Vault unter Versionskontrolle oder mit
Backup ist keine schlechte Idee, bevor man einen Agenten darin schreiben lässt.

## Lizenz

MIT — siehe [LICENSE](../LICENSE).
