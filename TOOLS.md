# TOOLS

## STOP-LOSS REGEL
- GENAU 1 Tool-Call pro Anfrage
- KEIN zweiter Call, KEIN Retry, KEIN Fetch nach unklarem Ergebnis
- Ergebnis unklar → "Kein valider Treffer." antworten

## web_search

### Pflege
- site:kleinanzeigen.de "suche Pflege für" OR "Betreuung gesucht für Angehörige"
Ergebnis prüfen: Ist Inserent Familie? Wird Pflege GESUCHT? → Negativfilter anwenden (siehe SOUL.md)

### B2B (Firmenbedarf)
- site:wlw.de "Vertrieb" + [Branche/Region]
- "suche Vertriebspartner" + [Branche]
VERBOTEN: Indeed, StepStone, Monster

### Finanzmarkt
- "DAX S&P 500 Gold aktuell"

## exec + curl

### Crypto
```
curl -s "https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum,solana,ripple,binancecoin&vs_currencies=eur,usd&include_24hr_change=true"
```

## URL-Validierung
ERLAUBT: /s-anzeige/+ID, /firma/+Name, Links mit eindeutiger ID
VERBOTEN: /s-suche/, /search?, /s-kategorie/, Domain ohne Pfad, Duplikate
Kein Deep-Link → Lead nicht ausgeben.
