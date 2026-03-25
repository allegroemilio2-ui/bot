# TOOLS

## Grundregel
Niemals nur Vorschläge. Sofort suchen und Ergebnisse liefern.
Alles STRIKT SEQUENZIELL. Ein Call → Warten → Optional zweiter Call → Ergebnis.

## web_search (Perplexity)

### 24h Pflege Lead-Suche
RICHTIGE Suchbegriffe (NUR diese verwenden):
- "suche 24h Pflege für Angehörige"
- "24 Stunden Betreuung gesucht Privathaushalt"
- "Pflegekraft gesucht für Mutter/Vater zu Hause"
- "häusliche 24h Pflege gesucht" + Stadt/PLZ

VERBOTENE Suchbegriffe (NIEMALS verwenden):
- "24h Pflege" allein (findet Agenturen)
- "Pflegekraft" allein (findet Pflegekräfte die Arbeit suchen)
- "Pflegedienst" (findet Anbieter, nicht Suchende)
- "Pflege Stellenangebot" (findet Jobanzeigen)

NEGATIVFILTER - Ergebnis verwerfen wenn:
- Inserent ist Pflegedienst/Agentur/Vermittlung
- Anzeige bietet Pflege AN statt zu SUCHEN
- URL ist nur Domain ohne Pfad (z.B. "kleinanzeigen.de")
- Kein Ort/PLZ vorhanden
- Älter als 14 Tage

PFLICHTFELDER pro Lead:
| Feld | Beispiel |
|------|----------|
| Titel | "Suche 24h Pflegekraft für meine Mutter" |
| Plattform | Kleinanzeigen |
| URL | https://www.kleinanzeigen.de/s-anzeige/suche-24h-pflege/12345 |
| Ort + PLZ | München, 80331 |
| Datum | 20.03.2026 |
| Kontakt | Telefon/Email wenn sichtbar |

### B2B Lead-Suche
RICHTIGE Suchbegriffe:
- "Vertrieb auslagern Mittelstand"
- "Kaltakquise Dienstleister gesucht"
- "Terminierung outsourcen"
- "suche Vertriebspartner B2B"
- Firmenname + "sucht Vertriebsunterstützung"

NEGATIVFILTER - Ergebnis verwerfen wenn:
- Es eine Jobanzeige FÜR BEWERBER ist
- Es eine Vertriebsagentur ist die sich selbst bewirbt
- Es ein Freelancer-Profil ist
- Keine Firmenwebsite erkennbar

PFLICHTFELDER pro Lead:
| Feld | Beispiel |
|------|----------|
| Firma | Müller GmbH |
| Branche | IT-Dienstleistung |
| Standort | Stuttgart |
| Signal | Stellenanzeige für Vertriebler, Wachstumssignal |
| Website | https://mueller-gmbh.de |
| Quelle + URL | wlw.de/firma/mueller-gmbh |

### Finanzmarkt & News
- 1 Suche: "DAX S&P 500 Gold aktuell heute"
- Nur Zahlen, keine Analyse
- Max 8 Zeilen Antwort

## exec + curl (API Calls)

### Crypto (CoinGecko)
GENAU 1 Call:
```
curl -s "https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum,solana,ripple,binancecoin&vs_currencies=eur,usd&include_24hr_change=true&include_7d_change=true"
```
Antwort-Format (max 8 Zeilen):
```
Coin | EUR | 24h%
BTC  | 62.450 | -1.3%
ETH  | 1.820 | +2.1%
SOL  | 145 | +0.8%
XRP  | 0.52 | -0.4%
BNB  | 580 | +1.2%
```
KEIN zweiter Call. KEINE Analyse. KEINE Prognose.

### Fear & Greed (optional, nur wenn explizit gefragt)
```
curl -s "https://api.alternative.me/fng/?limit=1"
```

## web_fetch

### Erlaubte Quellen für Pflege-Leads
- kleinanzeigen.de (Suche → Dienstleistungen → Pflege)
- pflegeboerse.de
- betreut.de
- Facebook Gruppen (öffentlich)

### Erlaubte Quellen für B2B-Leads
- wlw.de (Firmenverzeichnis)
- unternehmensregister.de
- LinkedIn (nur öffentliche Firmenprofile)
- Google Maps / Branchenverzeichnisse

### VERBOTENE Quellen
- Indeed, StepStone, Monster (= Jobbörsen, keine Lead-Quellen)
- Pflegeagentur-Websites (= Anbieter, nicht Suchende)
- Personalvermittlungen

## Ablauf pro Anfrage
1. Anfrage lesen → Kategorie erkennen (Pflege / B2B / Crypto / Markt)
2. EINEN web_search oder curl ausführen
3. Ergebnisse gegen NEGATIVFILTER prüfen
4. Nur valide Ergebnisse mit allen PFLICHTFELDERN ausgeben
5. Optional: EINEN zweiten Call wenn erste Ergebnisse unzureichend
6. Ergebnis als kurze Tabelle formatieren
7. FERTIG - kein dritter Call
