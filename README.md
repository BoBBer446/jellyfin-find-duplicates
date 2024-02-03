Um das `jellyfin-find-duplicates` Script zu verwenden, folge diesen Schritten, beginnend mit dem Klonen des Git-Repositories bis hin zur Ausführung des Scripts, um Duplikate in deiner Jellyfin-Bibliothek zu finden. Diese Anleitung setzt voraus, dass du grundlegende Kenntnisse im Umgang mit der Kommandozeile und Git hast, sowie Zugriff auf einen Server oder PC mit installiertem Git, curl, und jq.

### 1. Git Repository klonen

Zuerst musst du das Git-Repository, das das `jellyfin-find-duplicates` Script enthält, auf deinen Server oder deinen lokalen Computer klonen. Angenommen, das Repository ist öffentlich auf GitHub verfügbar:

```bash
git clone https://github.com/deinBenutzername/jellyfin-find-duplicates.git
cd jellyfin-find-duplicates
```

Ersetze `https://github.com/deinBenutzername/jellyfin-find-duplicates.git` mit der tatsächlichen URL des Git-Repositories.

### 2. Abhängigkeiten installieren

Stelle sicher, dass die Abhängigkeiten `curl` und `jq` installiert sind. Auf Debian-basierten Systemen kannst du sie mit folgendem Befehl installieren:

```bash
sudo apt update && sudo apt install curl jq -y
```

### 3. Konfigurationsdatei vorbereiten

Innerhalb des geklonten Repositories findest du eine Beispielkonfigurationsdatei, z.B. `jellyfin-find-duplicates.conf.example`. Kopiere diese Datei zu deinem `$XDG_CONFIG_HOME` Verzeichnis, oder, falls diese Umgebungsvariable nicht gesetzt ist, in dein `~/.config` Verzeichnis:

```bash
cp jellyfin-find-duplicates.conf.example ~/.config/jellyfin-find-duplicates.conf
```

### 4. Konfigurationsdatei bearbeiten

Öffne die Konfigurationsdatei mit einem Texteditor deiner Wahl:

```bash
nano ~/.config/jellyfin-find-duplicates.conf
```

Bearbeite die Datei, um die erforderlichen Konfigurationsvariablen anzupassen:

- `JELLYFIN_HOST`: Die URL deines Jellyfin-Servers, z.B. `https://jellyfin.meinserver.de`.
- `JELLYFIN_TOKEN`: Ein API-Token, den du im Jellyfin-Dashboard unter "Erweitert" → "API-Schlüssel" erstellen kannst.
- `JELLYFIN_USER`: Der Benutzername des Jellyfin-Benutzers, den du verwenden möchtest.
- `JELLYFIN_SHOWS_LIB_NAME`: Der Name der Bibliothek in Jellyfin, die deine TV-Serien enthält.
- `JELLYFIN_MOVIES_LIB_NAME`: Der Name der Bibliothek, die deine Filme enthält.

Speichere die Änderungen und schließe den Editor.

### 5. Script ausführen

Stelle sicher, dass das Script ausführbar ist. Wenn nötig, ändere die Berechtigungen des Scripts:

```bash
chmod +x jellyfin-find-duplicates.sh
```

Führe nun das Script aus, um nach doppelten TV-Serienepisoden und Filmen zu suchen:

```bash
./jellyfin-find-duplicates.sh
```

Das Script wird nun deine Jellyfin-Bibliotheken durchsuchen und Informationen über gefundene Duplikate ausgeben. Wenn keine Duplikate gefunden werden, endet das Script ohne Ausgabe.

Durch diese Schritte hast du das `jellyfin-find-duplicates` Script erfolgreich eingerichtet und ausgeführt, um Duplikate in deiner Jellyfin-Medienbibliothek zu finden.
