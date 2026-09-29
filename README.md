# Swipelist – Spotify-Playlists per Swipe aufräumen

Rechts wischen = behalten. Links wischen = Menü: in andere Playlist verschieben/kopieren oder komplett entfernen.
Tippen auf das Cover spielt einen Ausschnitt, „Ganzer Song" spielt von vorne.

Kein Server, kein Backend: alles läuft im Browser. Deine Daten bleiben zwischen dir und Spotify.

## Was du brauchst
- Spotify **Premium** (Pflicht für Developer-Apps und für die Wiedergabesteuerung)
- Einen kostenlosen GitHub-Account (fürs Hosting)
- Die Spotify-App auf dem iPhone

## 1. Hosten (GitHub Pages, ~5 Minuten)
1. Auf github.com einloggen → **New repository** → Name `swipelist` → **Public** → Create.
2. „uploading an existing file" klicken → alle Dateien aus diesem Ordner reinziehen (`index.html`, `manifest.webmanifest`, `icon-180.png`, `icon-512.png`) → Commit.
3. Im Repo: **Settings → Pages** → Source: „Deploy from a branch" → Branch `main`, Ordner `/ (root)` → Save.
4. Nach 1–2 Minuten ist die App unter `https://DEINNAME.github.io/swipelist/` erreichbar.

Die Client ID kommt nicht in den Code, du gibst sie in der App ein. Das Repo darf also öffentlich sein.

## 2. Spotify-App anlegen
1. developer.spotify.com/dashboard → **Create app**.
2. Name/Beschreibung egal. **Redirect URI**: exakt `https://DEINNAME.github.io/swipelist/` (mit Slash am Ende!). Die App zeigt dir die genaue URI beim ersten Start auch an.
3. Bei „Which API/SDKs" **Web API** anhaken → Save.
4. **Client ID** kopieren.
5. Falls der Login später mit „user not registered" scheitert: unter **User Management** deine Spotify-E-Mail eintragen.

## 3. Aufs iPhone
1. URL in **Safari** öffnen → Teilen-Button → **Zum Home-Bildschirm**.
2. **Ab jetzt nur noch über das Homescreen-Icon öffnen.** Safari und die Homescreen-App haben getrennten Speicher; wenn du dich in Safari einloggst, ist die Homescreen-App trotzdem ausgeloggt.
3. Client ID einfügen → Speichern → Mit Spotify verbinden.

## Benutzung
- **Wiedergabe:** Die App steuert deine Spotify-App fern. Kommt „Kein Spotify-Gerät gefunden": Spotify kurz öffnen, irgendwas abspielen, zurück in Swipelist.
- **Ausschnitt:** startet standardmäßig bei 35 % des Songs für 20 s. Einstellbar über das Zahnrad, Auto-Play auch abschaltbar.
- **Fortschritt:** Behaltene Songs merkt sich die App pro Playlist. Du kannst jederzeit aufhören und später weitermachen.
- **Rückgängig:** Pfeil-Button unten links, macht den letzten Schritt auch bei Spotify rückgängig.
- Am Mac geht's auch per Tastatur: ← / →, Leertaste = Ausschnitt, F = ganzer Song, Z = rückgängig.
- **Demo ohne Spotify:** `…/swipelist/?demo` aufrufen.

## Bekannte Grenzen
- Nur **eigene** (oder kollaborative) Playlists, das ist eine Spotify-Regel.
- Ist ein Song mehrfach in einer Playlist, entfernt „Entfernen" alle Kopien davon.
- Verschieben in eine Playlist, in der der Song schon ist, erzeugt ein Duplikat.
- „Rückgängig" bei Lieblingssongs setzt den Song oben neu ein (Spotify kennt dort keine Position).
- Rückgängig nach Verschieben entfernt den Song aus der Ziel-Playlist, auch eine eventuell schon vorher vorhandene Kopie.
- Development Mode: max. 5 Nutzer pro App. Spotify ändert die API 2026 häufig; wenn plötzlich 403-Fehler kommen, liegt's vermutlich an einer neuen Einschränkung.
