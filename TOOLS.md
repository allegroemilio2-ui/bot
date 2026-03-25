# TOOLS

## CALL-LIMIT (HARTE REGEL)
Max 2 Calls pro Anfrage:
1. web_search (Pflicht)
2. web_fetch (Optional — NUR wenn Schritt 1 keine Deep-Links liefert)

VERBOTEN:
- Mehr als 1 web_search
- Mehr als 1 web_fetch
- Retry / zweite Suche
- Parallele Calls
- Hintergrund-Jobs

## ABLAUF (EXAKT BEFOLGEN)

### Schritt 1: web_search
Suchbegriff ausführen. Ergebnis prüfen:
→ Deep-Links vorhanden (z.B. /s-anzeige/xxx/123)? → Schritt 3
→ Keine Deep-Links? → Schritt 2

### Schritt 2: web_fetch (optional, max 1x)
Beste URL aus Schritt 1 mit web_fetch öffnen.
Aus HTML Einzelanzeigen-URLs extrahieren.
Nur URLs mit /s-anzeige/, /firma/, /inserat/ + ID behalten.

### Schritt 3: Filter anwenden
Pflege: Negativfilter (siehe SOUL.md)
B2B: Firmenbedarf-Filter (siehe SOUL.md)
Nur valide Leads mit Deep-Link + Ort ausgeben.

### Schritt 4: Ergebnis liefern. STOP.
Kein weiterer Call. Keine Erklärung. Keine Wiederholung.

## SUCHBEGRIFFE

### Pflege
- site:kleinanzeigen.de "suche Pflege für" OR "Betreuung gesucht"
- "Familie sucht 24h Pflege" + [Stadt]

### B2B (Firmenbedarf)
- site:wlw.de "Vertrieb" + [Branche/Region]
- "suche Vertriebspartner B2B"

### Crypto
```
curl -s "https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum,solana,ripple,binancecoin&vs_currencies=eur,usd&include_24hr_change=true"
```

## URL-CHECK
ERLAUBT: /s-anzeige/+ID, /firma/+Name, /inserat/+ID
VERBOTEN: /s-suche/, /search?, /s-kategorie/, nur Domain, Duplikate
