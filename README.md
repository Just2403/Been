# 🌍 Been - Urlaubstracker

Ein interaktiver **Urlaubstracker** zum Dokumentieren und Visualisieren deiner Reisen auf einer Weltkarte. Markiere besuchte Länder, speichere Reisedetails und verwalte deine Reisehistorie!

## ✨ Features

- **🗺️ Interaktive Weltkarte**: Besuchte Länder werden grün hervorgehoben
- **📍 Reise-Management**: Füge Reisen mit Details wie Transportmittel, Unterkunft und Zeitraum hinzu
- **✈️ Flughafen-Tracking**: Speichere Flugverbindungen (z.B. Frankfurt → Bangkok)
- **📝 Bearbeitung & Löschung**: Ändere oder lösche Einträge jederzeit
- **💾 Cloud-Speicherung**: Alle Daten werden mit Firebase gespeichert
- **📱 Responsive Design**: Funktioniert auf Desktop und Mobile
- **🌙 Dark Mode**: Angenehmes Dark Theme für lange Nutzung

---

## 🚀 Schnellstart

### Voraussetzungen
- Ein **Firebase-Konto** (kostenlos unter [firebase.google.com](https://firebase.google.com) erstellen)
- Ein moderner Webbrowser

### Installation

1. **Klone das Repository**:
   ```bash
   git clone https://github.com/Just2403/Been.git
   cd Been
   ```

2. **Öffne die `been.html` Datei** direkt im Browser oder auf einem lokalen Server

3. **Firebase konfigurieren**:
   - Gehe zu [Firebase Console](https://console.firebase.google.com)
   - Erstelle ein neues Projekt
   - Aktiviere **Realtime Database**
   - Kopiere deine Firebase-Konfiguration
   - Ersetze die Konfigurationsdaten in `been.html` (Zeilen 120-128):

   ```javascript
   const firebaseConfig = {
     apiKey: "AIzaSyDEINE_ECHTE_API_KEY",
     authDomain: "dein-projekt.firebaseapp.com",
     databaseURL: "https://dein-projekt.firebaseio.com",
     projectId: "dein-projekt",
     storageBucket: "dein-projekt.appspot.com",
     messagingSenderId: "1234567890",
     appId: "1:1234567890:web:abc123..."
   };
   ```

4. **Firebase Database Regeln setzen** (für öffentliche Nutzung):
   ```json
   {
     "rules": {
       "trips": {
         ".read": true,
         ".write": true
       }
     }
   }
   ```

---

## 📖 Wie funktioniert es?

### 1️⃣ Reise hinzufügen

1. **Land auswählen**: Wähle aus dem Dropdown-Menü ein Land
2. **Transportmittel**: Wähle zwischen Flugzeug, Auto, Zug oder Bus
3. **Flughafen-Details** (nur bei Flugzeug):
   - "Von Flughafen": z.B. `Frankfurt (FRA)`
   - "Zu Flughafen": z.B. `Bangkok (BKK)`
4. **Unterkunft**: z.B. `Hotel XY`, `Airbnb`, Hostel
5. **Zeitraum**: Von- und Bis-Datum wählen
6. **Speichern**: Klicke "Eintragen"

### 2️⃣ Karte verstehen

- **🟢 Grün**: Du warst dort
- **🔘 Dunkelgrau**: Du warst noch nicht dort
- Die Karte aktualisiert sich automatisch, wenn du neue Länder hinzufügst

### 3️⃣ Reiseverlauf verwalten

- **📋 Reisehistorie**: Alle deine Reisen werden chronologisch (neueste zuerst) angezeigt
- **✏️ Bearbeiten**: Klick auf "Bearbeiten", um eine Reise zu ändern
- **🗑️ Löschen**: Klick auf "Löschen", um einen Eintrag zu entfernen

### 4️⃣ Daten speichern

Alle Änderungen werden **automatisch** in der Firebase-Datenbank gespeichert:
- Neue Reisen
- Bearbeitete Einträge
- Gelöschte Reisen

---

## 🛠️ Technologie & Abhängigkeiten

| Technologie | Verwendung |
|-------------|-----------|
| **HTML5** | Markup & Struktur |
| **CSS3** | Styling & Responsive Design |
| **JavaScript** | Logik & Interaktivität |
| **Leaflet.js** | Interaktive Kartendarstellung |
| **OpenStreetMap** | Kartendaten |
| **Firebase Realtime DB** | Cloud-Datenspeicherung |
| **GeoJSON** | Ländergrenzen & Daten |

### External Libraries
- [Leaflet.js v1.9.3](https://leafletjs.com/) - Kartenbibliothek
- [Firebase SDK v8.10.0](https://firebase.google.com/docs/database) - Echtzeit-Datenbank
- [World GeoJSON](https://github.com/johan/world.geo.json) - Ländergrenzen

---

## 🎨 Design & Farben

```css
Hintergrund:     #121212 (Dunkelgrau)
Karten-Box:      #1e1e1e (Dunkelgrau)
Besuchte Länder: #3fcf3f (Grün)
Bearbeiten:      #3f88cf (Blau)
Löschen:         #cf3f3f (Rot)
Text:            #fff (Weiß)
```

---

## 📋 Projektstruktur

```
Been/
├── been.html          # Hauptanwendung (All-in-One)
├── README.md          # Diese Datei
└── .gitignore         # (Optional) Firebase-Secrets ignorieren
```

**Hinweis**: Alles ist in einer einzigen HTML-Datei enthalten für einfache Bereitstellung.

---

## 🔐 Sicherheit & Tipps

### ⚠️ Wichtig für Produktion

1. **Nicht kommittiere Firebase-Secrets** in Git!
   - Erstelle eine `.gitignore` Datei:
   ```
   *.env
   firebase-config.js
   ```

2. **Firebase Security Rules** einrichten (nicht öffentlich):
   ```json
   {
     "rules": {
       "trips": {
         ".read": "auth != null",
         ".write": "auth != null"
       }
     }
   }
   ```

3. **GitHub Secrets nutzen** (falls du einen Server einsetzt)

---

## 🎯 Verwendungsbeispiele

### Beispiel 1: Einfache Landreise
- Land: Deutschland
- Transport: Auto
- Unterkunft: Camping an der Ostsee
- Zeitraum: 2025-06-01 bis 2025-06-10

### Beispiel 2: Fernreise mit Flug
- Land: Südkorea
- Transport: Flugzeug
- Flughäfen: Berlin (BER) → Incheon (ICN)
- Unterkunft: Airbnb in Seoul
- Zeitraum: 2025-09-15 bis 2025-09-29

---

## 🚀 Zukünftige Erweiterungen (TODOs)

- [ ] **Multi-User Support**: Mehrere Benutzer verwalten
- [ ] **Authentifizierung**: Login/Registrierung
- [ ] **Statistiken**: Anzahl der Länder, gesamte Reisezeit
- [ ] **Fotos hochladen**: Bilder zu Reisen hinzufügen
- [ ] **Budget-Tracking**: Reisekosten verwalten
- [ ] **Social Sharing**: Reisen teilen
- [ ] **Offline-Modus**: Lokale Speicherung
- [ ] **Export**: Daten als PDF/CSV exportieren
- [ ] **Kategorien**: Urlaubstypen (Abenteuer, Strand, Kultur, etc.)
- [ ] **Favoriten**: Länder markieren als Wunschreiseziele

---

## 🤝 Beitragen

Hast du Verbesserungsideen? Gerne kannst du:
1. **Issues erstellen** für Bugs oder Features
2. **Pull Requests** einreichen
3. **Feedback geben** zur Benutzererfahrung

---

## 📝 Lizenz

Dieses Projekt ist **Open Source** und frei verwendbar. Keine spezifische Lizenz gesetzt.

---

## 🎓 Lernquellen

- [Leaflet.js Dokumentation](https://leafletjs.com/reference.html)
- [Firebase Realtime Database](https://firebase.google.com/docs/database)
- [GeoJSON Specs](https://geojson.org/)
- [MDN Web Docs](https://developer.mozilla.org)

---

## 📧 Kontakt & Support

- **Autor**: Just2403
- **GitHub**: [Just2403/Been](https://github.com/Just2403/Been)
- **Fragen?**: Erstelle ein Issue im Repository

---

**Viel Spaß mit deinem Urlaubstracker! 🌍✈️🗺️**