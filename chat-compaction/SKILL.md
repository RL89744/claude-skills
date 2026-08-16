---
name: chat-compaction
description: Komprimiert den aktuellen Chat zu einem strukturierten Handover-Block, mit dem der User in einem neuen Chat tokensparend weiterarbeiten kann. Triggert IMMER bei "/compact", "/komprimieren", "komprimier den chat", "kompaktiere", "fasse den chat zusammen für neuen chat", "handover", "chat-übergabe", "übergebe den chat", "neuer chat fortsetzen", "context komprimieren", "token sparen chat", oder wenn der User signalisiert dass der Chat zu lang wird / das Limit nahe ist. Emuliert das serverseitige Compaction-Feature der Claude API für die Consumer-App. Nicht für: einfache Zusammenfassungen ("fasse zusammen") ohne Handover-Absicht.
---

# Chat Compaction (Handover für neuen Chat)

## Zweck

Das echte Compaction-Feature von Claude läuft serverseitig in der API und löscht alte Nachrichten physisch aus dem Kontext. In claude.ai geht das nicht — der Skill kann den laufenden Chat nicht verkleinern. Stattdessen erzeugt dieser Skill einen **Handover-Block**, den der User in einen **neuen Chat** kopiert. Dort startet Claude dann mit minimalem Kontext und der User spart Tokens / kommt langsamer ans Limit.

**Wichtig dem User gegenüber transparent machen** (einmal, kurz): Der Block muss in einen neuen Chat kopiert werden, sonst spart er nichts.

## Trigger

- Slash-artige Befehle: `/compact`, `/komprimieren`, `/handover`
- Natürliche Sprache: "komprimier den chat", "übergib das in nen neuen chat", "chat wird zu lang", "context komprimieren", "token sparen"

## Output-Format

Genau **ein** Markdown-Codeblock (damit der User ihn sauber per Copy-Button greifen kann), darin folgende Struktur. Keine Einleitungs- oder Schlussfloskeln um den Block herum außer einem einzigen Satz davor ("Hier dein Handover — füg das als erste Nachricht in einen neuen Chat ein:") und einem einzigen Satz danach mit dem Hinweis auf den neuen Chat.

````markdown
# Chat-Handover

## Kontext & Aufgabe
Worum geht es im Chat — in 2-4 Sätzen. Was ist das übergeordnete Ziel?

## Aktueller Stand
Wo stehen wir konkret? Was wurde bereits erledigt / entschieden / verworfen?
Stichpunkte, knapp.

## Wichtige Entscheidungen & Constraints
- Entscheidungen, die getroffen wurden und im neuen Chat NICHT erneut diskutiert werden sollen
- Vorgaben des Users (Tonalität, Format, technische Constraints)
- Sackgassen, die schon ausgeschlossen wurden

## Artefakte / Code / Daten
Code-Snippets, Datenstrukturen, URLs, Dateinamen, exakte Werte/Zahlen, die im neuen Chat verfügbar sein müssen. Verbatim übernehmen — keine Paraphrase. Bei längerem Code: vollständig einfügen, nicht kürzen.

## Offene Punkte / nächste Schritte
1. Konkret: Was ist der nächste Schritt?
2. ...
3. ...

## Bevorzugte Arbeitsweise des Users
Falls aus dem Chat klare Präferenzen hervorgehen (Sprache, Stil, Detailgrad, Tools), kurz festhalten. Nur wenn relevant.

## Erste Aktion im neuen Chat
Eine konkrete Anweisung an den neuen Claude, womit er starten soll.
````

## Regeln für die Erstellung

1. **Keine Höflichkeitsfloskeln im Block.** Der Block ist Maschinenfutter für den nächsten Claude.
2. **Code, Zahlen, Namen, URLs verbatim** — nie zusammenfassen oder paraphrasieren. Wenn der User im Chat eine Funktion geschrieben hat, kommt sie 1:1 rein.
3. **Aggressiv kürzen bei Diskussion und Reasoning** — nur das Ergebnis zählt, nicht der Weg dahin. Verworfene Optionen nur erwähnen, wenn sie eine Sackgasse markieren.
4. **Sektionen weglassen, wenn leer.** Lieber 4 dichte Sektionen als 7 mit "n/a".
5. **Sprache des Chats übernehmen** (meistens Deutsch bei diesem User). Der Handover ist in der Sprache, in der der Chat geführt wurde.
6. **Keine Memory-Inhalte einbauen**, die nicht im Chat selbst vorkamen — der neue Chat hat eigenen Memory-Zugriff.
7. **Länge-Ziel:** so kurz wie möglich, so lang wie nötig. Faustregel: 10-30% der ursprünglichen Chatlänge. Bei sehr code-/daten-lastigen Chats darf es länger werden, weil Verbatim-Material nicht gekürzt wird.

## Format der Antwort

```
Hier dein Handover — füg das als erste Nachricht in einen neuen Chat ein:

[CODEBLOCK MIT HANDOVER]

Tipp: Im neuen Chat wird das gesamte bisherige Hin und Her durch diesen Block ersetzt — Tokens werden also tatsächlich gespart, sobald du dort weitermachst statt hier.
```

Nichts weiter. Keine Nachfragen, keine zusätzlichen Erklärungen, keine "Soll ich noch X hinzufügen?"-Schleifen. Wenn der User Anpassungen will, sagt er's.
