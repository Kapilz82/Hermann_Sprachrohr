# Hermanns Sprechtafel – Plan & Claude-Code-Prompts

## Was es ist
AAC-Sprechtafel (Talker) für Opa Hermann: Tablet im Bett, eine Hand, ein Tipp = Satz wird vorgelesen. Web Speech API (de-DE), kein Backend, keine Installation, läuft als GitLab Page oder direkt als lokale Datei.

## Architektur (wie deine BIT-Seite)
- Eine `index.html`, komplett self-contained
- Alle Wörter/Sätze/Symbole in einem klar markierten `CONFIG`-Block oben im Script – editieren wie JSON, nichts anderes anfassen
- `symbol` (Emoji), `wort` (steht auf der Kachel), `satz` (wird gesprochen – bewusst getrennt: Kachel sagt "Durst", Stimme sagt den ganzen Satz)

## Design-Entscheidungen
- Dunkles Nachtblau statt Weiß → blendet abends im Bett nicht
- Kacheln min. 150 px, Emoji 60 px, Wort 26 px fett, Atkinson Hyperlegible (Schrift für Sehschwäche)
- Kategorie = Farbe (unterer Kachelrand + Tab): Menschen rosa, Brauche türkis, Antworten gelb, Zimmer blau
- Sprechblase oben zeigt den letzten Satz riesig + 🔁-Knopf zum Wiederholen
- Ein-Tipp-Logik, kein Doppeltipp, kein Zoom, kein Scrollen nötig pro Kategorie
- Wake Lock: Bildschirm bleibt an
- Vibration als Tipp-Feedback (Android)

## Kategorien (Startbelegung)
1. **Menschen**: Wilhelmine, Uwe, Alex, Anrufen, Besuch, Allein
2. **Brauche**: Durst, Hunger, Toilette, Schmerzen, Umlagern, Medizin, Kalt, Warm
3. **Antworten**: Ja, Nein, Danke, Gut, Schlecht, Später, Weiß nicht, Hab dich lieb
4. **Zimmer**: Fernseher, Licht an/aus, Brille, Fenster, Leiser

## Testen vor Übergabe
1. Datei aufs Tablet → in Chrome/Safari öffnen, einmal tippen (erster Tipp aktiviert TTS + Wake Lock)
2. Prüfen ob eine deutsche Stimme installiert ist (Android: Einstellungen → System → Sprachausgabe; iPad spricht de-DE out of the box)
3. Als Lesezeichen auf Homescreen legen → läuft wie App im Vollbild

---

## Claude-Code-Prompts (copy & paste)

**Schon fertig gebaut (kein Prompt nötig):** PWA-Manifest, Service Worker
(offline), App-Icons, iPad-Vollbild-Meta-Tags, Stimm-Check-Banner,
Maus-Hover/Tastatur-Fokus, `.gitlab-ci.yml` für Pages-Deploy.

### Prompt 1 – Repo anlegen & deployen
```
Im aktuellen Ordner liegt eine fertige PWA (AAC-Sprechtafel für meinen Opa:
index.html, manifest.webmanifest, sw.js, Icons, .gitlab-ci.yml).
Initialisiere ein Git-Repo "opa-talker", commite alles und pushe es zu
meinem GitLab, sodass die Pages-Pipeline läuft. Danach kurz prüfen ob die
Pipeline grün ist und mir die Pages-URL nennen.
```

### Prompt 2 – Später: Bearbeiten-Modus für die Familie
```
Ergänze einen versteckten Editier-Modus (5 Sekunden auf den Titel drücken):
Formular zum Hinzufügen/Ändern/Löschen von Wörtern pro Kategorie,
Speicherung in localStorage mit Export/Import als JSON-Datei,
damit Wilhelmine und Uwe Wörter ohne Code anpassen können.
```

## Später-Ideen (nicht für v1)
- Foto-Kacheln statt Emojis (echte Fotos von Wilhelmine/Uwe/Alex – wirkt für Opa vertrauter)
- Scanning-Modus falls die Hand schwächer wird (Kacheln blinken durch, ein großer Taster wählt)
- Satz-Baukasten (Wörter aneinanderreihen) – erst wenn die Ein-Tipp-Version sitzt
