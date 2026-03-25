# TOOLS

## CALL-LIMIT
Max 2 Calls pro Anfrage:
1. web_search (breite Websuche, keine Plattform-Priorisierung)
2. web_fetch (optional, nur wenn Schritt 1 keine konkreten URLs liefert)
Kein Retry. Keine zweite Suche. Keine parallelen Calls.

## SUCHSTRATEGIE
Breite Websuche. Keine Plattform bevorzugen.
Bei jeder web_search MEHRERE Suchbegriffe kombinieren (1 Call, mehrere Queries).

## SUCHBEGRIFFE (MULTI-QUERY)

### Pflege — alle in 1 web_search kombinieren:
- "24h Pflege gesucht"
- "Betreuung für Mutter gesucht"
- "Senior Betreuung gesucht"
- "Privat Pflege gesucht"
- "Angehöriger sucht Betreuung"
- "24 Stunden Pflege privat gesucht"
Optional + [Stadt/Region] ergänzen wenn vom User angegeben.

### B2B — alle in 1 web_search kombinieren:
- "Firma sucht Vertrieb"
- "Firma sucht Terminierung"
- "Unternehmen sucht Neukunden"
- "B2B Terminierung gesucht"
- "Firma sucht Akquise"
Optional + [Branche/Region] ergänzen wenn vom User angegeben.

### Crypto
```
curl -s "https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum,solana,ripple,binancecoin&vs_currencies=eur,usd&include_24hr_change=true"
```

## URL-REGEL
Erlaubt: jede konkrete URL zu einem einzelnen relevanten Ergebnis
Nicht erlaubt: Suchseiten, Startseiten, Kategorieseiten, generische Domains

## ABLAUF
1. Breite web_search mit mehreren Queries
2. Ergebnisse prüfen: konkrete URLs + relevanter Intent?
3. Falls nein → 1x web_fetch auf beste Quelle → extrahieren
4. Filter anwenden → Ergebnis liefern → STOP
