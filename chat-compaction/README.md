# chat-compaction
<img width="2048" height="1365" alt="Home_Sachwert-2048x1365" src="https://github.com/user-attachments/assets/b9e0d7a8-1c1f-4029-9ea0-4cc35adfda14" />

Ein Claude Skill, der einen langen Chat zu einem strukturierten Handover-Block
verdichtet, den man als erste Nachricht in einen neuen Chat einfügt. Der neue
Chat startet dann mit minimalem Kontext statt mit dem gesamten bisherigen Verlauf.

Deckt ab: Kontext und Ziel, aktueller Stand, getroffene Entscheidungen und
Sackgassen, Artefakte verbatim (Code, Zahlen, URLs), offene Punkte, erste
Aktion im neuen Chat.

## Wozu

Das serverseitige Compaction-Feature der Claude API löscht alte Nachrichten
physisch aus dem Kontext. In der Consumer-App gibt es das nicht: ein laufender
Chat lässt sich nicht nachträglich verkleinern. Dieser Skill baut den Ersatz von
Hand, nämlich eine Übergabe, die in einem frischen Chat weiterläuft.

Die Ersparnis entsteht erst beim Wechsel. Der Skill sagt das dem User auch
ausdrücklich, statt so zu tun, als wäre der aktuelle Chat danach leichter.

Der Block ist bewusst kein Fließtext-Protokoll: Diskussionen und Begründungswege
werden aggressiv gekürzt, Code, Zahlen, Namen und URLs dagegen wörtlich
übernommen. Was im neuen Chat rekonstruierbar wäre, fliegt raus. Was dort exakt
gebraucht wird, bleibt Zeichen für Zeichen erhalten.

## Installation

**Claude Code / Claude Agent SDK (lokal):**

```bash
mkdir -p ~/.claude/skills/chat-compaction
cp SKILL.md ~/.claude/skills/chat-compaction/
```

**Cowork / claude.ai:**

`SKILL.md` als `.skill`-Datei (ZIP-Archiv) packen und im Chat hochladen. Claude
bietet dann an, sie als Skill zu speichern.

```bash
zip -r chat-compaction.skill chat-compaction/
```

## Verwendung

`/compact`, `/komprimieren`, `/handover` oder in natürlicher Sprache:
*"komprimier den chat"*, *"übergib das in nen neuen Chat"*, *"der Chat wird zu
lang"*.

Die Ausgabe ist genau ein Markdown-Codeblock, damit sie sich mit dem
Copy-Button am Block in einem Zug greifen lässt. Danach: neuen Chat öffnen,
Block als erste Nachricht einfügen, weiterarbeiten.

## Abgrenzung

Nicht für einfache Zusammenfassungen. Wer *"fass den Chat mal zusammen"* meint
und keine Fortsetzung plant, bekommt hier ein unnötig technisches Format.

Nicht zu verwechseln mit einem Chat-Archiv: der Handover ist für den nächsten
Claude geschrieben, nicht für den Menschen in sechs Monaten. Wer Letzteres will,
ist bei [`chat-in-obsidian-speichern`](../chat-in-obsidian-speichern/) richtig.

## Konfiguration

Keine. Der Skill übernimmt die Sprache des Chats.

## Lizenz

MIT — siehe [LICENSE](../LICENSE).
