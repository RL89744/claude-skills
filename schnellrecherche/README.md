# schnellrecherche

Ein Claude Skill für den kurzen Rechercheauftrag: ein Thema aus mehreren
Quellen prüfen und als kompakten, belegten Überblick ausgeben. Ergebnis bleibt
im Chat, kein Dokument, in zwei Minuten lesbar.

Deckt ab: Zusammenfassung, Kernpunkte mit Beleg, Kosten und Preise, Stärken,
Schwächen, ehrliche Einschätzung, Quellenliste.

## Wozu

Zwischen "kurz nachgeschlagen" und "ausführlicher Bericht" fehlt meistens die
Mitte. Dieser Skill besetzt sie: genug Struktur, um eine Entscheidung zu
tragen, wenig genug Umfang, um sie noch am selben Tag zu treffen.

Drei Regeln machen den Unterschied zur beliebigen Websuche:

- **Mindestens drei bis fünf verschiedene Quellentypen**, nicht nur die
  Herstellerseite. Offizielle Angaben, Nachrichten, Community-Diskussionen,
  Preisseiten, Vergleichstests.
- **Widersprüche bleiben stehen.** Wenn Quellen sich uneins sind, wird das
  vermerkt statt stillschweigend zugunsten der plausibelsten Version aufgelöst.
- **Keine erfundenen Zahlen.** Marktanteile, Prozentsätze und Preise ohne Quelle
  werden nicht geschätzt, sondern als "keine belastbare Zahl gefunden"
  ausgewiesen.

Dazu kommt ein Zeitstempel bei allem, was schnell veraltet, und eine
Lebendigkeitsprüfung bei Tools. Ein Produkt, das seit zwei Jahren nicht mehr
weiterentwickelt wird, taugt nicht als Empfehlung.

## Installation

**Claude Code / Claude Agent SDK (lokal):**

```bash
mkdir -p ~/.claude/skills/schnellrecherche
cp SKILL.md ~/.claude/skills/schnellrecherche/
```

**Cowork / claude.ai:**

`SKILL.md` als `.skill`-Datei (ZIP-Archiv) packen und im Chat hochladen. Claude
bietet dann an, sie als Skill zu speichern.

```bash
zip -r schnellrecherche.skill schnellrecherche/
```

Der Skill braucht eine Websuche-Funktion in der jeweiligen Umgebung. Ohne die
kann er nur aus dem Trainingswissen antworten, was genau das ist, was er
vermeiden soll.

## Verwendung

*"Kurz recherchieren: [Thema]"*, *"schnell checken ob [Tool] was taugt"*,
*"gib mir einen Überblick zu [X]"*, *"[X] vs. [Y]"*, *"was ist der Stand bei
[Thema]"*.

Der Skill entscheidet je nach Frage zwischen Kurzantwort (zwei bis drei
Absätze), Vergleich (Gegenüberstellung) und kompaktem Überblick (Standard).

## Abgrenzung

Nicht für normale Wissensfragen im Gesprächsverlauf. *"Was weißt du über X"*
gehört direkt beantwortet, notfalls mit einer einzelnen Suche, aber ohne
Berichtsformat.

Nicht für Deep Dives. Sobald Tiefe oder ein gespeichertes Dokument verlangt
wird, ist ein ausführlicher Recherche-Skill der richtige Ort. Die `SKILL.md`
verweist an mehreren Stellen auf einen Skill namens `recherche-bericht`, der
nicht Teil dieses Repos ist. Wer ihn nicht hat, ersetzt den Verweis durch das
eigene Pendant oder streicht ihn.

## Konfiguration

Keine, abgesehen vom optionalen Verweis auf einen Deep-Dive-Skill (siehe oben).

## Lizenz

MIT — siehe [LICENSE](../LICENSE).
