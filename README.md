# 📘 Silver-Car - Limousinen Service – Projekt Silver-Car

## Umfassende Projektplanung & Design-Dokumentation (Version 3.0)

**Erstellt:** 28. Februar 2026  
**Projekt:** Silver-Car - Limousinen Service Website + Desktop App  
**Basis:** Brainstorm (Silver-Car_plan.md) + Design-Analysen (Silver-Car_style_webseite.md + Silver-Car_style_desktop_app.md)

---

## 📑 Inhaltsverzeichnis

| Kapitel | Inhalt                                           | Seite |
| ------- | ------------------------------------------------ | ----- |
| 1       | Projekt-Übersicht                                | 3     |
| 2       | Website Design & Struktur                        | 4     |
| 3       | Desktop App Design & Struktur                    | 12    |
| 4       | Rechtliche Anforderungen (DSGVO, Impressum, AGB) | 20    |
| 5       | Technische Architektur                           | 24    |
| 6       | Sicherheitskonzept                               | 28    |
| 7       | Implementierungs-Plan                            | 31    |
| 8       | Kosten- & Zeitplanung                            | 35    |
| 9       | Anhang & Referenzen                              | 37    |

---

## 1️⃣ PROJEKT-ÜBERSICHT

### 1.1 Projekt-Ziel

Entwicklung einer Premium-Limousinen-Mietplattform mit:

- **Öffentlicher Website** für Kundenakquise & Buchungen
- **Desktop App** für interne Verwaltung (Kunden, Termine, Mitarbeiter, Marketing)
- **DSGVO-konformer** Datenverarbeitung
- **Premium-Design** angelehnt an Automotive-Industry-Standards

### 1.2 Zielgruppen

| Zielgruppe      | Beschreibung                   | Zugang                   |
| --------------- | ------------------------------ | ------------------------ |
| **Gäste**       | Webseitenbesucher ohne Account | Öffentlich               |
| **Kunden**      | Registrierte Nutzer mit Login  | Nach Registrierung       |
| **Mitarbeiter** | Interne Nutzer der Desktop App | Nach Autorisierung       |
| **Admin**       | Vollzugriff auf alle Systeme   | Nach Autorisierung + 2FA |

### 1.3 Kernfunktionen im Überblick

```
┌─────────────────────────────────────────────────────────────────────┐
│                      SILVER-CAR SYSTEM                              │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  WEBSITE (Public)                    DESKTOP APP (Internal)         │
│  ┌─────────────────────────┐         ┌─────────────────────────┐   │
│  │ • Landingpage           │         │ • Kundenverwaltung      │   │
│  │ • Fuhrpark-Show         │         │ • Terminplanung         │   │
│  │ • Einzelfahrzeug-Show   │         │ • Mitarbeiter-Einteilung│   │
│  │ • Kalkulator (Km/Route) │         │ • Vertragsbestätigung   │   │
│  │ • Kontaktformular       │         │ • E-Mail-Marketing      │   │
│  │ • Gast: Termin-Info     │         │ • Reports & Analytics   │   │
│  │ • Kunde: Buchung        │         │ • Fahrzeug-Wartung      │   │
│  │ • Info-Service (Verkehr)│         │ • Systemeinstellungen   │   │
│  └─────────────────────────┘         └─────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 2️⃣ WEBSITE DESIGN & STRUKTUR

### 2.1 Design-Prinzipien (Premium Automotive Style)

| Prinzip              | Umsetzung                                              |
| -------------------- | ------------------------------------------------------ |
| **Premium-Feeling**  | Viel Weißraum, hochwertige Bilder, dezente Animationen |
| **Klarheit**         | Ein Ziel pro Section, klare Hierarchie                 |
| **Konsistenz**       | 8px-Grid-System, einheitliche Farben & Typografie      |
| **Vertrauen**        | Testimonials, Zertifikate, transparente Preise         |
| **Conversion**       | CTA auf jeder Section sichtbar                         |
| **Barrierefreiheit** | WCAG 2.1 AA Kontraste, Screenreader-Tauglichkeit       |
| **Performance**      | Ladezeit < 3 Sekunden, optimierte Bilder               |

### 2.2 Farbpalette (Silver-Car Brand)

| Farbe             | Hex-Code  | Verwendung                         |
| ----------------- | --------- | ---------------------------------- |
| **Silver Dark**   | `#1A1A1A` | Headlines, Primary Buttons, Footer |
| **Silver Medium** | `#4A4A4A` | Sekundärer Text, Borders           |
| **Silver Light**  | `#F5F5F5` | Hintergrund, Cards                 |
| **Pure White**    | `#FFFFFF` | Card-Hintergrund, Kontrast         |
| **Silver Accent** | `#C0C0C0` | Hover-States, Highlights           |
| **Gold Optional** | `#D4AF37` | Premium-CTAs (sparsam)             |

### 2.3 Typografie

| Ebene          | Schrift                       | Größe | Gewicht         | Zeilenhöhe |
| -------------- | ----------------------------- | ----- | --------------- | ---------- |
| **H1 Hero**    | Montserrat / Playfair Display | 48px  | Bold (700)      | 1.2        |
| **H2 Section** | Montserrat                    | 32px  | Semi-Bold (600) | 1.3        |
| **H3 Card**    | Montserrat                    | 22px  | Medium (500)    | 1.4        |
| **Body**       | Open Sans / Lato              | 16px  | Regular (400)   | 1.6        |
| **Small**      | Open Sans / Lato              | 14px  | Regular (400)   | 1.5        |

**Lizenzhinweis:** Google Fonts (lizenzfrei) oder gekaufte Fonts verwenden. Keine Raubkopien.

### 2.4 Seitenstruktur (Sitemap)

```
┌─────────────────────────────────────────────────────────────────────┐
│                         WEBSITE NAVIGATION                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  HOME                                                               │
│  ├── Services                                                       │
│  │   ├── Flughafen-Transfer                                         │
│  │   ├── Hochzeit                                                   │
│  │   ├── Business                                                   │
│  │   └── Events                                                     │
│  ├── Fuhrpark                                                       │
│  │   ├── Limousinen                                                 │
│  │   ├── Vans                                                       │
│  │   ├── SUVs                                                       │
│  │   └── Spezialfahrzeuge                                           │
│  ├── Preise & Kalkulator                                            │
│  ├── Über Uns                                                       │
│  ├── Kontakt                                                        │
│  ├── Registrierung / Login                                          │
│  └── Rechtliches                                                    │
│      ├── Impressum                                                  │
│      ├── Datenschutz                                                │
│      ├── AGB                                                        │
│      └── Stornobedingungen                                          │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### 2.5 Landingpage – Section-Übersicht

| Section          | Inhalt                                            | CTA                 |
| ---------------- | ------------------------------------------------- | ------------------- |
| **Hero**         | Premium-Fahrzeugbild/Video, Headline, Subline     | "Jetzt Buchen"      |
| **Services**     | 4 Kacheln (Flughafen, Hochzeit, Business, Events) | "Mehr erfahren"     |
| **Fuhrpark**     | 5-6 Fahrzeug-Cards mit Details                    | "Fahrzeug ansehen"  |
| **Kalkulator**   | Kilometer-Eingabe oder Route (OpenMap)            | "Preis berechnen"   |
| **Vorteile**     | 4 Icon-Cards (Pünktlich, Diskret, Komfort, 24/7)  | –                   |
| **Testimonials** | 2-3 Kundenbewertungen                             | –                   |
| **Kontakt**      | Formular, Telefon, E-Mail, Adresse                | "Kontakt aufnehmen" |
| **Footer**       | Navigation, Rechtliches, Social Media             | –                   |

### 2.6 Fuhrpark-Show (Gesamtübersicht)

**Layout:** Grid-System, 3 Spalten (Desktop), 2 (Tablet), 1 (Mobile)

**Je Fahrzeug-Card:**

```
┌─────────────────────────────────────────┐
│                                         │
│         [Fahrzeugbild 4:3 oder 1:1]     │
│                                         │
├─────────────────────────────────────────┤
│  Fahrzeugname (H3, 22px, Bold)          │
│  ─────────────────────────────────      │
│  • Passagiere: X                        │
│  • Koffer: X                            │
│  • Ausstattung: [Icons]                 │
│  • Preis: ab XXX EUR                    │
│                                         │
│  [Button: "Details ansehen"]            │
└─────────────────────────────────────────┘
```

### 2.7 Einzelfahrzeug-Show (Detailseite)

**Inhalt:**

- Großbild-Galerie (5-10 Bilder)
- Fahrzeug-Spezifikationen (Tabelle)
- Ausstattung (Checkliste mit Icons)
- Preisübersicht (Tabelle nach Kilometer/Stunden)
- Verfügbarkeits-Kalender
- Buchungsformular (für Kunden) / Anfrageformular (für Gäste)

**Spezifikations-Tabelle:**
| Eigenschaft | Wert |
|-------------|------|
| Fahrzeugtyp | Limousine |
| Modell | Mercedes S-Klasse (Beispiel) |
| Baujahr | 2024 |
| Passagiere | 4 |
| Koffer | 3 |
| Farbe | Schwarz / Silber |
| Ausstattung | Leder, Klima, WLAN, Getränke, ... |

### 2.8 Kalkulator (Mietkosten)

**Funktionsweise:**

1. **Direkte Kilometer-Eingabe:** Gast gibt Strecke in km ein
2. **OpenMap Route:** Gast gibt Start & Ziel ein, System berechnet Distanz
3. **Fahrzeug-Auswahl:** Gast wählt Fahrzeug-Kategorie
4. **Preis-Berechnung:** System zeigt Mietkosten basierend auf km + Fahrzeug

**Preis-Formel (Beispiel):**

```
Grundpreis + (Kilometer × Preis pro km) + Zusatzleistungen = Gesamtpreis
```

**UI-Layout:**

```
┌─────────────────────────────────────────────────────────────────┐
│  PREIS-KALKULATOR                                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. FAHRZEUG AUSWÄHLEN                                          │
│  [Limousine ▼] [Van ▼] [SUV ▼] [Spezial ▼]                      │
│                                                                 │
│  2. STRECKE EINGEBEN                                            │
│  ○ Direkte Kilometer: [________ km]                             │
│  ○ Route berechnen: [Start __________] → [Ziel __________]      │
│                                                                 │
│  3. ZUSATZLEISTUNGEN                                            │
│  ☐ Getränke-Paket (+50 EUR)                                     │
│  ☐ Dekorations-Paket (+150 EUR)                                 │
│  ☐ Mehrsprachiger Fahrer (+100 EUR)                             │
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│  GESAMTPREIS: [________ EUR]                                    │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  [Als Gast anfragen] [Als Kunde buchen]                         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 2.9 Info-Service (Straßenverkehr)

**Funktionen:**

- Stau-Informationen (API: Google Maps / TomTom)
- Fahrverbote (Umweltzonen, Feiertage)
- Freie Fahrt (Baustellen, Sperrungen)
- Wetter-Einfluss (bei Buchung anzeigen)

**Anzeige:**

- Auf Buchungsseite vor Bestätigung
- Optional als Widget auf Homepage
- Push-Benachrichtigung für Kunden vor Fahrt

### 2.10 Kontakt & Anfrage

| Funktion                         | Gast | Kunde |
| -------------------------------- | ---- | ----- |
| **Kontaktformular**              | ✓    | ✓     |
| **Termin-Info (unverbindlich)**  | ✓    | ✓     |
| **Termin-Buchung (verbindlich)** | ✗    | ✓     |
| **Telefon**                      | ✓    | ✓     |
| **E-Mail**                       | ✓    | ✓     |
| **WhatsApp**                     | ✓    | ✓     |

**Kontaktformular-Felder:**

- Name (Pflicht)
- E-Mail (Pflicht)
- Telefon (Pflicht)
- Nachricht (Pflicht)
- Service-Typ (Dropdown)
- Gewünschtes Datum (Optional)
- Datenschutz-Checkbox (Pflicht)

### 2.11 Registrierung & Login (Gast → Kunde)

**Registrierungs-Workflow:**

```
1. Gast füllt Registrierungsformular aus
   • Name, E-Mail, Telefon, Passwort
   • Datenschutz-Akzeptanz (Pflicht)
   • Newsletter-Opt-In (Optional)

2. System sendet E-Mail mit Auth-Daten
   • Bestätigungslink (Double-Opt-In)
   • Temporäres Passwort oder Aktivierungslink

3. Gast bestätigt E-Mail
   • Account wird aktiviert
   • Gast ist jetzt Kunde

4. Kunde loggt sich ein
   • Volle Buchungsfunktionalität freigeschaltet
```

**Login-Sicherheit:**

- Passwort: Min. 12 Zeichen, Sonderzeichen, Zahlen
- 2FA optional für Kunden (empfohlen)
- Session-Timeout: 30 Minuten Inaktivität
- Passwort-Reset über E-Mail

---

## 3️⃣ DESKTOP APP DESIGN & STRUKTUR

### 3.1 App-Übersicht

**Zweck:** Interne Verwaltung für Webseitenbetreiber & Mitarbeiter

**Hauptmodule:**
| Modul | Funktion | Nutzer |
|-------|----------|--------|
| **Kundenverwaltung** | Kunden-Daten CRUD, Historie | Admin, Manager |
| **Terminplanung** | Kalender, Buchungen, Status | Admin, Manager, Disponent |
| **Mitarbeiter-Einteilung** | Fahrer-Zuweisung, Schichten | Admin, Manager, Disponent |
| **Vertragsbestätigung** | PDF-Generierung, Versand | Admin, Manager |
| **E-Mail-Marketing** | Kampagnen, Verteiler, Templates | Admin, Manager |
| **Reports & Analytics** | Umsatz, Buchungen, KPIs | Admin, Manager |
| **Fahrzeug-Wartung** | Wartungsplan, Status | Admin, Manager |
| **Systemeinstellungen** | User, Rollen, Sicherheit | Admin |

### 3.2 Kundenverwaltung

**Datenstruktur:**
| Feld | Typ | Pflicht | DSGVO-Hinweis |
|------|-----|---------|----------------|
| Kunden-ID | Auto-Increment | Ja | Intern |
| Vorname | Text | Ja | Personenbezogen |
| Nachname | Text | Ja | Personenbezogen |
| E-Mail | E-Mail | Ja | Personenbezogen, Login |
| Telefon | Text | Ja | Personenbezogen |
| Adresse | Text | Nein | Personenbezogen, optional |
| Registrierungsdatum | Datum | Ja | Intern |
| Newsletter-Opt-In | Boolean | Nein | Dokumentiert speichern |
| Kundenstatus | Enum | Ja | Aktiv, Inaktiv, Gesperrt |
| Löschvermerk | Datum | Nein | Für DSGVO-Löschfrist |

**Funktionen:**

- Kunden suchen (Name, E-Mail, Telefon)
- Kunden-Detailansicht (alle Daten + Buchungshistorie)
- Kunden bearbeiten (CRUD)
- Kunden exportieren (CSV/PDF für Art. 20 DSGVO)
- Kunden löschen (Soft-Delete + Frist-Tracking für Art. 17 DSGVO)
- Zugriffs-Log (wer hat auf Daten zugegriffen?)

### 3.3 Terminplanung

**Kalender-Ansichten:**

- Tag (Stunden-Raster)
- Woche (Übersicht aller Fahrten)
- Monat (Übersicht aller Buchungen)

**Buchungs-Status:**
| Status | Farbe | Beschreibung |
|--------|-------|--------------|
| **Offen** | 🟡 Gelb | Anfrage eingegangen, noch nicht bestätigt |
| **Bestätigt** | 🟢 Grün | Vertrag bestätigt, Fahrer zugewiesen |
| **Im Einsatz** | 🔵 Blau | Fahrt läuft gerade |
| **Abgeschlossen** | ⚫ Grau | Fahrt erfolgreich beendet |
| **Storniert** | 🔴 Rot | Buchung storniert |

**Funktionen:**

- Neue Buchung manuell erstellen
- Buchung aus Website automatisch übernehmen
- Fahrzeug zuweisen (mit Verfügbarkeitsprüfung)
- Fahrer zuweisen (mit Verfügbarkeitsprüfung)
- Konflikterkennung (Doppelbuchungen, Überlastung)
- Status ändern (mit automatischer Kunden-Benachrichtigung)

### 3.4 Mitarbeiter-Einteilung

**Mitarbeiter-Daten:**
| Feld | Typ | Hinweis |
|------|-----|---------|
| Mitarbeiter-ID | Auto-Increment | Intern |
| Name | Text | Vollständiger Name |
| Rolle | Enum | Admin, Manager, Disponent, Fahrer, Support |
| Schicht | Zeit | 08:00-16:00, 14:00-22:00, etc. |
| Status | Enum | Verfügbar, Im Einsatz, Urlaub, Krank |
| Max. Fahrten/Tag | Integer | z.B. 4 Fahrten |
| Kontakt | Text | Telefon, E-Mail |

**Einteilungs-UI:**

- Verfügbare Fahrer anzeigen (gefiltert nach Datum/Zeit)
- Fahrer manuell zuweisen
- Automatische Vorschläge (basierend auf Verfügbarkeit)
- Urlaub/Krankheit markieren (automatisch ausblenden)
- Auslastung pro Fahrer anzeigen

### 3.5 Vertragsbestätigung

**Workflow:**

```
1. Buchung wird bestätigt (Fahrzeug + Fahrer zugewiesen)
2. PDF-Vertrag wird generiert (automatisch)
3. PDF wird an Kunden per E-Mail versendet
4. Status auf "Bestätigt" setzen
5. Kopie in Datenbank speichern (10 Jahre Aufbewahrung)
```

**PDF-Inhalt:**

- Silver-Car Logo & Adresse
- Kundendaten (Name, Adresse, Kontakt)
- Buchungsdetails (Datum, Uhrzeit, Service, Fahrzeug, Fahrer)
- Preisaufstellung (Basis, Zusatzleistungen, MwSt., Gesamt)
- AGB (vollständig oder Link)
- Stornobedingungen
- Platzhalter für digitale Signatur
- Datum & Stempel (automatisch)

**E-Mail-Template:**

- Betreff: "Buchungsbestätigung Silver-Car #SC-2026-XXXXX"
- Anhang: PDF-Vertrag
- Text: Persönliche Anrede, Buchungsdetails, Kontaktinfo
- Footer: Impressum, Datenschutz, Abmeldelink

### 3.6 E-Mail-Marketing

**Rechtliche Anforderungen:**
| Anforderung | Umsetzung |
|-------------|-----------|
| **Double-Opt-In** | Bestätigungs-E-Mail nach Anmeldung |
| **Abmeldelink** | In jeder Marketing-E-Mail Pflicht |
| **Verteiler-Log** | Wer hat welche Mails erhalten? |
| **Bounce-Handling** | Ungültige E-Mails automatisch entfernen |
| **Datenminimierung** | Nur E-Mail + Name für Marketing |

**Verteiler-Listen:**
| Liste | Beschreibung |
|-------|--------------|
| **Alle Kunden** | Alle registrierten Kunden |
| **Newsletter** | Kunden mit Opt-In |
| **Hochzeits-Kunden** | Kunden mit Hochzeit-Buchung |
| **Business-Kunden** | Kunden mit Business-Buchung |
| **Inaktive Kunden** | Keine Buchung in 6+ Monaten |

**Kampagnen-Typen:**
| Typ | Anlass | Frequenz |
|-----|--------|----------|
| **Willkommen** | Nach Registrierung | Automatisch |
| **Buchungsbestätigung** | Nach Buchung | Automatisch |
| **Erinnerung** | 24h vor Fahrt | Automatisch |
| **Feedback** | Nach abgeschlossener Fahrt | Automatisch |
| **Sonderangebot** | Saisonale Aktionen | Manuell |
| **Newsletter** | Monatlich | Manuell |
| **Geburtstag** | Kunden-Geburtstag | Automatisch |

**Kampagnen-Stats:**

- Gesendete E-Mails
- Öffnungsrate (%)
- Klickrate (%)
- Bounce-Rate (%)
- Abmeldungen

### 3.7 Reports & Analytics

**Verfügbare Reports:**
| Report | Inhalt | Export |
|--------|--------|--------|
| **Umsatz** | Täglich, Wöchentlich, Monatlich, Jährlich | PDF, CSV |
| **Buchungen** | Nach Service-Typ, Fahrzeug, Fahrer | PDF, CSV |
| **Kunden** | Neukunden, Bestandskunden, Inaktiv | PDF, CSV |
| **Fahrzeug-Auslastung** | Utilization pro Fahrzeug | PDF, CSV |
| **Fahrer-Performance** | Fahrten pro Fahrer, Bewertungen | PDF, CSV |
| **E-Mail-Statistik** | Öffnungsraten, Klicks, Bounces | PDF, CSV |

**Dashboard-KPIs:**

- Buchungen diese Woche
- Umsatz diesen Monat
- Fahrzeug-Auslastung (%)
- Neukunden
- Nächste Fahrten (Liste)
- Offene Buchungen (Liste)
- Fahrer-Status (Verfügbar/Im Einsatz/Krank)

---

## 4️⃣ RECHTLICHE ANFORDERUNGEN

### 4.1 DSGVO (Datenschutz-Grundverordnung)

**Kundendaten-Schutz:**
| Anforderung | Umsetzung |
|-------------|-----------|
| **Datenminimierung** | Nur notwendige Felder speichern |
| **Zweckbindung** | Daten nur für Buchung/Vertrag nutzen |
| **Speicherbegrenzung** | Löschfristen definieren (z.B. 3 Jahre nach letzter Buchung) |
| **Sicherheit** | Verschlüsselung (AES-256), Zugriffskontrolle |
| **Transparenz** | Datenschutzerklärung klar & verständlich |
| **Betroffenenrechte** | Export (Art. 20), Löschung (Art. 17), Auskunft (Art. 15) |

**Technische Maßnahmen:**

- Datenbank-Verschlüsselung (AES-256)
- TLS 1.3 für Datenübertragung
- Zugriffs-Log (wer hat wann auf was zugegriffen)
- Regelmäßige Sicherheits-Audits
- Backup (täglich, verschlüsselt, extern)

**Dokumentation:**

- Verzeichnis von Verarbeitungstätigkeiten (VVT)
- Auftragsverarbeitungsverträge (AVV) mit Dienstleistern
- Datenschutz-Folgenabschätzung (DSFA) bei Risiken

### 4.2 Impressum (§ 5 TMG)

**Pflichtangaben:**

- Vollständiger Name (Firma)
- Vollständige Adresse
- Kontakt (Telefon, E-Mail)
- Vertretungsberechtigte Personen
- Handelsregister (falls eingetragen)
- Umsatzsteuer-ID (falls vorhanden)
- Berufshaftpflichtversicherung (falls relevant)
- Streitbeilegung (OS-Plattform)

**Platzierung:**

- Footer-Link auf jeder Seite
- Direkt erreichbar (max. 2 Klicks von Homepage)
- Klar als "Impressum" gekennzeichnet

### 4.3 AGB (Allgemeine Geschäftsbedingungen)

**Inhalt:**

- Geltungsbereich
- Vertragsabschluss (Buchungsprozess)
- Preise & Zahlung
- Stornobedingungen (Fristen, Kosten)
- Haftungsausschluss
- Datenschutz-Hinweis
- Gerichtsstand

**Platzierung:**

- Footer-Link auf jeder Seite
- Bei Buchung: Checkbox "AGB akzeptiert" (Pflicht)
- Als PDF downloadbar

### 4.4 Cookie-Banner

**Anforderungen:**

- Vor Laden von Cookies einholen (Opt-In)
- Kategorien erklären (Notwendig, Statistik, Marketing)
- Widerrufbar jederzeit
- Dokumentation der Einwilligungen

**Umsetzung:**

- Banner bei erstem Besuch
- Einstellungen speicherbar
- Cookie-Liste öffentlich einsehbar

### 4.5 GoBD (Grundsätze zur ordnungsmäßigen Führung und Aufbewahrung von Büchern, Aufzeichnungen und Unterlagen in elektronischer Form)

**Für Vertragsdaten:**

- 10 Jahre Aufbewahrungsfrist
- Unveränderbarkeit (Nachvollziehbarkeit)
- Revisionssichere Archivierung
- Export-Funktion für Prüfungen

---

## 5️⃣ TECHNISCHE ARCHITEKTUR

### 5.1 System-Übersicht

```
┌─────────────────────────────────────────────────────────────────────┐
│                         SILVER-CAR SYSTEM                           │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  ┌─────────────────────┐         ┌─────────────────────────────┐   │
│  │   PUBLIC WEBSITE    │         │      DESKTOP APP (Admin)    │   │
│  │   (Kunden-Frontend) │         │      (Mitarbeiter-Backend)  │   │
│  │                     │         │                             │   │
│  │  • WordPress/Webflow│         │  • Electron/.NET            │   │
│  │  • Buchungsformular │◄───────►│  • Kundenverwaltung         │   │
│  │  • Kalkulator       │  API    │  • Terminplanung            │   │
│  │  • Kunden-Login     │  REST   │  • Mitarbeiter-Einteilung   │   │
│  └─────────────────────┘         │  • E-Mail-Marketing         │   │
│                                  │  • Reports & Analytics      │   │
│                                  └─────────────────────────────┘   │
│                                           │                         │
│                                           ▼                         │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                    ZENTRALE DATENBANK                       │   │
│  │  • PostgreSQL (verschlüsselt)                               │   │
│  │  • Kunden, Buchungen, Mitarbeiter, Fahrzeuge, Verträge      │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                           │                         │
│                                           ▼                         │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                    EXTERNE SERVICES                         │   │
│  │  • E-Mail: SendGrid / Mailgun / SMTP                        │   │
│  │  • Maps: Google Maps / OpenStreetMap                        │   │
│  │  • Payment: Stripe / PayPal                                 │   │
│  │  • Backup: Cloud (täglich)                                  │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### 5.2 Tech-Stack Empfehlungen

**Website (Kunden-Frontend):**
| Komponente | Empfehlung | Alternative |
|------------|------------|-------------|
| **CMS** | WordPress + Elementor | Webflow |
| **Hosting** | All-Inkl / Strato (DE-Server) | SiteGround |
| **SSL** | Let's Encrypt (kostenlos) | Comodo |
| **E-Mail** | SMTP über Host | SendGrid / Mailgun |

**Desktop App (Admin-Backend):**
| Komponente | Empfehlung | Alternative |
|------------|------------|-------------|
| **Framework** | Electron (Cross-Platform) | .NET WPF (Windows-only) |
| **Sprache** | JavaScript/TypeScript | C# |
| **Datenbank** | PostgreSQL | MySQL |
| **API** | REST (Node.js oder PHP) | GraphQL |
| **Auth** | JWT + 2FA | OAuth2 |
| **PDF** | PDFKit / Puppeteer | iText |

### 5.3 API-Schnittstellen

**Website ↔ Desktop App:**
| Endpunkt | Methode | Beschreibung |
|----------|---------|--------------|
| `/api/bookings` | GET | Alle Buchungen abrufen |
| `/api/bookings/:id` | GET | Einzelne Buchung abrufen |
| `/api/bookings` | POST | Neue Buchung erstellen |
| `/api/bookings/:id` | PUT | Buchung aktualisieren |
| `/api/customers` | GET | Alle Kunden abrufen |
| `/api/customers/:id` | GET | Einzelnen Kunden abrufen |
| `/api/vehicles` | GET | Alle Fahrzeuge abrufen |
| `/api/staff` | GET | Alle Mitarbeiter abrufen |

**Sicherheit:**

- JWT-Token für Authentifizierung
- HTTPS für alle Requests
- Rate-Limiting (Schutz vor Missbrauch)
- Input-Validierung (Schutz vor Injection)

---

## 6️⃣ SICHERHEITSKONZEPT

### 6.1 Zugriffskontrolle

**Benutzerrollen:**
| Rolle | Rechte | Beschränkungen |
|-------|--------|----------------|
| **Admin** | Alle Rechte | Keine |
| **Manager** | Kunden, Termine, Mitarbeiter, E-Mails | Keine Systemeinstellungen |
| **Disponent** | Termine, Mitarbeiter-Einteilung | Keine Finanzdaten |
| **Fahrer** | Eigene Fahrten ansehen | Keine Kundendaten-Exporte |
| **Support** | Kunden ansehen, E-Mails senden | Keine Löschungen |

**Authentifizierung:**

- Passwort: Min. 12 Zeichen, Sonderzeichen, Zahlen
- 2FA: SMS oder Authenticator App (Pflicht für Admin/Manager)
- Session-Timeout: 30 Minuten Inaktivität
- Zugriffs-Log: Jeder Login wird protokolliert

### 6.2 Daten-Sicherheit

| Maßnahme            | Umsetzung                                         |
| ------------------- | ------------------------------------------------- |
| **Verschlüsselung** | AES-256 für Datenbank, TLS 1.3 für Transfer       |
| **Backup**          | Täglich, verschlüsselt, extern, 30 Tage Retention |
| **Firewall**        | Server-seitig, nur notwendige Ports offen         |
| **Updates**         | Regelmäßige Sicherheits-Updates (CMS, App, DB)    |
| **Audit**           | Jährliches Sicherheits-Audit durch Dritte         |

### 6.3 Notfall-Plan

| Szenario                  | Maßnahme                                                                      |
| ------------------------- | ----------------------------------------------------------------------------- |
| **Datenleck**             | Sofortige Sperrung, Benachrichtigung Betroffener, Meldung an Aufsichtsbehörde |
| **Server-Ausfall**        | Backup-Restore, Failover-Server                                               |
| **Ransomware**            | Backup-Restore, keine Zahlung, Strafverfolgung                                |
| **Mitarbeiter-Kündigung** | Sofortiger Zugriffsentzug, Passwort-Reset                                     |

---

## 7️⃣ IMPLEMENTIERUNGS-PLAN

### 7.1 Phasen-Übersicht

| Phase       | Dauer       | Inhalt                        |
| ----------- | ----------- | ----------------------------- |
| **Phase 1** | Woche 1-4   | Website Grundgerüst           |
| **Phase 2** | Woche 5-8   | Website Buchungs-System       |
| **Phase 3** | Woche 9-16  | Desktop App Kernmodule        |
| **Phase 4** | Woche 17-20 | Desktop App Erweiterte Module |
| **Phase 5** | Woche 21-24 | Integration & Testing         |
| **Phase 6** | Woche 25-26 | Launch & Schulung             |

### 7.2 Detaillierte Meilensteine

**Phase 1: Website Grundgerüst (Woche 1-4)**

- [ ] HTML-Grundstruktur erstellen
- [ ] 8px-Grid-System implementieren
- [ ] Header/Footer-Navigation
- [ ] Hero, Services, Fuhrpark Sections
- [ ] Kontaktformular
- [ ] Impressum & Datenschutz

**Phase 2: Website Buchungs-System (Woche 5-8)**

- [ ] Buchungsformular mit Validierung
- [ ] Fahrzeug-Auswahl
- [ ] Termin-Auswahl (Kalender)
- [ ] Kalkulator (Km/Route)
- [ ] Kunden-Registrierung/Login
- [ ] Buchungsbestätigung E-Mail (automatisch)

**Phase 3: Desktop App – Kernmodule (Woche 9-16)**

- [ ] Datenbank-Setup (PostgreSQL)
- [ ] Authentifizierung (Login + 2FA)
- [ ] Kundenverwaltung (CRUD)
- [ ] Terminplanung (Kalender)
- [ ] Mitarbeiter-Einteilung
- [ ] Vertrags-PDF-Generierung

**Phase 4: Desktop App – Erweiterte Module (Woche 17-20)**

- [ ] E-Mail-Marketing-System
- [ ] Verteiler-Listen-Verwaltung
- [ ] E-Mail-Templates
- [ ] Reports & Analytics
- [ ] Dashboard

**Phase 5: Integration & Testing (Woche 21-24)**

- [ ] Website ↔ App API-Integration
- [ ] End-to-End Testing
- [ ] Sicherheits-Audit
- [ ] DSGVO-Compliance-Check
- [ ] Schulung für Mitarbeiter
- [ ] Go-Live

**Phase 6: Launch & Schulung (Woche 25-26)**

- [ ] Finaler Content-Check
- [ ] Performance-Optimierung
- [ ] Mitarbeiter-Schulung (Desktop App)
- [ ] Monitoring einrichten
- [ ] Support-Prozesse definieren

---

## 8️⃣ KOSTEN- & ZEITPLANUNG

### 8.1 Kostenschätzung (Grob)

| Komponente             | Aufwand             | Kosten (ca.)          |
| ---------------------- | ------------------- | --------------------- |
| **Website**            | 80-120 Stunden      | 8.000 - 15.000 €      |
| **Desktop App**        | 200-300 Stunden     | 20.000 - 35.000 €     |
| **Datenbank & API**    | 40-60 Stunden       | 4.000 - 8.000 €       |
| **DSGVO-Beratung**     | 10-20 Stunden       | 2.000 - 5.000 €       |
| **Hosting (jährlich)** | Laufend             | 500 - 1.500 €         |
| **E-Mail-Service**     | Laufend             | 300 - 1.000 €/Jahr    |
| **Gesamt**             | **330-500 Stunden** | **35.000 - 65.000 €** |


### 8.2 Zeitplan (Gantt-Übersicht)

```
Woche:  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26
        │──────────│──────────│──────────│──────────│──────────│──────────│──────────│
Phase 1 │██████████│          │          │          │          │          │          │
Phase 2 │          │██████████│          │          │          │          │          │
Phase 3 │          │          │███████████████████│          │          │          │
Phase 4 │          │          │          │          │██████████│          │          │
Phase 5 │          │          │          │          │          │██████████│          │
Phase 6 │          │          │          │          │          │          │██████████│
```

---

## 9️⃣ ANHANG & REFERENZEN

### 9.1 Verwendete Dokumente

| Dokument                            | Version | Datum      |
| ----------------------------------- | ------- | ---------- |
| **Silver-Car_plan.md**              | 1.0     | 28.02.2026 |
| **Silver-Car_style_webseite.md**    | 1.0     | 28.02.2026 |
| **Silver-Car_style_desktop_app.md** | 1.0     | 28.02.2026 |
| **Dieses Dokument**                 | 3.0     | 28.02.2026 |

### 9.2 Externe Ressourcen

| Ressource         | Link                                    | Zweck                    |
| ----------------- | --------------------------------------- | ------------------------ |
| **DSGVO Text**    | https://dsgvo-gesetz.de/                | Rechtliche Grundlage     |
| **WCAG 2.1**      | https://www.w3.org/WAI/WCAG21/quickref/ | Barrierefreiheit         |
| **Google Fonts**  | https://fonts.google.com/               | Lizenzfreie Schriftarten |
| **OpenStreetMap** | https://www.openstreetmap.org/          | Karten-Integration       |
| **SendGrid**      | https://sendgrid.com/                   | E-Mail-Versand           |

### 9.3 Kontakt & Support

| Rolle                       | Name            | Kontakt  |
| --------------------------- | --------------- | -------- |
| **Projekt-Leitung**         | [Ihr Name]      | [E-Mail] |
| **Webseitenbetreiber**      | [Freund's Name] | [E-Mail] |
| **Entwickler**              | [Name/Agentur]  | [E-Mail] |
| **Datenschutzbeauftragter** | [Name]          | [E-Mail] |

---

## ✅ NÄCHSTE SCHRITTE

1. **Dieses Dokument finalisieren** – Alle Beteiligten einbeziehen
2. **Datenschutzbeauftragten kontaktieren** – DSGVO-Compliance sicherstellen
3. **Tech-Stack final entscheiden** – Website + App Framework
4. **Budget & Timeline festlegen** – Realistische Meilensteine
5. **Entwickler/Agentur auswählen** – Angebote einholen
6. **Logo & Branding erstellen** – Silver-Car visuelle Identität
7. **Content sammeln** – Texte, Bilder, Fahrzeug-Daten
8. **Rechtliche Texte erstellen** – Impressum, AGB, Datenschutz

---

**Viel Erfolg mit dem Silver-Car Projekt! 🚗💨**

_Dieses Dokument dient als lebendige Planungsbasis und sollte bei Änderungen entsprechend aktualisiert werden._

---

## 📝 DOKUMENTEN-HISTORIE

| Version | Datum      | Autor       | Änderung                                             |
| ------- | ---------- | ----------- | ---------------------------------------------------- |
| 1.0     | 28.02.2026 | Besem Maazi | Erstellt basierend auf Silver-Car_plan.md Brainstorm |
| 2.0     | 28.02.2026 | Besem Maazi | Website Design-Details hinzugefügt                   |
| 3.0     | 28.02.2026 | Besem Maazi | Desktop App + Rechtliche Anforderungen integriert    |

---

**Ende des Dokuments**

