# PLAYBOOK

## Workflow 1: 24h Pflege Leads

### Zielgruppe
Familien/Privatpersonen die 24h-Pflege für Angehörige SUCHEN.
NICHT: Pflegekräfte, Agenturen, Vermittler.

### Suchstrategie
Schritt 1: web_search mit:
- "suche 24h Pflege für Angehörige" + [Stadt/Region]
- "24 Stunden Betreuung gesucht Privathaushalt"
- "Pflegekraft gesucht häusliche Pflege privat"
- Site-Filter: kleinanzeigen.de ODER pflegeboerse.de

Schritt 2: Jedes Ergebnis prüfen:
- [ ] Inserent = Privatperson/Familie? (nicht Agentur)
- [ ] Pflege wird GESUCHT? (nicht angeboten)
- [ ] Echte URL mit Pfad? (nicht nur Domain)
- [ ] Ort + PLZ vorhanden?
- [ ] Datum < 14 Tage?
→ Alle 5 Checks = JA → Lead ausgeben
→ Ein Check = NEIN → Lead verwerfen

### Ausschlusskriterien
Sofort verwerfen bei Keywords im Inserenten/Titel:
- "Pflegedienst", "Agentur", "Vermittlung", "GmbH" (als Inserent)
- "biete Pflege", "Pflegekraft verfügbar", "suche Arbeit"
- "polnische Pflegekraft", "osteuropäische Betreuung" (= Agentur-Angebote)

### Output pro Lead
```
1. [Titel der Anzeige]
   Plattform: Kleinanzeigen
   URL: https://www.kleinanzeigen.de/s-anzeige/...
   Ort: München, 80331
   Datum: 20.03.2026
   Kontakt: [wenn sichtbar]
```

## Workflow 2: B2B Leads (Vertrieb/Terminierung)

### Zielgruppe
Mittelstandsfirmen (10-250 MA) die Vertrieb/Terminierung BRAUCHEN.
NICHT: Jobanzeigen, Freelancer, Vertriebsagenturen.

### Suchstrategie
Schritt 1: web_search mit:
- "suche Vertriebspartner B2B" + [Branche]
- "Kaltakquise outsourcen Mittelstand"
- "Terminierung auslagern Dienstleister gesucht"
- "Vertriebsunterstützung gesucht"

ALTERNATIVE Signale (indirekt):
- Firma stellt Vertriebler ein → hat Bedarf → potentieller Outsourcing-Kunde
- Suche: "[Firmenname] sucht Sales Manager" auf LinkedIn/Stellenportale

Schritt 2: Jedes Ergebnis prüfen:
- [ ] Echte Firma mit Website?
- [ ] Erkennbarer Vertriebsbedarf?
- [ ] Mittelstand (10-250 MA)?
- [ ] NICHT: Jobanzeige für Bewerber
- [ ] NICHT: Agentur die sich selbst bewirbt

### Ausschlusskriterien
Sofort verwerfen wenn:
- Quelle ist Indeed/StepStone/Monster (= Jobbörse für Bewerber)
- Ergebnis ist ein Freelancer-Profil
- Ergebnis ist eine Vertriebsagentur die ihre Dienste anbietet
- Keine Firmenwebsite erkennbar

### Output pro Lead
```
1. [Firmenname]
   Branche: IT-Dienstleistung
   Standort: Stuttgart
   Website: https://firma.de
   Signal: Stellenanzeige für Sales Manager (LinkedIn, 15.03.2026)
   Mitarbeiter: ca. 50
   Quelle: https://wlw.de/firma/...
```

## Workflow 3: Crypto Markt

### Ablauf
1. GENAU 1 curl-Call an CoinGecko API
2. Daten parsen
3. Tabelle ausgeben
4. FERTIG

### Output-Format
```
Crypto Update [Datum]:
Coin | EUR     | 24h%   | 7d%
BTC  | 62.450  | -1.3%  | +4.2%
ETH  | 1.820   | +2.1%  | -0.8%
SOL  | 145     | +0.8%  | +12.3%
XRP  | 0.52    | -0.4%  | +1.5%
BNB  | 580     | +1.2%  | +3.1%
```
KEINE Analyse. KEINE Prognosen. KEINE Erklärungen. Max 8 Zeilen.

## Workflow 4: Finanzmarkt

### Ablauf
1. 1 web_search: "DAX S&P 500 Gold Kurs heute"
2. Ergebnisse extrahieren
3. Tabelle ausgeben
4. FERTIG

### Output-Format
```
Markt Update [Datum]:
Asset  | Kurs    | Veränderung
DAX    | 18.450  | +0.3%
S&P500 | 5.280   | -0.1%
Gold   | 2.180   | +0.5%
BTC    | 62.450  | -1.3%
```
Alarm nur bei > 2% Bewegung. Max 8 Zeilen.

## Allgemeine Regeln
- Max 5 Leads pro Anfrage
- Max 2 API-Calls pro Anfrage
- Alles sequenziell
- 10s Pause zwischen Calls
- Tabellen statt Fließtext
- Max 15 Zeilen pro Antwort
- Qualität vor Quantität
