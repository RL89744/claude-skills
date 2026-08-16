---
name: "schnellrecherche"
description: "Ein Thema aus mehreren Quellen schnell recherchieren und als kompakten, quellenbelegten Kurzbericht ausgeben. Nur aktivieren, wenn ausdrücklich Recherche gewünscht ist: \"kurz recherchieren\", \"schnell checken\", \"gib mir einen Überblick zu\", \"Vergleich X vs. Y\", \"lohnt sich Tool X\", \"was ist der Stand bei\". NICHT bei normalen Wissens- oder Rückfragen im Gesprächsverlauf (\"was weißt du über\", \"was ist mit\") — die direkt beantworten. NICHT bei ausdrücklichem Wunsch nach Tiefe, Deep Dive oder einem gespeicherten Dokument (dafür: recherche-bericht)."
---

# Schnellrecherche

Kompakter Rechercheassistent für den schnellen Informationsbedarf. Kein tiefer Bericht, sondern eine kondensierte Antwort mit Quellen — als Entscheidungsgrundlage in 2 Minuten lesbar.

## Abgrenzung

- **Dieser Skill:** kurzer Überblick, Vergleich, Produkt-Check. Ergebnis bleibt im Chat.
- **`recherche-bericht`:** Deep Dive, ausführliche Ausarbeitung, Ergebnis ist ein gespeichertes Dokument. Dorthin wechseln, sobald Tiefe oder ein Dokument verlangt wird.
- **Kein Skill:** einfache Wissensfragen im Gesprächsverlauf. Direkt beantworten, notfalls mit einer einzelnen Websuche, ohne Berichtsformat.

## Schritt 1: Umfang klären

Erst einordnen, was tatsächlich gefragt ist:

- **Kurzantwort** — "Was ist eigentlich mit [X]?" → 2–3 Absätze Zusammenfassung
- **Vergleich** — "Soll ich X oder Y nehmen?" → Seite-an-Seite-Gegenüberstellung
- **Kompakter Überblick** — "Gib mir einen Überblick zu [Thema]" → Bericht mit Struktur unten

Standard ist der kompakte Überblick — außer es ist klar erkennbar, dass nur eine Kurzantwort erwartet wird.

## Schritt 2: Quellen sammeln

Web-Suche nutzen und aus mindestens 3–5 unterschiedlichen Quellen ziehen:

- Offizielle Produkt- oder Anbieterseiten
- Aktuelle Nachrichtenartikel und Ankündigungen
- Nutzerbewertungen und Community-Diskussionen (Reddit, Foren, Fachseiten)
- Preisseiten und Konditionen
- Vergleichstests und Konkurrenzanalysen

Aussagen über mehrere Quellen abgleichen. Wenn sich Quellen widersprechen, das explizit vermerken — nicht stillschweigend die plausibelste Version übernehmen.

## Schritt 3: Bericht bauen

```
RECHERCHEÜBERBLICK: [Thema]
━━━━━━━━━━━━━━━━━━━━━━━━━

ZUSAMMENFASSUNG
[2–3 Sätze — was es ist und warum es relevant ist]

KERNPUNKTE
- [Punkt 1 — belegt durch Quelle]
- [Punkt 2 — belegt durch Quelle]
- [Punkt 3 — belegt durch Quelle]
- [Punkt 4 — belegt durch Quelle]

KOSTEN / PREISE
[Gratis-Tier? Kostenpflichtige Pläne? Was bekommt man dafür?]

STÄRKEN
- [Stärke 1]
- [Stärke 2]

SCHWÄCHEN
- [Schwäche 1]
- [Schwäche 2]

EINSCHÄTZUNG
[Ein Absatz — ehrliche Einordnung. Ist das relevant? Für wen geeignet? Wer sollte die Finger davon lassen?]

QUELLEN
- [Quelle 1 mit Titel und URL]
- [Quelle 2 mit Titel und URL]
- [Quelle 3 mit Titel und URL]
```

## Regeln

- Immer Quellen angeben. Unbelegte Aussagen nicht als Fakt präsentieren.
- Bei widersprüchlichen Quellen ehrlich bleiben: "Quellen widersprechen sich in Punkt X" ist besser, als sich für eine Version zu entscheiden und das stillschweigend zu tun.
- Keine Marketingsprache übernehmen. Wenn ein Produkt schwach ist, das so sagen — nicht freundlich umformulieren.
- Keine erfundenen Zahlen. Keine geschätzten Prozentsätze, Marktanteile oder Preise, wenn sie nicht aus einer Quelle kommen. Stattdessen: "Keine belastbare Zahl gefunden" schreiben.
- Kompakt und scanbar bleiben. Überschriften, Bullets, kurze Absätze. Kein Fließtext über mehrere Zeilen.
- Bei Produktrecherche prüfen, ob das Tool überhaupt noch existiert und aktiv entwickelt wird. Keine toten Tools empfehlen.
- Bei sich schnell ändernden Themen (Preise, Features, Firmenstatus) ein Zeitfenster angeben: "Stand [Monat/Jahr] laut [Quelle]".
- Wenn die Recherche tiefer gehen sollte: am Ende anbieten, auf den Recherche-Bericht-Skill zu wechseln.
