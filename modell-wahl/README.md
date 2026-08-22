# modell-wahl

Ein Claude Skill, der empfiehlt, welches Modell — Haiku, Sonnet oder Opus —
für die anstehende Aufgabe das richtige ist. Auf Zuruf, und als knapper
Einzeiler, wenn Modell und Aufgabe erkennbar nicht zusammenpassen.

Deckt ab: eine Entscheidungsregel aus vier Fragen, eine Zuordnung nach
Aufgabentyp, die Kostenfaktoren, die tatsächlich schwerer wiegen als die
Modellwahl, und ein festes Ausgabeformat.

## Wozu

Die Faustregel lautet: das kleinste Modell nehmen, das die Aufgabe noch sicher
löst, nicht das größte, das sie besonders gut löst. In der Praxis wird sie
selten angewandt, weil die Abwägung bei jeder Aufgabe neu stattfindet und im
Zweifel das große Modell gewinnt. Dieser Skill hält die Abwägung einmal fest.

Die Entscheidung hängt an zwei Größen: was ein Fehler kostet und wie mehrdeutig
die Aufgabe ist. Alles, was mechanisch und sofort prüfbar ist, geht an Haiku.
Alles, was Recherche, Werkzeuge oder mehrere Schritte braucht, ist Sonnet-Gebiet.
Opus lohnt erst, wenn Urteilsvermögen die eigentliche Arbeit ist.

## Was der Skill nicht kann

Er schaltet das Modell nicht um. Ein Skill hat dafür kein Werkzeug — der
Wechsel läuft über `/model` und bleibt Sache des Users.

Er greift außerdem erst, wenn Claude bereits antwortet, also im laufenden
Modell. Wer Opus eine Trivialfrage stellt, hat den teuren Turn schon bezahlt,
bevor der Hinweis kommt. Der Nutzen entsteht ab der nächsten Aufgabe und in
langen Sessions, in denen früh umgeschaltet wird.

Und der unbequemste Punkt, den der Skill selbst ausspricht: die Modellwahl ist
beim Token-Sparen nicht der größte Hebel. Der Kontext ist es. Jeder Turn
schickt die komplette bisherige Unterhaltung neu, plus die Beschreibungen aller
aktiven Connectors. Ein langer Haiku-Chat kann teurer sein als ein kurzer
Opus-Chat.

## Installation

**Claude Code / Claude Agent SDK (lokal):**

```bash
mkdir -p ~/.claude/skills/modell-wahl
cp SKILL.md ~/.claude/skills/modell-wahl/
```

**Cowork / claude.ai:**

`SKILL.md` als `.skill`-Datei (ZIP-Archiv) packen und im Chat hochladen. Claude
bietet dann an, sie als Skill zu speichern.

```bash
zip -r modell-wahl.skill modell-wahl/
```

## Verwendung

Direkt fragen:

```
Welches Modell soll ich für die Vertragsprüfung nehmen?
Reicht Sonnet für die Recherche?
Wie kriege ich das billiger?
```

Antwort ist eine Zeile Empfehlung, eine Zeile Begründung, der Befehl:

```
Opus. Ein übersehenes Haftungsrisiko kostet mehr als der teurere Durchgang.
→ /model opus
```

Ungefragt meldet sich der Skill nur bei klarem Mismatch, höchstens einmal pro
Session pro Richtung, als Nachsatz am Ende einer normalen Antwort.

## Konfiguration

Der Abschnitt *Zuordnung nach Aufgabentyp* in der `SKILL.md` ist nach
Aufgabenarten sortiert, nicht nach konkreten Skills. Wer eine eigene
Skill-Sammlung betreibt, kann die eigenen Skill-Namen dort direkt eintragen —
also etwa `vertrag-pruefen` unter Opus, `schnellrecherche` unter Sonnet,
`rechnung-erstellen` unter Haiku. Die Empfehlung wird dadurch spürbar
treffsicherer.

Der Skill nennt bewusst nur Modellklassen, keine Versionsnummern. Die Nummern
wechseln mehrmals im Jahr, das Verhältnis der Klassen zueinander bleibt.
