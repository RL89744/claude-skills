---
name: rechnung-erstellen
description: Eine saubere, rechtskonforme PDF-Rechnung aus wenigen Angaben erzeugen. Diesen Skill aktivieren bei Formulierungen wie "Rechnung erstellen", "Rechnung schreiben", "Kunde abrechnen", "Rechnung generieren", "Invoice erstellen", "Rechnung an" oder wenn für eine erbrachte Leistung eine Rechnung ausgestellt werden soll.
---

# Rechnung erstellen

Professionelle Rechnung als PDF aus wenigen Eingaben generieren. Keine Vorlage nötig, keine Software installieren. Nur Empfänger, Leistung und Betrag angeben — den Rest erledigt der Skill.

## Ablauf

### Schritt 1: Angaben zusammentragen

Aus der Anfrage oder dem Projektkontext extrahieren:

**Empfänger:**
- Name / Firma
- Anschrift (für rechtskonforme Rechnung erforderlich)
- Ggf. USt-ID (bei B2B im EU-Ausland, für Reverse Charge)

**Eigene Daten:**
- Firmen- oder Geschäftsname
- Vollständige Anschrift
- Steuernummer oder USt-ID
- Bankverbindung (IBAN, BIC)
- Kontakt (E-Mail, ggf. Telefon)
Diese Daten möglichst aus der Projektdatei (CLAUDE.md o.ä.) ziehen, nicht erfinden.

**Rechnungsdaten:**
- Rechnungsnummer (fortlaufend, eindeutig; falls nicht vorgegeben: Format `YYYY-NNN`)
- Rechnungsdatum (heute, falls nicht anders angegeben)
- Leistungsdatum oder -zeitraum (Pflicht nach §14 UStG)
- Zahlungsziel (Standard: 14 Tage netto)
- Positionen: Beschreibung, Menge, Einzelpreis
- Umsatzsteuer: 19 %, 7 % oder steuerfrei (Kleinunternehmer §19 UStG oder Reverse Charge)

Bei unvollständigen Angaben: nur dann nachfragen, wenn Empfängername oder Beträge fehlen. Alles andere möglichst sinnvoll vervollständigen oder Platzhalter setzen.

### Schritt 2: Beträge berechnen

Für jede Position:
- Menge × Einzelpreis = Positionssumme

Dann:
- **Netto-Gesamtbetrag** = Summe aller Positionen
- **Umsatzsteuer** = Netto × Steuersatz (bei Kleinunternehmer entfällt das)
- **Brutto / Rechnungsbetrag** = Netto + USt

Zweimal rechnen lassen. Falsche Summen ruinieren die Glaubwürdigkeit — und bei Rechnungen auch die Zahlungsmoral.

### Schritt 3: Rechnung gestalten

Aufbau nach deutschen Anforderungen (§14 UStG):

```
[Eigener Firmenname]
[Eigene Anschrift]
[E-Mail · Telefon]

                                          [Empfängername]
                                          [Empfängeranschrift]


RECHNUNG Nr. [Rechnungsnummer]

Rechnungsdatum:     [Datum]
Leistungszeitraum:  [Zeitraum oder -datum]
Kundennummer:       [falls vorhanden]

---

| Pos. | Beschreibung              | Menge | Einzelpreis | Betrag     |
|------|---------------------------|-------|-------------|------------|
| 1    | [Leistung]                | [X]   | [X,XX €]    | [X,XX €]   |
| 2    | [Leistung]                | [X]   | [X,XX €]    | [X,XX €]   |

---

                            Nettobetrag:       [X,XX €]
                            zzgl. 19 % USt:    [X,XX €]
                            Rechnungsbetrag:   [X,XX €]

Zahlungsziel: [Datum] ([X] Tage netto)

Bankverbindung:
[Kontoinhaber]
IBAN: [IBAN]
BIC:  [BIC]
Verwendungszweck: Rechnung [Nummer]

Steuernummer: [Nummer]  ·  USt-IdNr.: [Nummer]

[Bei Kleinunternehmer: Gemäß § 19 UStG wird keine Umsatzsteuer berechnet.]
[Bei Reverse Charge: Steuerschuldnerschaft des Leistungsempfängers (Reverse Charge).]

Vielen Dank für den Auftrag.
```

### Schritt 4: PDF generieren

Mit Python (`reportlab` oder `fpdf2`) ein sauber formatiertes PDF erzeugen. Standardschrift: Helvetica oder eine serifenlose Systemschrift. Schriftgrößen: 10pt Fließtext, 14pt für "RECHNUNG Nr. X".

Dateiname: `Rechnung-[Nummer]-[Empfaenger].pdf`

Ablageort: Arbeitsordner des Nutzers.

### Schritt 5: Übergabe

Dateipfad zur Verfügung stellen, plus Einzeiler mit:
- Rechnungsbetrag
- Fälligkeit
- Empfänger

Optional anbieten: "Soll eine Vorlage für diesen Kunden gespeichert werden, damit künftige Rechnungen schneller gehen?"

## Pflichtangaben für rechtskonforme Rechnungen in Deutschland

Nach §14 Abs. 4 UStG müssen auf einer ordnungsgemäßen Rechnung stehen:

1. Vollständiger Name und Anschrift des leistenden Unternehmens
2. Vollständiger Name und Anschrift des Leistungsempfängers
3. Steuernummer oder USt-IdNr. des leistenden Unternehmens
4. Ausstellungsdatum
5. Fortlaufende, eindeutige Rechnungsnummer
6. Menge und handelsübliche Bezeichnung der Leistung
7. Leistungsdatum oder -zeitraum
8. Nach Steuersätzen aufgeschlüsseltes Entgelt (netto)
9. Angewandter Steuersatz und Steuerbetrag
10. Bei Steuerbefreiung: Hinweis darauf

Bei Kleinbetragsrechnungen bis 250 € brutto reichen vereinfachte Angaben (kein Empfängername nötig).

## Regeln

- Rechenergebnisse immer zweimal prüfen. Netto-, USt- und Bruttobetrag müssen stimmen.
- Optik schlicht und geschäftsmäßig. Keine Dekoration, keine Icons, keine Farbverläufe.
- Eigene Daten aus dem Projektkontext übernehmen, nicht erfinden. Fehlende Bankdaten als Platzhalter markieren, nicht frei erfinden.
- Währung: EUR als Standard, Format `1.234,56 €` (deutsches Format mit Punkt als Tausendertrenner und Komma als Dezimaltrenner).
- Rechnungsnummer muss eindeutig und fortlaufend sein — bei mehreren Rechnungen im selben Chat hochzählen.
- Bei Kleinunternehmer-Rechnungen: USt weglassen UND den §19-Hinweis unten aufnehmen. Beides zusammen.
- Datumsformat: `TT.MM.JJJJ` (deutsch) — nicht ISO, nicht US-Format.
