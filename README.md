# Auss.Zeit Haustechnik Wiki

Internes Wiki für Haustechnik, Wartung und Notfälle der Auss.Zeit OG, Außervillgraten.

## 🌐 Live-Wiki

Zu finden unter: `https://<username>.github.io/auss-zeit-haustechnik/` (nach erstem Deploy)

## ✏️ Wiki bearbeiten

### Variante A: Direkt auf GitHub (einfach)

1. Datei in `docs/` öffnen
2. Stift-Symbol oben rechts klicken
3. Markdown bearbeiten
4. Unten **Commit changes** klicken
5. In ~30 Sekunden ist die Änderung online

### Variante B: Lokal mit Live-Vorschau (für größere Änderungen)

Voraussetzung: Python 3.9+ installiert.

```bash
# Repo klonen
git clone https://github.com/<username>/auss-zeit-haustechnik.git
cd auss-zeit-haustechnik

# Abhängigkeiten installieren (einmalig)
pip install mkdocs-material

# Lokalen Server starten
mkdocs serve

# → http://localhost:8000 im Browser öffnen
# Änderungen werden live angezeigt
```

Wenn alles passt:

```bash
git add .
git commit -m "Heizung: Wartungsintervall ergänzt"
git push
```

### Variante C: Mit Claude Code

```bash
cd auss-zeit-haustechnik
claude
```

Dann z.B.: *"Lege eine neue Seite docs/heizung/jahresservice-2026.md an mit Protokoll vom Service am 15.10.2026"*

## 📁 Struktur

```
docs/
├── notfall/           # Was tun bei Stromausfall, Wasserrohrbruch, etc.
├── heizung/           # Pelletheizung, Wartung, Fehlercodes
├── wasser/            # Absperrhähne, Boiler, Frostschutz
├── strom/             # Verteiler, Sicherungen
├── netzwerk/          # WLAN, Router, Feratel
├── apartments/        # Technik je Apartment
├── geraete/           # Inventarliste mit Wartungsdaten
└── wartungsplan/      # Jahres- und Saisonpläne
```

## 🔐 Sensible Daten

**Keine Passwörter, API-Keys oder Bankdaten ins Wiki!**

Stattdessen:
- WLAN-Passwörter, Admin-Logins → Bitwarden / 1Password
- Im Wiki nur referenzieren: *"Login siehe Bitwarden Eintrag 'Heizung Webinterface'"*

## 📱 Als App auf dem Handy

Die Site ist PWA-fähig: Im Handy-Browser öffnen → Menü → "Zum Startbildschirm hinzufügen". Verhält sich dann wie eine native App.
