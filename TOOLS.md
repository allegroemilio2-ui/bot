# TOOLS

## Grundregel
Niemals nur Vorschläge. Sofort suchen und Ergebnisse liefern.
Alles STRIKT SEQUENZIELL. Ein Call → Warten → Optional zweiter Call → Ergebnis.

## web_search (Perplexity)

### 24h Pflege Lead-Suche
RICHTIGE Suchbegriffe (NUR diese verwenden):
- "suche 24h Pflege für Angehörige" + [Stadt/PLZ]
- "24 Stunden Betreuung gesucht Privathaushalt"
- "Pflegekraft gesucht für Mutter/Vater zu Hause"
- site:kleinanzeigen.de "Pflege gesucht privat"

VERBOTENE Suchbegriffe (NIEMALS verwenden):
- "24h Pflege" allein
- "Pflegekraft" allein
- "Pflegedienst"
- "Pflege Stellenangebot"

NEGATIVFILTER — Ergebnis verwerfen wenn:
- Inserent ist Pflegedienst/Agentur/Vermittlung
- Anzeige bietet Pflege AN statt zu SUCHEN
- URL ist nur Domain ohne Pfad
- Kein Ort/PLZ
- Älter als 14 Tage

### B2B Lead-Suche
RICHTIGE Suchbegriffe:
- "Vertrieb auslagern Mittelstand"
- "Kaltakquise Dienstleister gesucht"
- "Terminierung outsourcen"
- "suche Vertriebspartner B2B"

NEGATIVFILTER — Ergebnis verwerfen wenn:
- Jobanzeige FÜR BEWERBER (Indeed/StepStone/Monster)
- Vertriebsagentur bewirbt SICH SELBST
- Freelancer-Profil
- Keine Firmenwebsite erkennbar

### Finanzmarkt
- 1 Suche: "DAX S&P 500 Gold aktuell heute"
- Nur Zahlen, keine Analyse, max 8 Zeilen

## exec + curl (API Calls)

### Crypto (GENAU 1 Call)
```
curl -s "https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum,solana,ripple,binancecoin&vs_currencies=eur,usd&include_24hr_change=true&include_7d_change=true"
```
KEIN zweiter Call. KEINE Analyse. Nur Tabelle.

### Fear & Greed (nur wenn explizit gefragt)
```
curl -s "https://api.alternative.me/fng/?limit=1"
```

## Erlaubte Quellen
Pflege: kleinanzeigen.de, pflegeboerse.de, betreut.de
B2B: wlw.de, unternehmensregister.de, LinkedIn (öffentlich)

## VERBOTENE Quellen
- Indeed, StepStone, Monster (= Jobbörsen für Bewerber)
- Pflegeagentur-Websites (= Anbieter, nicht Suchende)

## Ablauf pro Anfrage
1. Kategorie erkennen (Pflege / B2B / Crypto / Markt)
2. EINEN Call ausführen
3. Ergebnisse gegen NEGATIVFILTER prüfen
4. Nur valide Ergebnisse mit allen Pflichtfeldern ausgeben
5. Optional: EINEN zweiten Call
6. FERTIG — kein dritter Call
