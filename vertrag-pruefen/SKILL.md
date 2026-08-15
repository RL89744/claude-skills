---
name: vertrag-pruefen
description: Verträge, AGB und juristische Dokumente analysieren, problematische Klauseln markieren und eine klare Empfehlung zur Unterzeichnung geben. Diesen Skill aktivieren bei Formulierungen wie "Vertrag prüfen", "Vertrag checken", "soll ich das unterschreiben", "Vertragsanalyse", "was steht da drin", "NDA checken", "Mietvertrag durchsehen", "Freelance-Vertrag prüfen", "AGB checken" oder wenn ein Vertragstext, eine Vereinbarung oder ein juristisches Dokument zur Prüfung eingefügt wird.
---

# Vertrag prüfen

Dieser Skill analysiert Verträge und juristische Dokumente. Juristensprache wird in verständliches Deutsch übersetzt, riskante Klauseln werden markiert, und am Ende steht eine klare Einschätzung: unterschreiben, nachverhandeln oder ablehnen.

## Eingabeformate

Akzeptiert werden:
- Direkt eingefügter Vertragstext
- PDF oder Word-Datei im Ordner
- Screenshot eines Vertrags
- URL zu AGB oder Nutzungsbedingungen
- Beschreibung eines Deals mit der Frage, was im Vertrag stehen sollte

## Vorgehen

Das komplette Dokument lesen, dann in dieser Reihenfolge auswerten:

1. Worum geht es in der Vereinbarung?
2. Was sind die zentralen Bedingungen?
3. Welche Klauseln sind problematisch?
4. Was fehlt, obwohl es drinstehen sollte?
5. Empfehlung: unterschreiben, nachverhandeln oder ablehnen?

## Ausgabeformat

```
# Vertragsprüfung — [Dokumenttitel oder -art]

**Art:** [Arbeitsvertrag / Freelance-Vertrag / NDA / Mietvertrag / SaaS-AGB / etc.]
**Parteien:** [Partei A] und [Partei B]
**Datum:** [falls angegeben]

---

## Kurzfassung

[3–4 Sätze. Worum geht es, zu wessen Gunsten ist der Vertrag formuliert, und was ist das Wichtigste, das vor Unterschrift bekannt sein muss.]

## Zentrale Bedingungen

| Klausel | Was der Vertrag sagt | Was das praktisch bedeutet |
|---------|---------------------|---------------------------|
| Laufzeit | [Zitat] | [Klartext] |
| Vergütung / Zahlung | [Zitat] | [Klartext] |
| Kündigung | [Zitat] | [Klartext] |
| Haftung | [Zitat] | [Klartext] |
| Rechte / Eigentum | [Zitat] | [Klartext] |
| Gerichtsstand | [Zitat] | [Klartext] |

## Problematische Klauseln

[Pro Problem dieses Format:]

### 🔴 [Titel des Problems]

**Klausel im Wortlaut:** "[Exaktes Zitat aus dem Vertrag]"

**Warum das ein Problem ist:** [Verständlich erklärt, welcher Nachteil daraus entsteht]

**Alternativvorschlag:** [Konkrete Umformulierung oder Änderung, die nachzuverhandeln ist]

[Pro Problem wiederholen. Wenn keine roten Flaggen gefunden werden: "Keine ernsten Probleme gefunden." und kurz begründen, warum der Vertrag fair wirkt.]

## Graubereich

[Dinge, die keine Deal-Breaker sind, aber im Hinterkopf bleiben sollten:]

- ⚠️ **[Thema]** — [Warum es relevant ist und worauf zu achten ist]
- ⚠️ **[Thema]** — [Warum es relevant ist und worauf zu achten ist]

## Was fehlt

[Wichtige Klauseln, die in diesem Vertragstyp üblich sind, hier aber fehlen:]

- **[Fehlende Klausel]** — [Warum das relevant ist. Beispiel: "Ohne ordentliches Kündigungsrecht ist eine Bindung auf unbestimmte Zeit möglich."]
- **[Fehlende Klausel]** — [Warum das relevant ist]

## Empfehlung

**Unterschreiben?** [Ja / Ja, mit Änderungen / Nein]

[2–3 Sätze zur Begründung. Direkt, ohne Beschönigung. Falls nachverhandelt werden sollte: genau benennen, was zu ändern ist. Falls abgelehnt: das auch so sagen.]

## Formulierungen für die Nachverhandlung

[1–3 konkrete Textbausteine, die sich direkt kopieren und an die Gegenseite schicken lassen:]

1. **Zu [Problem]:** "Ich möchte [Klausel] anpassen. Lässt sich das auf [konkrete Alternative] ändern? So sind beide Seiten abgesichert."

2. **Zu [Problem]:** "[Textbaustein]"
```

## Besonderheiten nach Vertragsart

### Freelance- und Werkverträge
Immer prüfen:
- Zahlungsziel (14, 30, 60 Tage?)
- Abbruchhonorar bei Projektstopp durch Auftraggeber
- Nutzungsrechte und Portfolio-Verwendung
- Regelung bei Scope-Erweiterung
- Wettbewerbsverbot (räumlich und zeitlich angemessen?)
- Scheinselbständigkeit-Risiko (insbesondere bei Einzelkunden-Abhängigkeit)

### NDA / Geheimhaltungsvereinbarungen
Immer prüfen:
- Laufzeit (unbefristet ist eine rote Flagge)
- Definition von "vertraulichen Informationen" (zu weit gefasst?)
- Einseitig oder wechselseitig?
- Ausnahmen (öffentlich bekannte Infos, gerichtliche Anordnungen)
- Vertragsstrafen bei Verstoß

### Arbeitsverträge
Immer prüfen:
- Probezeit und Kündigungsfristen
- Nachvertragliches Wettbewerbsverbot (Dauer, Reichweite, Karenzentschädigung)
- Überstundenregelung (Pauschalabgeltung problematisch)
- IP-Abtretung (auch für Werke außerhalb der Arbeitszeit?)
- Urlaubs- und Bonusregelungen
- Verfallsklauseln für Ansprüche

### Mietverträge
Immer prüfen:
- Kündigungsfristen und Mindestvertragslaufzeit
- Mieterhöhungsklauseln (Index, Staffel, oder Vergleichsmiete?)
- Schönheitsreparaturen (starre Fristen sind oft unwirksam)
- Untervermietung
- Kautionsregelung und Rückzahlungsmodalitäten
- Betriebskostenabrechnung

### SaaS / Nutzungsbedingungen
Immer prüfen:
- Datenhoheit und Exportmöglichkeit
- Ankündigungsfristen bei Preiserhöhungen
- Automatische Verlängerung und Kündigungsmodalitäten
- SLA / garantierte Verfügbarkeit
- Haftungsbegrenzung
- DSGVO-Konformität und Auftragsverarbeitungsvertrag

## Regeln

- Juristensprache immer übersetzen. Fachbegriffe direkt beim ersten Auftreten in einem Halbsatz erklären.
- Problematische Klauseln nicht beschönigen. Wenn etwas einseitig ist, wird das so benannt.
- Immer anmerken, welche Partei der Vertrag begünstigt. In der Regel diejenige, die ihn aufgesetzt hat.
- Konkrete Formulierungen für die Nachverhandlung liefern. Nicht "hier sollte verhandelt werden", sondern der fertige Textbaustein.
- Am Ende dieser Hinweis: "Das ist keine Rechtsberatung. Bei wichtigen Verträgen (Arbeitsvertrag, größere Aufträge, Gesellschaftsverträge) zusätzlich einen Anwalt einbeziehen. Diese Prüfung hilft beim Verstehen und Vorbereiten der richtigen Nachfragen."
- Wenn ein Vertrag fair und ausgewogen ist, das auch so sagen. Keine künstlichen Probleme erfinden.
- Automatische Verlängerungsklauseln jedes Mal explizit markieren. Das ist der Klassiker, den Leute übersehen und später bereuen.
- Bei deutschen Verträgen auf AGB-Kontrolle achten: überraschende, unangemessen benachteiligende Klauseln sind oft nach §§ 305 ff. BGB unwirksam, auch wenn sie unterschrieben wurden.
