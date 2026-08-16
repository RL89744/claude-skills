# ki-spuren-entfernen
<img width="2200" height="1100" alt="Large-BALENCIAGA_JERSEY_2200x1100px_DESKTOP_W_03_2544" src="https://github.com/user-attachments/assets/2feb2019-6418-4fed-a39e-c34ccbf50219" />

Ein Claude Skill, der deutschen Texten die typischen Spuren maschineller
Erzeugung austreibt. 23 katalogisierte Muster, jeweils mit Beispiel, Diagnose
und Alternative, plus ein vollständiges Vorher-Nachher an einem längeren Text.

Deckt ab: inhaltliche Muster (Bedeutungsinflation, Nominalstil, KI-Lieblingswörter,
Werbesprache, Schwammwörter, Partizipialphrasen, Kopula-Vermeidung,
"nicht nur/sondern auch", Dreierfiguren, Synonymzwang, falsche Spannweiten,
hohle Einleitungen), stilistische Muster (Gedankenstrich-Flut, Fettschrift,
Bullet-Tic, Emojis in Überschriften, typografische Anführungszeichen),
Kommunikationsmuster (Chatbot-Reste, Cut-Off-Disclaimer, übertriebene
Zustimmung) sowie Füllwörter, Hedging und generische Optimismus-Schlüsse.

## Wozu

Die kursierenden "Signs of AI writing"-Listen sind englischsprachig. Übersetzt
helfen sie nur halb, weil deutsche Modelle andere Tells produzieren: hohe
Nominalstildichte, aufgeblähter Wortschatz, gleichförmiger Satzbau, stabile
Floskelmuster. Dieser Skill katalogisiert, was im Deutschen konkret nach
Maschine klingt.

Der wichtigere Teil steht allerdings vor dem Katalog. Ein Text kann jedes
einzelne Muster vermeiden und trotzdem tot sein, wenn niemand dahintersteht.
Deshalb bleibt es nicht beim Streichen: der Skill fordert Haltung, ungleiche
Satzlängen, Ambivalenz und konkrete Beispiele ein. Am Ende läuft ein zweiter
Durchgang, der die Frage stellt, was immer noch nach KI klingt, und eine
nachgeschärfte Fassung liefert.

## Installation

**Claude Code / Claude Agent SDK (lokal):**

```bash
mkdir -p ~/.claude/skills/ki-spuren-entfernen
cp SKILL.md ~/.claude/skills/ki-spuren-entfernen/
```

**Cowork / claude.ai:**

`SKILL.md` als `.skill`-Datei (ZIP-Archiv) packen und im Chat hochladen. Claude
bietet dann an, sie als Skill zu speichern.

```bash
zip -r ki-spuren-entfernen.skill ki-spuren-entfernen/
```

## Verwendung

Text einfügen und *"humanisieren"*, *"das klingt nach ChatGPT"*, *"mach den
Text natürlicher"* oder *"zu glatt geschrieben"*. Der Skill liefert die
überarbeitete Fassung plus eine Liste dessen, was geändert wurde und warum.

## Abgrenzung

Nur für Deutsch. Für englische Texte greifen die Beispiele daneben, weil
die Tells andere sind.

Kein Detektor. Der Skill sagt nicht, ob ein Text von einer KI stammt, er
entfernt die Merkmale, die danach aussehen. Das ist auch bei von Hand
geschriebenen, aber steifen Texten nützlich.

Kein Freibrief für Täuschung. Wo Kennzeichnungspflicht besteht (Prüfungen,
wissenschaftliche Arbeiten, redaktionelle Vorgaben), ändert ein anderer
Sprachstil nichts an der Pflicht, die Herkunft anzugeben.

## Konfiguration

Keine.

## Quellen

Beobachtungen deutscher Ausgaben von ChatGPT, Claude, Gemini und Mistral aus
2023 bis 2025, angelehnt an die Kategorien des englischen WikiProject AI Cleanup
("Signs of AI writing"), auf den deutschen Sprachraum übertragen.

## Lizenz

MIT — siehe [LICENSE](../LICENSE).
