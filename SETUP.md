# Setup-Anleitung: Auss.Zeit Haustechnik Wiki

Schritt-für-Schritt-Anleitung für die Erstinstallation auf GitHub.

## ⏱️ Aufwand
ca. **15-20 Minuten** für komplettes Setup mit Live-Site.

---

## Schritt 1: GitHub-Account & Repo

### 1.1 GitHub-Account
Falls noch nicht vorhanden: https://github.com/signup → Account anlegen.

### 1.2 Neues Repository erstellen
1. Auf https://github.com/new gehen
2. **Repository name**: `auss-zeit-haustechnik`
3. **Description**: *Internes Wiki für Haustechnik der Auss.Zeit OG*
4. **Privat** auswählen ✅ (wichtig – nicht öffentlich!)
5. **NICHT** "Add a README", "Add .gitignore" oder "Add a license" anhaken
   (das alles ist im ZIP schon drin)
6. **Create repository** klicken

### 1.3 Elisabeth als Collaborator hinzufügen
1. Im Repo: **Settings** → **Collaborators** → **Add people**
2. Ihren GitHub-Benutzernamen oder E-Mail eingeben
3. Sie bekommt eine Einladung per Mail

---

## Schritt 2: Inhalte hochladen

Du hast zwei Wege – such dir den passenden aus.

### Variante A: Per Web-Upload (kein Terminal nötig)

1. ZIP-Datei `auss-zeit-haustechnik.zip` lokal entpacken
2. Im neuen GitHub-Repo: **uploading an existing file** klicken
3. Alle Dateien & Ordner aus dem entpackten Ordner per Drag&Drop hochladen
   - ⚠️ Versteckte Datei `.gitignore` mit hochladen (zeige versteckte Dateien im Datei-Explorer!)
   - ⚠️ Versteckter Ordner `.github` muss auch hochgeladen werden
4. Unten: **Commit changes**

### Variante B: Per Terminal (empfohlen wenn du Git kennst)

```bash
# ZIP entpacken
unzip auss-zeit-haustechnik.zip
cd auss-zeit-haustechnik

# Git initialisieren
git init
git add .
git commit -m "Initial wiki setup"
git branch -M main

# Mit GitHub verbinden (URL aus deinem neuen Repo)
git remote add origin https://github.com/<DEIN-USERNAME>/auss-zeit-haustechnik.git
git push -u origin main
```

---

## Schritt 3: GitHub Pages aktivieren

1. Im Repo: **Settings** → **Pages**
2. Unter **Source**: **GitHub Actions** auswählen (nicht "Deploy from branch"!)
3. Speichern

Das erste Deployment startet automatisch beim ersten Push.

### Status prüfen
- Tab **Actions** im Repo
- Du siehst den Workflow "Deploy MkDocs to GitHub Pages" laufen
- Nach ~1-2 Minuten steht da ein grünes Häkchen ✅
- URL der Site: meist `https://<DEIN-USERNAME>.github.io/auss-zeit-haustechnik/`

---

## Schritt 4: mkdocs.yml personalisieren

Nach dem ersten Deploy diese Zeilen in `mkdocs.yml` ergänzen (auskommentiert):

```yaml
site_url: https://<DEIN-USERNAME>.github.io/auss-zeit-haustechnik/

repo_name: <DEIN-USERNAME>/auss-zeit-haustechnik
repo_url: https://github.com/<DEIN-USERNAME>/auss-zeit-haustechnik
edit_uri: edit/main/docs/
```

→ Damit erscheinen Edit-Buttons direkt auf der Wiki-Seite, mit denen man eine Seite mit einem Klick auf GitHub bearbeiten kann.

---

## Schritt 5: Inhalte befüllen

Die Vorlagen sind alle mit `*(eintragen)*` markiert. Du kannst dir aussuchen:

### Schneller Weg: GitHub-Web-UI
- Im Repo eine `.md`-Datei öffnen
- Stift-Symbol oben rechts klicken
- Bearbeiten → unten: **Commit changes**
- Nach ~30s ist die Site aktualisiert

### Komfortabler Weg: Lokal mit Live-Vorschau
```bash
# Einmalig
pip install mkdocs-material

# Live-Vorschau während Bearbeitung
cd auss-zeit-haustechnik
mkdocs serve
# → http://localhost:8000

# Wenn fertig
git add .
git commit -m "Notfall-Kontakte ausgefüllt"
git push
```

### KI-unterstützt: Claude Code
```bash
cd auss-zeit-haustechnik
claude
```
Dann z.B. *"Fülle die Pelletheizung-Seite aus, wir haben eine ETA PE-K 25kW seit Baujahr 2018, Installateur war [Firmenname]"*

---

## Schritt 6 (optional): Zugriffsschutz

GitHub Pages ist standardmäßig öffentlich erreichbar. Für ein internes Wiki sind das die Optionen:

### Option A: Nur über GitHub einsehen
Wenn die Site nicht aktiviert wird (Schritt 3 überspringen), kann das Wiki nur direkt auf GitHub angesehen werden – Markdown-Rendering funktioniert da auch, nur ohne MkDocs-Komfort.

### Option B: Cloudflare Access (empfohlen)
1. Domain bei Cloudflare verwalten lassen (kostenlos)
2. **Cloudflare Access** → **Application** anlegen
3. Subdomain (z.B. `wiki.das-ausszeit.at`) auf GitHub Pages zeigen lassen
4. Login per Email-OTP – nur für berechtigte E-Mail-Adressen

→ Kostenlos für bis zu 50 Benutzer.

### Option C: Auf Hetzner-VPS / World4You hosten
Statisches Build (`mkdocs build` → Ordner `site/`) per FTP/Rsync auf eigenen Server, mit `.htaccess` Basic Auth.

---

## Schritt 7: Auf dem Handy als App

1. Wiki-URL im Mobile-Browser öffnen
2. **Browser-Menü** → **Zum Startbildschirm hinzufügen**
3. Verhält sich wie eine native App, mit Offline-Cache der zuletzt besuchten Seiten

---

## Tipps zum Befüllen

### Priorität (was zuerst)
1. ⭐⭐⭐ **[Notfall-Kontakte](docs/notfall/kontakte.md)** – die wichtigsten Telefonnummern
2. ⭐⭐⭐ **[Hauptabsperrhahn](docs/wasser/absperrhaehne.md)** – mit Foto!
3. ⭐⭐⭐ **[Hauptverteiler](docs/strom/hauptverteiler.md)** – mit Foto!
4. ⭐⭐ **[Pelletheizung](docs/heizung/pelletheizung.md)** – Modell, Bedienung
5. ⭐⭐ **[Wartungsplan jährlich](docs/wartungsplan/jaehrlich.md)** – Termine
6. ⭐ Apartments im Detail
7. ⭐ Geräte-Inventar

### Fotos einbinden
1. Foto in `docs/assets/images/` ablegen
2. In Markdown einbinden:
   ```markdown
   ![Hauptabsperrhahn Heizraum](../assets/images/hauptabsperrhahn.jpg)
   ```

### Sensible Daten
**Niemals direkt im Wiki!** Stattdessen:
- Passwortmanager wie **Bitwarden** (kostenlos, selbst hostbar) verwenden
- Im Wiki nur referenzieren: *"Login siehe Bitwarden-Eintrag 'XYZ'"*

---

## Bei Fragen

Frag mich einfach! Ich kann:
- Neue Seiten generieren ("schreib mir eine Seite über die Schließanlage")
- Bestehende Seiten anpassen
- mkdocs.yml erweitern
- Bei Cloudflare-Access-Setup helfen
- Bei Migration nach BookStack o.ä. helfen, falls du später wechseln willst
