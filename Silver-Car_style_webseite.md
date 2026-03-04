# Design-Anweisung: Limusinen Service Silver-Car

## Website Design Dokument (Version 1.0)

**Erstellt:** 28. Februar 2026  
**Projekt:** Limusinen Service Silver-Car Website  
**Basis:** Adaptierte Premium-Automotive Design-Prinzipien  

---

## 1. Rechtliche Hinweise & Lizenzinformationen

| Bereich            | Richtlinie                                 | Umsetzung                                         |
| ------------------ | ------------------------------------------ | ------------------------------------------------- |
| **Markenrecht**    | Keine geschützten Logos/Names verwenden    | Eigenes Logo für Silver-Car entwickeln            |
| **Design-Patente** | Spezifische UI-Elemente nicht 1:1 kopieren | Prinzipien adaptieren, nicht kopieren             |
| **Bilder**         | Lizenzfreie oder selbst erstellte Fotos    | Stock-Lizenzen prüfen (Shutterstock, Adobe Stock) |
| **Schriftarten**   | Lizenzierte Fonts verwenden                | Google Fonts (lizenzfrei) oder gekaufte Fonts     |
| **Impressum**      | Pflichtangaben gemäß § 5 TMG               | Vollständige Anbieterkennzeichnung                |
| **Datenschutz**    | DSGVO-konform                              | Cookie-Banner, Datenschutzerklärung               |
| **Accessibility**  | WCAG 2.1 Level AA anstreben                | Kontraste, Screenreader-Tauglichkeit              |

**Wichtig:** Diese Website ist ein **eigenständiges Design**, das von Premium-Automotive-Design-Prinzipien inspiriert ist, aber keine geschützten Elemente von Mercedes-Benz oder anderen Marken verwendet.

---

## 2. Layout-Struktur & Grid-System

### 2.1 Basis-Raster

```
Grid-System: 8px-Basis
Container: Max. 1440px, zentriert
Seitenabstand: 24px (Mobile), 48px (Tablet), 80px (Desktop)
Section-Padding: 80px vertikal zwischen Bereichen
```

### 2.2 Seitenstruktur

```
┌─────────────────────────────────────────────────────────┐
│                    HEADER                               │
│  [Logo Silver-Car]  [Navigation]  [CTA: Buchen]         │
├─────────────────────────────────────────────────────────┤
│                    HERO-STAGE                           │
│  [Premium Fahrzeugbild/Video] + [Headline + CTA]        │
├─────────────────────────────────────────────────────────┤
│              SERVICE-ÜBERSICHT (Kacheln)                │
│  [3-4 Kacheln: Flughafen, Hochzeit, Business, Events]   │
├─────────────────────────────────────────────────────────┤
│                 FAHRZEUGFLOTTE                          │
│  [5-6 Fahrzeug-Cards mit Details]                       │
├─────────────────────────────────────────────────────────┤
│                   VORTEILE                              │
│  [Icon-Cards: Pünktlich, Diskret, Komfort, 24/7]        │
├─────────────────────────────────────────────────────────┤
│                 KUNDENSTIMMEN                           │
│  [2-3 Testimonial-Cards]                                │
├─────────────────────────────────────────────────────────┤
│                    FOOTER                               │
│  [Links, Kontakt, Rechtliches, Social Media]            │
└─────────────────────────────────────────────────────────┘
```

### 2.3 Responsive Breakpoints

| Breakpoint  | Breite         | Anpassungen                      |
| ----------- | -------------- | -------------------------------- |
| **Mobile**  | < 768px        | 1 Spalte, Hamburger-Menu         |
| **Tablet**  | 768px - 1024px | 2 Spalten, reduzierte Navigation |
| **Desktop** | > 1024px       | 3-4 Spalten, volle Navigation    |

---

## 3. Farbpalette (Silver-Car Brand)

### 3.1 Primärfarben

| Farbe             | Hex-Code  | Verwendung                 |
| ----------------- | --------- | -------------------------- |
| **Silver Dark**   | `#1A1A1A` | Headlines, Primary Buttons |
| **Silver Medium** | `#4A4A4A` | Sekundärer Text, Borders   |
| **Silver Light**  | `#F5F5F5` | Hintergrund, Cards         |
| **Pure White**    | `#FFFFFF` | Card-Hintergrund, Kontrast |

### 3.2 Akzentfarbe

| Farbe             | Hex-Code  | Verwendung               |
| ----------------- | --------- | ------------------------ |
| **Silver Accent** | `#C0C0C0` | Hover-States, Highlights |
| **Gold Optional** | `#D4AF37` | Premium-CTAs (sparsam)   |

### 3.3 Kontrast-Anforderungen

- **Text auf Hintergrund:** Mindestens 4.5:1 (WCAG AA)
- **Großer Text:** Mindestens 3:1
- **Alle Kombinationen vor Launch prüfen**

---

## 4. Typografie

### 4.1 Schriftarten-Empfehlung (Lizenzfrei)

| Ebene          | Schrift                       | Größe | Gewicht         | Zeilenhöhe |
| -------------- | ----------------------------- | ----- | --------------- | ---------- |
| **H1 Hero**    | Montserrat / Playfair Display | 48px  | Bold (700)      | 1.2        |
| **H2 Section** | Montserrat                    | 32px  | Semi-Bold (600) | 1.3        |
| **H3 Card**    | Montserrat                    | 22px  | Medium (500)    | 1.4        |
| **Body**       | Open Sans / Lato              | 16px  | Regular (400)   | 1.6        |
| **Small**      | Open Sans / Lato              | 14px  | Regular (400)   | 1.5        |

### 4.2 Typografie-Hierarchie

```
H1 → Einmal pro Seite (Hero)
H2 → Pro Section (Services, Flotte, Vorteile...)
H3 → Pro Card (Fahrzeugnamen, Service-Titel)
Body → Fließtext, Beschreibungen
Small → Zusatzinfos, Footer, Captions
```

---

## 5. Kacheln / Cards Design-Spezifikation

### 5.1 Service-Kachel (Hauptservices)

```
┌─────────────────────────────────────────┐
│                                         │
│           [Service-Bild 16:9]           │
│                                         │
├─────────────────────────────────────────┤
│  [Icon optional]                        │
│  Service-Titel (H3, 22px, Bold)         │
│  Kurzbeschreibung (2-3 Zeilen)          │
│                                         │
│  [Link: "Mehr erfahren" →]              │
└─────────────────────────────────────────┘
```

**Specs:**

- Padding: 24px innen
- Border-Radius: 4px (leicht abgerundet)
- Shadow: `0 2px 8px rgba(0,0,0,0.08)`
- Hover: Shadow erhöhen auf `0 4px 16px rgba(0,0,0,0.12)`
- Layout: 3 Spalten (Desktop), 2 (Tablet), 1 (Mobile)

### 5.2 Fahrzeug-Card (Flotte)

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
│                                         │
│  [Button: "Anfragen" - Secondary]       │
└─────────────────────────────────────────┘
```

**Specs:**

- Padding: 32px innen
- Border: 1px solid `#E0E0E0`
- Border-Radius: 4px
- Bild: Hochwertig, freigestellt oder Lifestyle
- Layout: 3 Spalten (Desktop), 2 (Tablet), 1 (Mobile)

### 5.3 Vorteil-Card (Icons)

```
┌─────────────────────────────────────────┐
│                                         │
│           [Icon 64x64px]                │
│                                         │
│  Vorteil-Titel (H3, 20px, Bold)         │
│  Kurzbeschreibung (1-2 Zeilen)          │
│                                         │
└─────────────────────────────────────────┘
```

**Specs:**

- Padding: 24px innen
- Kein Border/Shadow (minimalistisch)
- Icon-Stil: Line-Icons oder gefüllt (konsistent)
- Layout: 4 Spalten (Desktop), 2 (Tablet), 2 (Mobile)

### 5.4 Testimonial-Card

```
┌─────────────────────────────────────────┐
│  "Zitat des Kunden in 2-3 Zeilen"       │
│                                         │
│  ─────────────────────────────────      │
│  [★ ★ ★ ★ ★]                            │
│  Kundenname, Ort                        │
│  Service-Typ (optional)                 │
└─────────────────────────────────────────┘
```

**Specs:**

- Padding: 32px innen
- Background: `#F5F5F5` (leicht abgesetzt)
- Border-Radius: 8px
- Layout: 2-3 Spalten (Desktop), 1 (Mobile)

---

## 6. Navigation

### 6.1 Header-Navigation

| Element    | Position | Stil                                                           |
| ---------- | -------- | -------------------------------------------------------------- |
| **Logo**   | Links    | Silver-Car Logo, max. 180px Breite                             |
| **Menu**   | Zentrum  | 5-6 Punkte (Home, Services, Flotte, Preise, Über uns, Kontakt) |
| **CTA**    | Rechts   | Button "Jetzt Buchen" (Primary)                                |
| **Sticky** | Ja       | Beim Scrollen erhalten, Höhe reduziert                         |

### 6.2 Mobile Navigation

- **Hamburger-Menu:** Rechts oben
- **Drawer:** Von rechts einfliegend
- **CTA:** Im Drawer integriert

### 6.3 Footer-Navigation

```
┌─────────────────────────────────────────────────────────────┐
│  Services          Flotte           Unternehmen    Kontakt  │
│  • Flughafen       • Limousine      • Über uns    • Telefon │
│  • Hochzeit        • Van            • Karriere    • E-Mail  │
│  • Business        • SUV            • Presse      • Adresse │
│  • Events          • Spezial        • Partner     • Formular│
├─────────────────────────────────────────────────────────────┤
│  © 2026 Silver-Car | Impressum | Datenschutz | AGB         │
│  [Social Icons: Instagram, Facebook, LinkedIn]              │
└─────────────────────────────────────────────────────────────┘
```

---

## 7. Button-Styles

### 7.1 Button-Typen

| Typ           | Background  | Text      | Border                | Verwendung         |
| ------------- | ----------- | --------- | --------------------- | ------------------ |
| **Primary**   | `#1A1A1A`   | `#FFFFFF` | none                  | Haupt-CTAs         |
| **Secondary** | transparent | `#1A1A1A` | `1px solid #1A1A1A`   | Sekundäre Aktionen |
| **Text-Link** | none        | `#1A1A1A` | none, Underline Hover | "Mehr erfahren"    |

### 7.2 Button-Größen

| Größe      | Höhe | Padding         | Verwendung    |
| ---------- | ---- | --------------- | ------------- |
| **Large**  | 56px | 32px horizontal | Hero-CTAs     |
| **Medium** | 48px | 24px horizontal | Card-Buttons  |
| **Small**  | 40px | 16px horizontal | Footer, Forms |

### 7.3 Button-Texte (Beispiele)

- "Jetzt Buchen"
- "Fahrzeug Anfragen"
- "Preis Erhalten"
- "Mehr Erfahren →"
- "Kontakt Aufnehmen"

---

## 8. Bildbehandlung

### 8.1 Bild-Anforderungen

| Typ          | Format       | Größe            | Stil                                  |
| ------------ | ------------ | ---------------- | ------------------------------------- |
| **Hero**     | 16:9         | Min. 1920x1080px | Lifestyle, Fahrzeug im Einsatz        |
| **Service**  | 16:9         | Min. 800x450px   | Konsistente Beleuchtung               |
| **Fahrzeug** | 4:3 oder 1:1 | Min. 800x600px   | Freigestellt oder Studio              |
| **Icons**    | 1:1          | 64x64px          | Einheitlicher Stil (Line oder Filled) |

### 8.2 Bild-Optimierung

- **Format:** WebP mit JPG-Fallback
- **Kompression:** Max. 200KB pro Bild
- **Lazy Loading:** Für alle Bilder unterhalb Hero
- **Alt-Texte:** Beschreibend für Accessibility & SEO

### 8.3 Bild-Stil-Richtlinien

- **Farbtemperatur:** Konsistent (leicht kühl für Premium-Look)
- **Beleuchtung:** Professionell, keine harten Schatten
- **Menschen:** Divers, professionell gekleidet
- **Fahrzeuge:** Sauber, poliert, beste Winkel

---

## 9. UI/UX-Prinzipien für Silver-Car

| Prinzip              | Umsetzung                              | Priorität |
| -------------------- | -------------------------------------- | --------- |
| **Premium-Feeling**  | Viel Weißraum, hochwertige Bilder      | Hoch      |
| **Klarheit**         | Ein Ziel pro Section                   | Hoch      |
| **Vertrauen**        | Testimonials, Zertifikate, Kontaktinfo | Hoch      |
| **Conversion**       | CTA sichtbar auf jeder Section         | Hoch      |
| **Barrierefreiheit** | WCAG 2.1 AA Kontraste, Screenreader    | Mittel    |
| **Performance**      | Ladezeit < 3 Sekunden                  | Hoch      |
| **Mobile-First**     | Mobile Optimierung vor Desktop         | Hoch      |

---

## 10. Implementierungs-Checkliste

### Phase 1: Grundgerüst (Woche 1-2)

- [ ] HTML-Grundstruktur erstellen
- [ ] 8px-Grid-System implementieren (CSS Variables)
- [ ] Responsive Breakpoints definieren
- [ ] Header-Navigation aufbauen
- [ ] Footer-Struktur erstellen

### Phase 2: Komponenten (Woche 2-3)

- [ ] Hero-Section mit Platzhalter-Content
- [ ] Service-Kacheln (3-4 Stück)
- [ ] Fahrzeug-Cards (5-6 Stück)
- [ ] Vorteil-Icon-Cards (4 Stück)
- [ ] Button-Styles (Primary, Secondary, Text)
- [ ] Typografie-Skala implementieren

### Phase 3: Content-Integration (Woche 3-4)

- [ ] Silver-Car Logo einbinden
- [ ] Eigene Fahrzeugbilder vorbereiten
- [ ] Service-Texte vom Freund einholen
- [ ] Kontaktinformationen integrieren
- [ ] Testimonials sammeln und einbauen

### Phase 4: Verfeinerung (Woche 4-5)

- [ ] Hover-Effekte hinzufügen
- [ ] Mobile-Optimierung testen (alle Breakpoints)
- [ ] Ladezeiten optimieren (Bilder, Code)
- [ ] Barrierefreiheit prüfen (Kontraste, ARIA)
- [ ] Browser-Testing (Chrome, Firefox, Safari, Edge)

### Phase 5: Launch-Vorbereitung (Woche 5-6)

- [ ] Impressum erstellen (Rechtsanwalt prüfen)
- [ ] Datenschutzerklärung (DSGVO-konform)
- [ ] Cookie-Banner implementieren
- [ ] SSL-Zertifikat aktivieren
- [ ] Analytics einrichten (Google Analytics / Matomo)
- [ ] Finaler Content-Check
- [ ] Go-Live

---

## 11. Empfohlene Tech-Stack Optionen

| Option                    | Für                           | Vorteile                              | Nachteile                    |
| ------------------------- | ----------------------------- | ------------------------------------- | ---------------------------- |
| **WordPress + Elementor** | Einfache Wartung durch Freund | CMS, viele Plugins, günstig           | Etwas langsamer              |
| **Webflow**               | Design-Flexibilität           | Visuell, Hosting inkl., sauberer Code | Lernkurve, monatliche Kosten |
| **Next.js + Vercel**      | Performance                   | Sehr schnell, modern, skalierbar      | Entwickler-Kenntnisse nötig  |
| **Framer**                | Schnell & Schön               | Design-First, Hosting inkl., einfach  | Begrenzte Skalierbarkeit     |

**Empfehlung für Silver-Car:** **WordPress + Elementor** oder **Webflow** (wenn Freund selbst Content pflegen soll)

---

## 12. Kontakt & Support-Integration

### 12.1 Kontakt-Optionen (sichtbar auf jeder Seite)

| Option       | Platzierung                | Format                           |
| ------------ | -------------------------- | -------------------------------- |
| **Telefon**  | Header rechts              | Klickbar (tel:-Link)             |
| **E-Mail**   | Footer + Kontaktseite      | Klickbar (mailto:-Link)          |
| **Formular** | Kontaktseite + Modal       | Name, E-Mail, Service, Nachricht |
| **WhatsApp** | Floating Button (optional) | Direkte Nachricht                |
| **Standort** | Footer + Kontaktseite      | Google Maps Embed                |

### 12.2 Erreichbarkeit kommunizieren

- **Telefonzeiten:** Mo-Fr 8:00-20:00, Sa 10:00-16:00
- **24/7 Service:** Für Flughafen-Transfers hervorheben
- **Antwortzeit:** "Antwort innerhalb 2 Stunden" (wenn zutreffend)

---

## 13. Wichtige Warnhinweise

| Thema            | Hinweis                                                          |
| ---------------- | ---------------------------------------------------------------- |
| **Markenrecht**  | Keine Mercedes-Logos, Namen oder geschützte Designs verwenden    |
| **Bilder**       | Nur lizenzierte oder selbst erstellte Fotos nutzen               |
| **Schriftarten** | Google Fonts oder gekaufte Lizenzen (keine Raubkopien)           |
| **Impressum**    | Vollständige Anbieterkennzeichnung Pflicht (§ 5 TMG)             |
| **Datenschutz**  | DSGVO-konform (Cookie-Banner, Datenschutzerklärung)              |
| **Preise**       | Wenn angegeben: "inkl. MwSt." oder "ab-Preise" klar kennzeichnen |
| **Testimonials** | Nur echte Kundenbewertungen mit Einwilligung                     |

---

## 14. Erfolgsmessung (Post-Launch)

| Metrik                    | Ziel                      | Tool                      |
| ------------------------- | ------------------------- | ------------------------- |
| **Ladezeit**              | < 3 Sekunden              | Google PageSpeed Insights |
| **Mobile Score**          | > 90                      | Google PageSpeed Insights |
| **Conversion Rate**       | > 3% (Anfragen/Besucher)  | Google Analytics          |
| **Absprungrate**          | < 50%                     | Google Analytics          |
| **Suchmaschinen-Ranking** | Top 3 für lokale Keywords | Google Search Console     |

---

## 15. Dokumenten-Historie

| Version | Datum      | Autor       | Änderung                                            |
| ------- | ---------- | ----------- | --------------------------------------------------- |
| 1.0     | 28.02.2026 | Besem Maazi | Erstellt basierend auf Mercedes-Benz Design-Analyse |

---


