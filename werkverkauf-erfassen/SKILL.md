---
name: werkverkauf-erfassen
description: Verkauf eines Kunstwerks erfassen — Preis vorschlagen, bestehenden Werkkatalog um Käufer, Verkaufsdatum und Zahlungsstatus ergänzen, und die Daten für eine Rechnung vorbereiten. Diesen Skill aktivieren bei Formulierungen wie "Werk verkauft", "Verkauf erfassen", "[Titel] ist verkauft an...", "Preis für [Werk] vorschlagen", "Käufer eintragen", "was soll [Werk] kosten" oder wenn ein Kunstwerk, Druck oder Editionsstück den Besitzer wechselt.
---

# Werkverkauf erfassen

Schließt die Lücke zwischen Werkkatalog und Buchhaltung: ein Kunstwerk wird
verkauft, dieser Skill trägt den Verkauf im bestehenden Katalog nach, schlägt
bei Bedarf einen Preis vor und liefert alle Angaben so aufbereitet, dass eine
Rechnung direkt daraus erstellt werden kann.

Der Skill legt **kein neues Katalogsystem an**. Er lernt das Schema, das
bereits existiert — Tabellenspalten, Statuswerte, ID-Format — und schreibt
dort hinein. Nur wenn wirklich noch kein Katalog existiert, wird ein
minimales Schema vorgeschlagen.

## Ablauf

### Schritt 1: Bestehenden Katalog finden und Schema lernen

Bevor irgendetwas geschrieben wird: den Werkkatalog des Nutzers suchen
(Ordner- oder Dateiname mit "Werk", "Katalog", "Archiv", "Inventar" o. ä.,
oder Hinweis aus dem Projektkontext). Mindestens einen bestehenden,
ausgefüllten Eintrag lesen und daraus ableiten:

- Wie werden einzelne Werke identifiziert? (Titel allein reicht selten —
  meist gibt es eine ID/SKU, oft mit Jahr oder Listennummer)
- Welche Statuswerte gibt es, und wo im Workflow steht "verkauft" logisch
  dazu? (Falls der bestehende Status-Workflow nur Produktion/Content abdeckt,
  z. B. bis "gepostet", dann "verkauft"/"reserviert" als neue Werte ergänzen,
  nicht bestehende überschreiben.)
- Sind Preis, Käufer, Verkaufsdatum, Zahlungsstatus schon Felder? Wenn nein:
  in derselben Struktur ergänzen (neue Spalte, neuer Abschnitt), nicht in
  einem separaten, unverbundenen System.
- Maß- und Materialangaben, aus denen sich ein Preis ableiten lässt.

**Nie raten, wo die Struktur unklar ist.** Lieber kurz nachfragen oder einen
Vorschlag zur Bestätigung vorlegen, als ein bestehendes, gewachsenes System
zu verbiegen.

Existiert noch kein Katalog: minimales Schema anlegen mit Titel, ID, Jahr,
Maß, Material, Status, Preis, Käufer, Verkaufsdatum, Zahlungsstatus — als
einzelne Datei oder Tabelle, je nachdem was zum sonstigen Notizsystem passt
(Obsidian-Frontmatter, einfache Markdown-Tabelle, CSV).

### Schritt 2: Preis vorschlagen (nur wenn gefragt oder noch kein Preis gesetzt)

Basisformel, transparent und nachvollziehbar:

```
Vorschlag = Fläche (Höhe × Breite) × Basispreis-pro-Flächeneinheit × Faktor
```

Der Faktor hängt von Serie, Material/Technik, Edition (Unikat vs. Auflage)
und ggf. Rahmung ab. Diesen Faktor **nicht erfinden**:

1. Zuerst in bereits erfassten Verkäufen derselben Serie/Technik im Katalog
   nachsehen und daraus einen Faktor ableiten.
2. Gibt es noch keine Vergleichswerte: einmalig nachfragen, welcher
   Basispreis/Faktor angesetzt werden soll, und diesen für künftige
   Anfragen an einer zentralen Stelle notieren (z. B. eine kurze Konfig-Notiz
   im selben Ordner wie der Katalog), damit nicht bei jedem Werk neu gefragt
   werden muss.
3. Rahmung, Versand oder Vermittlungsprovision nur einrechnen, wenn das im
   Katalog oder der Anfrage explizit vorgesehen ist.

Ergebnis immer klar als **Vorschlag** kennzeichnen, nicht als feststehenden
Preis. Der tatsächliche Verkaufspreis in Schritt 3 kann davon abweichen
(Verhandlung, Rabatt, Sonderfall).

### Schritt 3: Verkauf erfassen

Angaben zusammentragen:

- Werk (Titel + ID/SKU — falls mehrdeutig, über die ID identifizieren)
- Käufer (Name, ggf. Kontakt — nur so viel speichern wie nötig)
- Verkaufspreis (final, nach Verhandlung)
- Verkaufsdatum
- Zahlungsstatus (offen / angezahlt / vollständig bezahlt)
- Sonderfälle: Rahmen inklusive, Versand, Rabatt, Reservierung mit Frist

Katalogeintrag aktualisieren: Status auf "verkauft" (oder "reserviert" bei
Anzahlung/Vorbehalt) setzen, restliche Felder ergänzen. Bestehende Angaben
(Maß, Material, Produktionsstatus, Content-Status) unangetastet lassen —
dieser Skill ergänzt, er überschreibt nicht.

### Schritt 4: Für Rechnung übergeben

Aus den erfassten Daten die Angaben zusammenstellen, die ein
Rechnungs-Skill (z. B. `rechnung-erstellen`) direkt braucht:

- Empfänger = Käufer
- Position = Werktitel + ID, mit kurzer Beschreibung (Technik, Maß, Jahr)
- Betrag = finaler Verkaufspreis
- Leistungsdatum = Verkaufsdatum

Wenn ein Rechnungs-Skill verfügbar ist: anbieten, ihn direkt mit diesen
Angaben aufzurufen. Wenn nicht: die Angaben so ausgeben, dass sie sich 1:1
in eine Rechnung oder ein Buchhaltungstool übertragen lassen.

### Schritt 5: Zusammenfassung

Kurz bestätigen:

```
✓ [Titel] ([ID]) — verkauft an [Käufer]
  Preis: [Betrag] · Status: [Zahlungsstatus] · Datum: [Datum]
  Katalog aktualisiert: [Dateiname/Pfad]
  → Rechnung erstellen? [ja/nein]
```

## Regeln

- Schema-Treue zuerst: das bestehende Katalogsystem lesen und verstehen,
  bevor irgendetwas geschrieben wird. Kein Parallelsystem aufbauen.
- Preisvorschläge sind Vorschläge. Nie unaufgefordert als "der Preis"
  ausgeben, immer als Berechnungsgrundlage kenntlich machen.
- Faktoren und Basispreise nicht raten — aus Vergleichsverkäufen ableiten
  oder einmalig erfragen und für Wiederverwendung merken.
- Nur die Käuferdaten speichern, die für Verkauf, Rechnung und ggf.
  Provenienz nötig sind. Keine zusätzlichen Felder erfinden.
- Bestehende Status- und Produktionsfelder (z. B. Content-/Postingstatus)
  nicht überschreiben — Verkaufsstatus ergänzt den Workflow, ersetzt ihn
  nicht.
- Währung und Zahlenformat an die Landeskonvention des Katalogs anpassen
  (im deutschsprachigen Raum: `1.234,56 €`, Datum `TT.MM.JJJJ`).
- Bei Unklarheit über Struktur oder fehlenden Angaben: kurz nachfragen,
  statt eine Annahme unkommentiert ins System zu schreiben.
