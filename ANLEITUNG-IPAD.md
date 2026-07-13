# Sprechtafel auf dem iPad einrichten

## Variante A – Online (empfohlen, mit GitHub Pages)
1. Seite in **Safari** öffnen (die GitHub-Pages-Adresse)
2. **Teilen-Symbol** (Viereck mit Pfeil) → **"Zum Home-Bildschirm"** → Hinzufügen
3. Neues Icon "Sprechtafel" auf dem Homescreen antippen → startet im **Vollbild** ohne Browserleiste
4. Einmal auf eine Kachel tippen → Sprachausgabe ist aktiv, Bildschirm bleibt an
5. Nach dem ersten Laden funktioniert die App auch **offline**

## Variante B – Ohne Internet / ohne Deploy
- `index.html` per AirDrop/Mail aufs iPad → in Safari öffnen → geht sofort
- Vollbild + Offline-Cache gibt es nur über Variante A (Homescreen braucht https)

## Damit nichts schiefgeht
- **Geführter Zugriff** aktivieren (Einstellungen → Bedienungshilfen → Geführter Zugriff): dreimal Seitentaste drücken sperrt das iPad auf diese eine App – Opa kann nichts versehentlich schließen
- **Automatische Sperre** auf "Nie" stellen (Einstellungen → Anzeige & Helligkeit), Ladekabel dranlassen
- Lautstärke prüfen und Stummschalter aus
- Deutsche Stimme ist auf dem iPad vorinstalliert; schönere Stimme: Einstellungen → Bedienungshilfen → Gesprochene Inhalte → Stimmen → Deutsch → z. B. "Anna (Premium)" laden

## Wörter ändern
In `index.html` ganz oben den `CONFIG`-Block bearbeiten:
- `symbol` = Emoji auf der Kachel
- `wort` = Text auf der Kachel
- `satz` = was vorgelesen wird
Datei speichern, Seite neu laden – fertig.

## Falls das iPad eine alte Version zeigt
Die App lädt bei bestehender Internetverbindung automatisch die neueste
Version nach. Zeigt sie trotzdem noch alten Stand:
1. Einstellungen → Safari → Erweitert → Websitedaten → nach "github.io"
   suchen → Wischen zum Löschen → Löschen
2. Icon vom Homescreen entfernen (antippen & halten → Entfernen)
3. Seite frisch in Safari öffnen, erneut "Zum Home-Bildschirm" hinzufügen
