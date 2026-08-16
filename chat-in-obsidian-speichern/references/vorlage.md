# Vorlage und Tag-Taxonomie

## Frontmatter

```yaml
---
type: chat-log
status: active
created: 2026-08-16
updated: 2026-08-16
tags: ['domain-system', 'status-active', 'type-chat-log', 'backup', 'rsync']
links: ['[[Server-Setup]]', '[[Backup-Strategie]]']
---
```

`created` = Datum der Session. `updated` = heute. Bei einem Nachtrag `updated`
hochsetzen und `created` unangetastet lassen.

### Tags

Immer die drei Struktur-Tags, in dieser Reihenfolge, plus zwei bis vier freie
Themen-Tags (kleingeschrieben, Bindestriche statt Leerzeichen):

1. **`domain-*`** — genau eines. Die folgende Tabelle ist ein Beispiel und **muss
   durch die eigene Taxonomie ersetzt werden**. Ohne feste Liste erfindet Claude bei
   jedem Aufruf neue Tags und der Vault franst aus.

   | Tag | Wofür |
   |---|---|
   | `domain-system` | Technik, Tooling, Automation, Setup |
   | `domain-arbeit` | Projekte, Kundenarbeit, Beruf |
   | `domain-wissen` | Recherche, Fachwissen, Hintergrund |
   | `domain-persoenlich` | Privates, Haushalt, Gesundheit |

   Passt nichts, das nächstliegende nehmen. Keine neuen `domain-*`-Tags erfinden.

   Wer keine Domain-Taxonomie fährt, streicht diesen Punkt und lässt nur die freien
   Themen-Tags stehen.

2. **`status-active`** — Standard. `status-archive` nur, wenn das Thema erledigt ist
   und nicht mehr aufgegriffen wird.

3. **`type-chat-log`** — passend zu `type: chat-log` im Kopf.

### links

Liste von Wikilinks auf betroffene Notizen. Leer lassen (`[]`), wenn es keine gibt.
Lieber leer als erfunden.

## Aufbau der Notiz

```markdown
# Chat 2026-08-16 — Kurztitel

## Worum ging's

Zwei bis vier Sätze. Die Ausgangsfrage, nicht die Antwort. Falls die Session eine
frühere fortsetzt, hier verlinken.

## Was umgesetzt wurde

Nummeriert oder als Absätze mit fetten Stichworten. Konkret: Dateinamen, Notiznamen,
Zahlen, Versionen. "Backup-Intervall von 24 h auf 6 h gesetzt, in `crontab` fest
eingetragen" statt "Backup angepasst".

## Entscheidungen

| Was | Entscheidung |
|---|---|
| Frage | Ergebnis, mit Begründung in einem Halbsatz |

Nur bei mehr als zwei Entscheidungen als Tabelle, sonst Fließtext. Verworfene Optionen
gehören hier rein, der Grund ist später mehr wert als das Ergebnis.

## Offene Punkte

- [ ] Konkret genug, dass es ohne den Chat verständlich ist
- [ ] Mit Bedingung, falls die Sache von etwas abhängt
```

Optionale Abschnitte, nur wenn es sie wirklich gibt:

- `## Nachtrag — <Stichwort>` bei Ergänzungen am selben Tag
- `## Korrekturen` wenn im Verlauf ein Fehler gefunden und behoben wurde. Wichtig, weil
  ältere Notizen dann eventuell noch falsche Angaben enthalten
- `## Blockiert` bei Dingen, die technisch nicht gingen, mit der Fehlermeldung im
  Original

Fehlt ein Abschnitt inhaltlich, weglassen statt mit "keine" zu füllen.

## Ton

Sachlich, im Präteritum, ohne Marketing. Die Notiz erklärt dem eigenen Ich in sechs
Monaten, was hier passiert ist, nicht wie produktiv die Session war. Unsicherheiten
offen benennen ("ungetestet", "offen, ob") statt glattziehen.
