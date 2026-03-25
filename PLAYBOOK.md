# PLAYBOOK (Referenz)

## Workflow 1: 24h Pflege Leads

Zielgruppe: Familien die Pflege SUCHEN. NICHT Pflegekräfte/Agenturen.

Schritt 1: web_search mit:
- "suche 24h Pflege für Angehörige" + [Stadt/Region]
- site:kleinanzeigen.de "Pflege gesucht privat"

Schritt 2: Jedes Ergebnis prüfen:
- [ ] Inserent = Privatperson/Familie?
- [ ] Pflege wird GESUCHT?
- [ ] Echte URL mit Pfad?
- [ ] Ort + PLZ vorhanden?
- [ ] Datum < 14 Tage?
→ Alle JA = ausgeben. Ein NEIN = verwerfen.

Sofort verwerfen bei:
- "Pflegedienst", "Agentur", "Vermittlung", "GmbH" als Inserent
- "biete Pflege", "Pflegekraft verfügbar", "suche Arbeit"
- "polnische Pflegekraft vermitteln" (= Agentur-Angebot)

## Workflow 2: B2B Leads

Zielgruppe: Mittelstand (10-250 MA) mit Vertriebsbedarf. NICHT Jobanzeigen.

Schritt 1: web_search mit:
- "suche Vertriebspartner B2B" + [Branche]
- "Kaltakquise outsourcen Mittelstand"
- wlw.de + [Branche] + [Region]

Schritt 2: Prüfen:
- [ ] Echte Firma mit Website?
- [ ] Vertriebsbedarf erkennbar?
- [ ] NICHT Jobanzeige für Bewerber?
- [ ] NICHT Agentur-Eigenwerbung?

Verbotene Quellen: Indeed, StepStone, Monster

## Workflow 3: Crypto

1 curl-Call → CoinGecko API → Tabelle → FERTIG
Keine Analyse, keine Prognosen.

## Workflow 4: Finanzmarkt

1 web_search → Zahlen extrahieren → Tabelle → FERTIG
Alarm nur bei > 2% Bewegung.
