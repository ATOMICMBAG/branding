# 📐 Design-Anweisung: Limusinen Service Silver-Car

## Website + Desktop App Design Dokument (Version 2.0)

**Erstellt:** 28. Februar 2026  
**Projekt:** Limusinen Service Silver-Car Website + Admin Desktop App  
**Basis:** Adaptierte Premium-Automotive Design-Prinzipien  
**Erweiterung:** Desktop App für Kundenverwaltung & Mitarbeiterplanung

---

## 1. Rechtliche Hinweise & Lizenzinformationen (Erweitert)

| Bereich              | Richtlinie                                 | Umsetzung                                         |
| -------------------- | ------------------------------------------ | ------------------------------------------------- |
| **Markenrecht**      | Keine geschützten Logos/Names verwenden    | Eigenes Logo für Silver-Car entwickeln            |
| **Design-Patente**   | Spezifische UI-Elemente nicht 1:1 kopieren | Prinzipien adaptieren, nicht kopieren             |
| **Bilder**           | Lizenzfreie oder selbst erstellte Fotos    | Stock-Lizenzen prüfen (Shutterstock, Adobe Stock) |
| **Schriftarten**     | Lizenzierte Fonts verwenden                | Google Fonts (lizenzfrei) oder gekaufte Fonts     |
| **Impressum**        | Pflichtangaben gemäß § 5 TMG               | Vollständige Anbieterkennzeichnung                |
| **Datenschutz**      | DSGVO-konform                              | Cookie-Banner, Datenschutzerklärung               |
| **Accessibility**    | WCAG 2.1 Level AA anstreben                | Kontraste, Screenreader-Tauglichkeit              |
| **Kundendaten**      | DSGVO Art. 6, 17, 20                       | Datenminimierung, Löschkonzept, Exportfunktion    |
| **E-Mail-Marketing** | DSGVO + UWG § 7                            | Double-Opt-In, Abmeldelink in jeder Mail          |
| **Vertragsdaten**    | GoBD-konforme Aufbewahrung                 | 10 Jahre Aufbewahrungsfrist für Buchungen         |

**⚠️ Wichtig:** Die Desktop App verarbeitet personenbezogene Daten. Ein **Datenschutzbeauftragter** sollte vor Entwicklung konsultiert werden.

---

## 2. Gesamtsystem-Architektur

### 2.1 System-Übersicht

```
┌─────────────────────────────────────────────────────────────────────┐
│                         SILVER-CAR SYSTEM                           │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  ┌─────────────────────┐         ┌─────────────────────────────┐   │
│  │   PUBLIC WEBSITE    │         │      DESKTOP APP (Admin)    │   │
│  │   (Kunden-Frontend) │         │      (Mitarbeiter-Backend)  │   │
│  │                     │         │                             │   │
│  │  • Homepage         │         │  • Kundenverwaltung         │   │
│  │  • Services         │◄───────►│  • Terminplanung            │   │
│  │  • Fahrzeugflotte   │  API    │  • Mitarbeiter-Einteilung   │   │
│  │  • Buchungsformular │  REST   │  • Vertragsbestätigung      │   │
│  │  • Kontakt          │         │  • E-Mail-Marketing         │   │
│  └─────────────────────┘         │  • Reports & Analytics      │   │
│                                  └─────────────────────────────┘   │
│                                           │                         │
│                                           ▼                         │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                    ZENTRALE DATENBANK                       │   │
│  │  • Kunden (DSGVO-verschlüsselt)                             │   │
│  │  • Buchungen / Termine                                      │   │
│  │  • Mitarbeiter / Fahrer                                     │   │
│  │  • Fahrzeuge / Wartung                                      │   │
│  │  • Verträge / Rechnungen                                    │   │
│  │  • E-Mail-Verteiler                                         │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                           │                         │
│                                           ▼                         │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                    EXTERNE SERVICES                         │   │
│  │  • E-Mail-Server (SMTP / SendGrid / Mailgun)                │   │
│  │  • SMS-Gateway (optional für Benachrichtigungen)            │   │
│  │  • Payment-Provider (Stripe / PayPal)                       │   │
│  │  • Cloud-Backup (täglich)                                   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### 2.2 Technische Anforderungen

| Komponente            | Anforderung                             | Begründung                       |
| --------------------- | --------------------------------------- | -------------------------------- |
| **Datenbank**         | PostgreSQL oder MySQL                   | DSGVO-konform, verschlüsselbar   |
| **API**               | REST oder GraphQL                       | Website ↔ App Kommunikation      |
| **Desktop App**       | Electron oder .NET WPF                  | Cross-Platform oder Windows-only |
| **Authentifizierung** | JWT + 2FA                               | Sicherer Zugang für Mitarbeiter  |
| **Verschlüsselung**   | AES-256 für Daten, TLS 1.3 für Transfer | Datenschutz                      |
| **Backup**            | Täglich, 30 Tage Retention              | Datensicherheit                  |

---

## 3. Desktop App – Modulübersicht

### 3.1 Hauptmodule der Desktop App

```
┌─────────────────────────────────────────────────────────────────┐
│                    SILVER-CAR ADMIN APP                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │
│  │   KUNDEN     │  │   TERMINE    │  │  MITARBEITER │          │
│  │   VERWALTUNG │  │   PLANUNG    │  │  EINTEILUNG  │          │
│  └──────────────┘  └──────────────┘  └──────────────┘          │
│                                                                 │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │
│  │   VERTRÄGE   │  │   E-MAIL     │  │   REPORTS    │          │
│  │   BESTÄTIGUNG│  │   MARKETING  │  │   & EXPORT   │          │
│  └──────────────┘  └──────────────┘  └──────────────┘          │
│                                                                 │
│  ┌──────────────┐  ┌──────────────┐                            │
│  │   FAHRZEUGE  │  │   EINSTELLUNGEN│                          │
│  │   & WARTUNG  │  │   & USER     │                            │
│  └──────────────┘  └──────────────┘                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 4. Modul: Kundenverwaltung

### 4.1 Kunden-Datenstruktur

| Feld                | Typ            | Pflicht | DSGVO-Hinweis                  |
| ------------------- | -------------- | ------- | ------------------------------ |
| Kunden-ID           | Auto-Increment | Ja      | Intern                         |
| Vorname             | Text           | Ja      | Personenbezogen                |
| Nachname            | Text           | Ja      | Personenbezogen                |
| E-Mail              | E-Mail         | Ja      | Personenbezogen, Login         |
| Telefon             | Text           | Ja      | Personenbezogen                |
| Adresse             | Text           | Nein    | Personenbezogen, optional      |
| Geburtsdatum        | Datum          | Nein    | Sensibel, nur mit Einwilligung |
| Registrierungsdatum | Datum          | Ja      | Intern                         |
| Newsletter-Opt-In   | Boolean        | Nein    | Dokumentiert speichern         |
| Letzter Login       | Datum          | Ja      | Intern                         |
| Kundenstatus        | Enum           | Ja      | Aktiv, Inaktiv, Gesperrt       |
| Löschvermerk        | Datum          | Nein    | Für DSGVO-Löschfrist           |

### 4.2 Kundenverwaltung – UI-Layout

```
┌─────────────────────────────────────────────────────────────────┐
│  KUNDENVERWALTUNG                              [+ Neuer Kunde]  │
├─────────────────────────────────────────────────────────────────┤
│  [Suche: Name, E-Mail, Telefon...]  [Filter: Status, Datum]    │
├─────────────────────────────────────────────────────────────────┤
│  ┌───────────────────────────────────────────────────────────┐  │
│  │ Name          │ E-Mail           │ Telefon    │ Status    │  │
│  ├───────────────────────────────────────────────────────────┤  │
│  │ Max Mustermann│ max@email.de     │ +49 123... │ ● Aktiv   │  │
│  │ Erika Beispiel│ erika@email.de   │ +49 456... │ ● Aktiv   │  │
│  │ John Doe      │ john@email.de    │ +49 789... │ ○ Inaktiv │  │
│  │ ...           │ ...              │ ...        │ ...       │  │
│  └───────────────────────────────────────────────────────────┘  │
│                                                                 │
│  [Ausgewählt: 1 Kunde]  [Bearbeiten]  [Löschen]  [Export]      │
└─────────────────────────────────────────────────────────────────┘
```

### 4.3 Kunden-Detailansicht

```
┌─────────────────────────────────────────────────────────────────┐
│  KUNDE: Max Mustermann (ID: 12345)             [Bearbeiten] ✕   │
├─────────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────┐  ┌─────────────────────────────┐  │
│  │  PERSÖNLICHE DATEN      │  │  BUCHUNGSHISTORIE           │  │
│  │                         │  │                             │  │
│  │  E-Mail: max@email.de   │  │  Datum      │ Service       │  │
│  │  Telefon: +49 123...    │  │  15.01.26   │ Flughafen     │  │
│  │  Adresse: Musterstr. 1  │  │  20.12.25   │ Hochzeit      │  │
│  │                         │  │  10.11.25   │ Business      │  │
│  │  Newsletter: ✓ Opt-In   │  │                             │  │
│  │  Registriert: 01.06.24  │  │  Gesamt: 12 Buchungen       │  │
│  └─────────────────────────┘  └─────────────────────────────┘  │
│                                                                 │
│  [Alle Buchungen anzeigen]  [E-Mail senden]  [Kunde löschen]   │
└─────────────────────────────────────────────────────────────────┘
```

### 4.4 DSGVO-Funktionen (Pflicht!)

| Funktion        | Beschreibung                                | Umsetzung                    |
| --------------- | ------------------------------------------- | ---------------------------- |
| **Datenexport** | Kunde kann alle Daten exportieren (Art. 20) | CSV/PDF-Export pro Kunde     |
| **Löschung**    | Kunde kann Löschung beantragen (Art. 17)    | Soft-Delete + Frist-Tracking |
| **Opt-In-Log**  | Newsletter-Anmeldung dokumentieren          | Timestamp + IP speichern     |
| **Datenschutz** | Minimale Datenspeicherung                   | Nur notwendige Felder        |
| **Zugriffslog** | Wer hat auf Daten zugegriffen?              | Audit-Trail für Mitarbeiter  |

---

## 5. Modul: Terminplanung & Mitarbeiter-Einteilung

### 5.1 Termin-Datenstruktur

| Feld           | Typ               | Pflicht | Hinweis                                    |
| -------------- | ----------------- | ------- | ------------------------------------------ |
| Buchungs-ID    | Auto-Increment    | Ja      | Intern                                     |
| Kunden-ID      | Foreign Key       | Ja      | Verknüpfung Kunde                          |
| Service-Typ    | Enum              | Ja      | Flughafen, Hochzeit, Business, Event       |
| Fahrzeug-ID    | Foreign Key       | Ja      | Zugewiesenes Fahrzeug                      |
| Datum          | Datum             | Ja      | Fahrttermin                                |
| Uhrzeit        | Zeit              | Ja      | Abfahrtszeit                               |
| Dauer          | Integer (Minuten) | Ja      | Geschätzte Dauer                           |
| Abholort       | Text              | Ja      | Adresse                                    |
| Zielort        | Text              | Ja      | Adresse                                    |
| Fahrer-ID      | Foreign Key       | Ja      | Zugewiesener Mitarbeiter                   |
| Status         | Enum              | Ja      | Offen, Bestätigt, Abgeschlossen, Storniert |
| Preis          | Decimal           | Ja      | Endpreis inkl. MwSt.                       |
| Zahlungsstatus | Enum              | Ja      | Offen, Bezahlt, Teilweise                  |
| Vertragsdatum  | Datum             | Ja      | Bei Bestätigung                            |
| Notizen        | Text              | Nein    | Interne Notizen                            |

### 5.2 Kalender-Ansicht – UI-Layout

```
┌─────────────────────────────────────────────────────────────────┐
│  TERMINPLANUNG                    [Tag] [Woche] [Monat] [+ Neu] │
├─────────────────────────────────────────────────────────────────┤
│  Filter: [Alle Fahrzeuge ▼] [Alle Fahrer ▼] [Status: Alle ▼]   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│     08:00  │  [F1] Flughafen - Herr Müller                     │
│     09:00  │  ─────────────────────────────────────────────    │
│     10:00  │  [F3] Hochzeit - Familie Schmidt                  │
│     11:00  │  ─────────────────────────────────────────────    │
│     12:00  │                                                   │
│     13:00  │  [F2] Business - Frau Weber                       │
│     14:00  │  ─────────────────────────────────────────────    │
│     15:00  │                                                   │
│     16:00  │  [F1] Event - Firma XYZ                           │
│     17:00  │                                                   │
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│  LEGENDE: [F1] = Fahrzeug 1  |  🟢 Bestätigt  |  🟡 Offen       │
└─────────────────────────────────────────────────────────────────┘
```

### 5.3 Mitarbeiter-Einteilung – UI-Layout

```
┌─────────────────────────────────────────────────────────────────┐
│  MITARBEITER-EINTEILUNG                        [Mitarbeiter +]  │
├─────────────────────────────────────────────────────────────────┤
│  Termin: 15.03.2026, 14:00 - Hochzeit Schmidt                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  VERFÜGBARE FAHRER (15.03.2026):                                │
│  ┌───────────────────────────────────────────────────────────┐  │
│  │ ✓ Fahrer     │ Schicht     │ Status    │ Auslastung      │  │
│  ├───────────────────────────────────────────────────────────┤  │
│  │ ☐ Michael K. │ 08:00-16:00 │ Verfügbar │ 2/4 Fahrten     │  │
│  │ ☐ Stefan B.  │ 08:00-16:00 │ Verfügbar │ 3/4 Fahrten     │  │
│  │ ☐ Thomas W.  │ 14:00-22:00 │ Verfügbar │ 1/4 Fahrten     │  │
│  │ ☐ Andreas L. │ 08:00-16:00 │ Urlaub    │ 0/4 Fahrten     │  │
│  └───────────────────────────────────────────────────────────┘  │
│                                                                 │
│  ZUGEWIESENER FAHRER: [Michael K. ▼]                            │
│  FAHRZEUG:              [Limousine 1 ▼]                         │
│                                                                 │
│  [Speichern]  [Absage senden]                                   │
└─────────────────────────────────────────────────────────────────┘
```

### 5.4 Konflikterkennung

| Konflikt-Typ               | Erkennung                       | Lösung                  |
| -------------------------- | ------------------------------- | ----------------------- |
| **Fahrzeug-Doppelbuchung** | Fahrzeug bereits vergeben       | Alternative vorschlagen |
| **Fahrer-Überlastung**     | Max. 4 Fahrten/Tag erreicht     | Anderen Fahrer zuweisen |
| **Fahrer-Urlaub/Krank**    | Kalender-Markierung             | Automatisch ausblenden  |
| **Zeit-Überschneidung**    | Fahrt dauert länger als geplant | Pufferzeit einplanen    |

---

## 6. Modul: Vertragsbestätigung & Kundenkommunikation

### 6.1 Automatischer Bestätigungs-Workflow

```
┌─────────────────────────────────────────────────────────────────┐
│                    BESTÄTIGUNGS-WORKFLOW                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. KUNDE BUCHT ONLINE                                          │
│     ↓                                                           │
│  2. BUCHUNG ERSCHEINT IN APP (Status: "Offen")                  │
│     ↓                                                           │
│  3. MITARBEITER PRÜFT & WEIST ZU                                │
│     • Fahrzeug zuweisen                                         │
│     • Fahrer zuweisen                                           │
│     • Preis bestätigen                                          │
│     ↓                                                           │
│  4. VERTRAGSBESTÄTIGUNG WIRD GENERIERT                          │
│     • PDF mit allen Details                                     │
│     • AGB + Stornobedingungen                                   │
│     ↓                                                           │
│  5. BESTÄTIGUNG AN KUNDEN VERSANDT                              │
│     • E-Mail mit PDF-Anhang                                     │
│     • SMS optional (kurze Bestätigung)                          │
│     ↓                                                           │
│  6. STATUS AUF "BESTÄTIGT" SETZEN                               │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 6.2 Bestätigungs-E-Mail Template

```
┌─────────────────────────────────────────────────────────────────┐
│  Silver-Car - Limousinen Service                                │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  Sehr geehrter Herr Mustermann,                                 │
│                                                                 │
│  wir bestätigen Ihre Buchung mit folgenden Details:             │
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│  BUCHUNGS-NR:      SC-2026-00123                                │
│  DATUM:            15.03.2026                                   │
│  UHRZEIT:          14:00 Uhr                                    │
│  SERVICE:          Hochzeit                                     │
│  FAHRZEUG:         Mercedes S-Klasse Limousine                  │
│  FAHRER:           Herr Michael K.                              │
│  ABHOLORT:         Musterstraße 1, 80331 München                │
│  ZIELORT:          Schloss Nymphenburg, München                 │
│  PREIS:            450,00 EUR (inkl. MwSt.)                     │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  Im Anhang finden Sie Ihren Vertragsbestätigung.                │
│                                                                 │
│  Bei Fragen erreichen Sie uns unter:                            │
│  📞 +49 89 123 456 78                                           │
│  ✉️ service@silver-car.de                                       │
│                                                                 │
│  Wir freuen uns auf Sie!                                        │
│  Ihr Silver-Car Team                                            │
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│  Silver-Car GmbH | Musterstraße 1 | 80331 München               │
│  [Abmelden] [Datenschutz] [Impressum]                           │
└─────────────────────────────────────────────────────────────────┘
```

### 6.3 PDF-Vertragsinhalt (Pflichtfelder)

| Abschnitt             | Inhalt                                      |
| --------------------- | ------------------------------------------- |
| **Kopfzeile**         | Silver-Car Logo, Adresse, Kontakt           |
| **Kundendaten**       | Name, Adresse, Kontakt                      |
| **Buchungsdetails**   | Datum, Uhrzeit, Service, Fahrzeug           |
| **Preisaufstellung**  | Basispreis, Zusatzleistungen, MwSt., Gesamt |
| **AGB**               | Vollständig oder Link                       |
| **Stornobedingungen** | Fristen, Kosten                             |
| **Unterschrift**      | Platzhalter für digitale Signatur           |
| **Datum & Stempel**   | Automatisch generiert                       |

---

## 7. Modul: E-Mail-Marketing

### 7.1 Rechtliche Anforderungen (UWG § 7 + DSGVO)

| Anforderung          | Umsetzung                               |
| -------------------- | --------------------------------------- |
| **Double-Opt-In**    | Bestätigungs-E-Mail nach Anmeldung      |
| **Abmeldelink**      | In jeder Marketing-E-Mail Pflicht       |
| **Verteiler-Log**    | Wer hat welche Mails erhalten?          |
| **Bounce-Handling**  | Ungültige E-Mails automatisch entfernen |
| **Datenminimierung** | Nur E-Mail + Name für Marketing         |

### 7.2 E-Mail-Marketing – UI-Layout

```
┌─────────────────────────────────────────────────────────────────┐
│  E-MAIL MARKETING                               [+ Neue Kampagne]│
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  VERTEILER-LISTEN:                                              │
│  ┌───────────────────────────────────────────────────────────┐  │
│  │ Liste              │ Abonnenten │ Status    │ Letzte Mail │  │
│  ├───────────────────────────────────────────────────────────┤  │
│  │ Alle Kunden        │ 1.234      │ Aktiv     │ 01.02.2026  │  │
│  │ Newsletter         │ 856        │ Aktiv     │ 15.01.2026  │  │
│  │ Hochzeits-Kunden   │ 342        │ Aktiv     │ 20.12.2025  │  │
│  │ Business-Kunden    │ 521        │ Aktiv     │ 10.01.2026  │  │
│  └───────────────────────────────────────────────────────────┘  │
│                                                                 │
│  LETZTE KAMPAGNEN:                                              │
│  ┌───────────────────────────────────────────────────────────┐  │
│  │ Kampagne           │ Gesendet   │ Öffnungsrate │ Klicks   │  │
│  ├───────────────────────────────────────────────────────────┤  │
│  │ Winter-Angebot     │ 1.234      │ 24,5%        │ 8,2%     │  │
│  │ Neujahrs-Gruß      │ 1.198      │ 31,2%        │ 12,1%    │  │
│  └───────────────────────────────────────────────────────────┘  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 7.3 Kampagnen-Erstellung – UI-Layout

```
┌─────────────────────────────────────────────────────────────────┐
│  NEUE E-MAIL KAMPAGNE                          [Speichern] ✕    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. GRUNDDATEN                                                  │
│  ┌───────────────────────────────────────────────────────────┐  │
│  │ Kampagnen-Name:  [Frühlings-Angebot 2026____________]      │  │
│  │ Verteiler:       [Alle Kunden ▼]                           │  │
│  │ Betreff:         [🌸 Frühling = Frische Preise!_______]    │  │
│  │ Absender:        [Silver-Car <service@silver-car.de>___]   │  │
│  └───────────────────────────────────────────────────────────┘  │
│                                                                 │
│  2. INHALT (WYSIWYG Editor)                                     │
│  ┌───────────────────────────────────────────────────────────┐  │
│  │ [B] [I] [U] [Link] [Bild] [Template]                       │  │
│  │ ─────────────────────────────────────────────────────────  │  │
│  │  Sehr geehrte Damen und Herren,                           │  │
│  │                                                           │  │
│  │  Der Frühling kommt – und wir haben besondere Angebote... │  │
│  │                                                           │  │
│  │  [Button: Jetzt Buchen]                                   │  │
│  │                                                           │  │
│  └───────────────────────────────────────────────────────────┘  │
│                                                                 │
│  3. VORSCHAU & TEST                                             │
│  [Vorschau Desktop] [Vorschau Mobile] [Test-E-Mail senden]      │
│                                                                 │
│  4. VERSAND                                                     │
│  [Jetzt senden] [Geplant senden: __.__.____ __:__]              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 7.4 E-Mail-Templates (Vorgefertigt)

| Template                | Anlass                     | Frequenz    |
| ----------------------- | -------------------------- | ----------- |
| **Willkommen**          | Nach Registrierung         | Automatisch |
| **Buchungsbestätigung** | Nach Buchung               | Automatisch |
| **Erinnerung**          | 24h vor Fahrt              | Automatisch |
| **Feedback**            | Nach abgeschlossener Fahrt | Automatisch |
| **Sonderangebot**       | Saisonale Aktionen         | Manuell     |
| **Newsletter**          | Monatlich                  | Manuell     |
| **Geburtstag**          | Kunden-Geburtstag          | Automatisch |

---

## 8. Modul: Reports & Analytics

### 8.1 Verfügbare Reports

| Report                  | Inhalt                                    | Export   |
| ----------------------- | ----------------------------------------- | -------- |
| **Umsatz**              | Täglich, Wöchentlich, Monatlich, Jährlich | PDF, CSV |
| **Buchungen**           | Nach Service-Typ, Fahrzeug, Fahrer        | PDF, CSV |
| **Kunden**              | Neukunden, Bestandskunden, Inaktiv        | PDF, CSV |
| **Fahrzeug-Auslastung** | utilization pro Fahrzeug                  | PDF, CSV |
| **Fahrer-Performance**  | Fahrten pro Fahrer, Bewertungen           | PDF, CSV |
| **E-Mail-Statistik**    | Öffnungsraten, Klicks, Bounces            | PDF, CSV |

### 8.2 Dashboard – UI-Layout

```
┌─────────────────────────────────────────────────────────────────┐
│  DASHBOARD                                      [Zeitraum: ▼]  │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌───────────┐ │
│  │ Buchungen   │ │ Umsatz      │ │ Auslastung  │ │ Kunden    │ │
│  │ diese Woche │ │ diesen Monat│ │ Fahrzeuge   │ │ neu       │ │
│  │             │ │             │ │             │ │           │ │
│  │    47       │ │  12.450€    │ │    78%      │ │    23     │ │
│  │   ↑ 12%     │ │   ↑ 8%      │ │   ↓ 3%      │ │   ↑ 15%   │ │
│  └─────────────┘ └─────────────┘ └─────────────┘ └───────────┘ │
│                                                                 │
│  ┌─────────────────────────────────┐ ┌───────────────────────┐ │
│  │  UMSATZ ENTWICKLUNG (12 Monate) │ │  NÄCHSTE FAHRTEN      │ │
│  │                                 │ │                       │ │
│  │  [████████████████ Line Chart]  │ │  14:00 - Flughafen    │ │
│  │                                 │ │  15:30 - Hochzeit     │ │
│  │  J F M A M J J A S O N D        │ │  17:00 - Business     │ │
│  └─────────────────────────────────┘ └───────────────────────┘ │
│                                                                 │
│  ┌─────────────────────────────────┐ ┌───────────────────────┐ │
│  │  OFFENE BUCHUNGEN               │ │  FAHRER STATUS        │ │
│  │                                 │ │                       │ │
│  │  • 5x Bestätigung ausstehend    │ │  🟢 8 Verfügbar       │ │
│  │  • 3x Zahlung offen             │ │  🟡 2 Im Einsatz      │ │
│  │  • 1x Stornierung Anfrage       │ │  🔴 1 Krank/Urlaub    │ │
│  └─────────────────────────────────┘ └───────────────────────┘ │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 9. Sicherheit & Zugriffskontrolle

### 9.1 Benutzerrollen

| Rolle         | Rechte                                | Beschränkungen            |
| ------------- | ------------------------------------- | ------------------------- |
| **Admin**     | Alle Rechte                           | Keine                     |
| **Manager**   | Kunden, Termine, Mitarbeiter, E-Mails | Keine Systemeinstellungen |
| **Disponent** | Termine, Mitarbeiter-Einteilung       | Keine Finanzdaten         |
| **Fahrer**    | Eigene Fahrten ansehen                | Keine Kundendaten-Exporte |
| **Support**   | Kunden ansehen, E-Mails senden        | Keine Löschungen          |

### 9.2 Sicherheitsmaßnahmen

| Maßnahme                  | Umsetzung                              |
| ------------------------- | -------------------------------------- |
| **Passwort-Richtlinie**   | Min. 12 Zeichen, Sonderzeichen, Zahlen |
| **2-Faktor-Auth**         | SMS oder Authenticator App             |
| **Session-Timeout**       | 30 Minuten Inaktivität                 |
| **Zugriffs-Log**          | Jeder Login wird protokolliert         |
| **Daten-Verschlüsselung** | AES-256 für Datenbank                  |
| **Backup**                | Täglich, verschlüsselt, extern         |
| **IP-Whitelist**          | Optional für Admin-Zugang              |

---

## 🛠️ 10. Tech-Stack Empfehlungen

### 10.1 Website (Kunden-Frontend)

| Komponente  | Empfehlung                    | Alternative        |
| ----------- | ----------------------------- | ------------------ |
| **CMS**     | WordPress + Elementor         | Webflow            |
| **Hosting** | All-Inkl / Strato (DE-Server) | SiteGround         |
| **SSL**     | Let's Encrypt (kostenlos)     | Comodo             |
| **E-Mail**  | SMTP über Host                | SendGrid / Mailgun |

### 10.2 Desktop App (Admin-Backend)

| Komponente    | Empfehlung                | Alternative             |
| ------------- | ------------------------- | ----------------------- |
| **Framework** | Electron (Cross-Platform) | .NET WPF (Windows-only) |
| **Sprache**   | JavaScript/TypeScript     | C#                      |
| **Datenbank** | PostgreSQL                | MySQL                   |
| **API**       | REST (Node.js oder PHP)   | GraphQL                 |
| **Auth**      | JWT + 2FA                 | OAuth2                  |
| **E-Mail**    | SendGrid API              | SMTP                    |
| **PDF**       | PDFKit / Puppeteer        | iText                   |

### 10.3 Infrastruktur

```
┌─────────────────────────────────────────────────────────────────┐
│                    INFRASTRUKTUR-ÜBERSICHT                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  WEBSITE (Public)                                               │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │  Hosting: All-Inkl (Deutschland)                        │   │
│  │  Domain: www.silver-car.de                              │   │
│  │  SSL: Let's Encrypt                                     │   │
│  │  CMS: WordPress                                         │   │
│  └─────────────────────────────────────────────────────────┘   │
│                          │                                      │
│                          │ API (REST)                           │
│                          ▼                                      │
│  DESKTOP APP (Admin - Lokal oder Cloud)                         │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │  Framework: Electron                                    │   │
│  │  Datenbank: PostgreSQL (verschüsselt)                   │   │
│  │  Backup: Täglich zu externem Speicher                   │   │
│  │  Zugriff: Nur autorisierte Mitarbeiter (2FA)            │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 11. Implementierungs-Phasen (Erweitert)

### Phase 1: Website Grundgerüst (Woche 1-4)

- [ ] HTML-Grundstruktur erstellen
- [ ] 8px-Grid-System implementieren
- [ ] Header/Footer-Navigation
- [ ] Hero, Services, Flotte Sections
- [ ] Kontaktformular
- [ ] Impressum & Datenschutz

### Phase 2: Website Buchungs-System (Woche 5-8)

- [ ] Buchungsformular mit Validierung
- [ ] Fahrzeug-Auswahl
- [ ] Termin-Auswahl (Kalender)
- [ ] Kunden-Registrierung/Login
- [ ] Buchungsbestätigung E-Mail (automatisch)

### Phase 3: Desktop App – Kernmodule (Woche 9-16)

- [ ] Datenbank-Setup (PostgreSQL)
- [ ] Authentifizierung (Login + 2FA)
- [ ] Kundenverwaltung (CRUD)
- [ ] Terminplanung (Kalender)
- [ ] Mitarbeiter-Einteilung
- [ ] Vertrags-PDF-Generierung

### Phase 4: Desktop App – Erweiterte Module (Woche 17-20)

- [ ] E-Mail-Marketing-System
- [ ] Verteiler-Listen-Verwaltung
- [ ] E-Mail-Templates
- [ ] Reports & Analytics
- [ ] Dashboard

### Phase 5: Integration & Testing (Woche 21-24)

- [ ] Website ↔ App API-Integration
- [ ] End-to-End Testing
- [ ] Sicherheits-Audit
- [ ] DSGVO-Compliance-Check
- [ ] Schulung für Mitarbeiter
- [ ] Go-Live

---

## 12. Kritische Warnhinweise

| Thema                | Risiko                         | Empfehlung                          |
| -------------------- | ------------------------------ | ----------------------------------- |
| **DSGVO**            | Hohe Strafen bei Verstößen     | Datenschutzbeauftragten einbinden   |
| **Kundendaten**      | Datenleck = Reputationsverlust | Verschlüsselung, Zugriffskontrolle  |
| **E-Mail-Marketing** | Abmahnung bei falschem Opt-In  | Double-Opt-In zwingend              |
| **Vertragsdaten**    | GoBD-Verstöße                  | 10 Jahre Aufbewahrung sicherstellen |
| **Backup**           | Datenverlust bei Ausfall       | Täglich, extern, getestet           |
| **2FA**              | Unbefugter Zugang              | Für alle Mitarbeiter verpflichtend  |

---

## 14. Dokumenten-Historie

| Version | Datum      | Autor       | Änderung                                            |
| ------- | ---------- | ----------- | --------------------------------------------------- |
| 1.0     | 28.02.2026 | Besem Maazi | Erstellt basierend auf Mercedes-Benz Design-Analyse |
| 2.0     | 28.02.2026 | Besem Maazi | Erweiterung: Desktop App Module hinzugefügt         |

---



