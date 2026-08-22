---
name: modell-wahl
description: Empfiehlt, welches Claude-Modell (Haiku, Sonnet, Opus) für die aktuelle Aufgabe das richtige ist, um Tokens und Nutzungslimit zu sparen, ohne Qualität zu verlieren. Aktivieren bei "welches Modell", "welches Model soll ich nehmen", "reicht Sonnet", "reicht Haiku", "Opus oder Sonnet", "Modellwahl", "brauche ich dafür Opus", "Token sparen", "das ist zu teuer", "Limit fast erreicht", "wie kriege ich das billiger" — sowie eigenständig als Einzeiler, wenn Modell und Aufgabe erkennbar nicht zusammenpassen.
---

# Modell-Wahl

Ziel: das kleinste Modell benutzen, das die Aufgabe noch sicher löst. Nicht das größte, das sie besonders gut löst.

## Wann dieser Skill etwas sagt

**Auf Zuruf:** Immer, wenn der User nach dem Modell, nach Kosten oder nach Token-Sparen fragt. Dann eine Empfehlung mit Begründung in ein bis drei Sätzen.

**Von selbst (Mismatch-Warnung):** Nur ein Einzeiler, und nur wenn der Fall klar ist:

- Der User arbeitet mit **Opus** an etwas rein Mechanischem (Dateien umbenennen, Daten extrahieren, Format konvertieren, eine Vorlage befüllen).
- Er arbeitet mit **Haiku** an etwas, das Urteil verlangt (Vertragsrisiko, Text mit eigener These, strategische Abwägung, mehrdeutiges Debugging) — und die Antwort wird sichtbar dünn.

Format der Warnung, ans Ende der normalen Antwort, ohne Aufhebens:

> Nebenbei: Dafür hätte Sonnet gereicht — `/model sonnet`.

Regeln für die Warnung: höchstens **einmal pro Session pro Richtung**. Nicht wiederholen, wenn der User sie ignoriert hat. Nicht warnen, wenn er das Modell in dieser Session bereits bewusst gesetzt hat. Nicht warnen bei kurzen Gesprächen — der Hinweis kostet dann mehr, als er spart.

## Die Entscheidung

Vier Fragen, in dieser Reihenfolge. Die erste, die mit Ja beantwortet wird, entscheidet.

1. **Ist ein Fehler teuer oder schwer zu bemerken?** (Vertrag, Geld, Außenwirkung, Recht, ein Text, der unter seinem Namen erscheint) → **Opus**
2. **Ist die Aufgabe mehrdeutig, offen oder verlangt eine eigene These?** (Strategie, Kritik, "was soll ich hier überhaupt tun", verworrener Bug) → **Opus**
3. **Braucht es Recherche, mehrere Werkzeuge, Code oder mehr als ein paar Schritte?** → **Sonnet**
4. **Sonst:** → **Haiku**

## Zuordnung nach Aufgabentyp

**Haiku** — mechanisch, klar definiert, Ergebnis sofort prüfbar:
Dateien sortieren und umbenennen, Daten aus einem Dokument ziehen, Formate konvertieren, kurze Texte zusammenfassen, eine bestehende Vorlage befüllen, Terminfragen an den Kalender, "was steht in dieser Mail", ein Dokument aus bereits fertigen Angaben erzeugen, einen Chat als Notiz ablegen.

**Sonnet** — der Normalfall, hier läuft das meiste:
Recherche, Code, Content-Produktion nach klaren Vorgaben, Marketing- und Produkttexte, Dokumente bauen (docx, pptx, xlsx, pdf), E-Mails, Skill-Ausführung mit eindeutigen Regeln, Chat-Kompaktierung, Dashboards und Briefings.

**Opus** — wenn Urteilsvermögen die eigentliche Arbeit ist:
Vertrags- und AGB-Prüfung, Texte mit eigener Position (Kritik, Essay, Statement, Pressetext), heikle Gespräche vorbereiten, Briefe, die von Doppelbödigkeit leben, strategische Entscheidungen, KI-Spuren aus Texten entfernen, wenn es wirklich unhörbar werden soll, lange autonome Läufe ohne Aufsicht, bei denen ein früher Denkfehler alles Folgende ruiniert.

**Zwischenweg, der oft der beste ist:** Mit Sonnet arbeiten, das Ergebnis mit Opus prüfen lassen. Ein Prüfdurchgang über ein fertiges Ergebnis ist viel billiger als die ganze Produktion mit Opus.

## Was der User über die Kosten wissen muss

Diese Punkte offen ansprechen, wenn nach Token-Sparen gefragt wird. Sie sind wichtiger als die Modellwahl selbst:

- **Der Kontext kostet mehr als das Modell.** Jeder Turn schickt die gesamte bisherige Unterhaltung neu. Ein langer Chat mit Haiku kann teurer sein als ein kurzer mit Opus. Der größte Hebel ist ein neuer Chat für ein neues Thema — dafür gibt es `chat-compaction`.
- **Geladene Connectors und Tools kosten bei jedem Turn.** Wer ein Dutzend MCP-Server gleichzeitig aktiv hat, zahlt deren Werkzeugbeschreibungen in jeder einzelnen Nachricht mit. Für eine Session, die nur Text schreibt, lohnt es sich, nicht gebrauchte Connectors abzuschalten.
- **Ein Modellwechsel mitten im Chat wirkt erst ab dem nächsten Turn** und nimmt den vollen bisherigen Kontext mit. Wechseln lohnt also früh, nicht nach der zwanzigsten Nachricht.
- **Das Modell zu klein zu wählen kann teurer sein.** Drei Korrekturrunden mit Haiku verbrauchen mehr als ein sauberer Durchgang mit Sonnet. Sparen heißt: richtig beim ersten Mal.

## Ausgabeformat

Auf eine direkte Frage: eine Zeile Empfehlung, eine Zeile Begründung, der Befehl. Nicht mehr.

```
Sonnet. Recherche mit mehreren Quellen, aber keine strittigen Urteile — Opus bringt hier nichts.
→ /model sonnet
```

Wenn die Sache wirklich auf der Kippe steht, das sagen, statt eine Sicherheit vorzutäuschen: "Grenzfall. Sonnet reicht wahrscheinlich; wenn der Text nach außen geht, nimm Opus."

## Modellklassen statt Versionen

Immer von **Haiku / Sonnet / Opus** sprechen, nie von Versionsnummern. Die Nummern ändern sich mehrmals im Jahr, das Verhältnis der Klassen zueinander bleibt: Haiku schnell und günstig, Sonnet der Arbeiter, Opus der Denker. Wenn nach der konkret aktuellen Version gefragt wird, nachschlagen statt raten.
