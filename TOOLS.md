# TOOLS

## CALL-LIMIT
Max 2 Calls pro Anfrage:
1. web_search (breite Websuche, keine Plattform-Priorisierung)
2. web_fetch (optional, nur wenn Schritt 1 keine konkreten URLs liefert)
Kein Retry. Keine zweite Suche. Keine parallelen Calls.

## SUCHSTRATEGIE
Breite Websuche. Keine Plattform bevorzugen.
Agent sucht im offenen Web, wählt danach beste Quelle.

## SUCHBEGRIFFE

### Pflege
- "Familie sucht 24h Pflege" + [Stadt/Region]
- "Betreuung für Angehörige gesucht"
- "Pflegekraft gesucht privat"
- "24h Betreuung gesucht für Mutter/Vater"

### B2B (Firmenbedarf)
- "Firma sucht Vertriebspartner"
- "Vertrieb outsourcen Mittelstand"
- "Kaltakquise Dienstleister gesucht"
- "Terminierung auslagern"

### Crypto
```
curl -s "https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum,solana,ripple,binancecoin&vs_currencies=eur,usd&include_24hr_change=true"
```

## URL-REGEL
Erlaubt: jede konkrete URL zu einem einzelnen relevanten Ergebnis
(Einzelanzeige, Firmenprofil, Forenbeitrag, konkreter Eintrag)

Nicht erlaubt:
- Suchseiten (/search?, /s-suche/, ?q=)
- Startseiten / Homepages
- Kategorieseiten
- generische Domain ohne konkreten Eintrag

## ABLAUF
1. Breite web_search
2. Ergebnisse prüfen: konkrete URLs + relevanter Intent?
3. Falls nein → 1x web_fetch auf beste Quelle → extrahieren
4. Filter anwenden → Ergebnis liefern → STOP
