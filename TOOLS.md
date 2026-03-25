# TOOLS

## CALL-LIMIT
Max 2 Calls pro Anfrage:
1. web_search (Pflicht — BREITE Websuche, KEINE Plattform-Priorisierung)
2. web_fetch (Optional — nur wenn Schritt 1 keine konkreten URLs liefert)

VERBOTEN: zweiter web_search, zweiter web_fetch, Retry, parallele Calls

## SUCHSTRATEGIE (HARTE REGEL)

IMMER breite Websuche zuerst.
KEINE Plattform automatisch bevorzugen.
NICHT site:kleinanzeigen.de als Standard.
NICHT site:wlw.de als Standard.
KEINE Domain-Einschränkung im Suchbegriff.

Der Agent sucht im offenen Web und wählt DANACH die beste konkrete Quelle.

## SUCHBEGRIFFE

### Pflege
- "Familie sucht 24h Pflege" + [Stadt/Region]
- "Angehörige sucht Betreuung zuhause" + [Region]
- "Privathaushalt sucht Pflegekraft"
- "suche 24h Betreuung für Mutter" OR "für Vater" OR "für Angehörige"
KEINE site:-Einschränkung. Breite Suche.

### B2B (Firmenbedarf)
- "Firma sucht Vertriebspartner" + [Branche/Region]
- "Vertrieb outsourcen Mittelstand"
- "Kaltakquise Dienstleister gesucht"
- "Terminierung auslagern"
KEINE site:-Einschränkung. Breite Suche.

### Crypto
```
curl -s "https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum,solana,ripple,binancecoin&vs_currencies=eur,usd&include_24hr_change=true"
```

## QUELLENLOGIK

Pflege — mögliche Quellen (NICHT priorisiert):
betreut.de, markt.de, quoka.de, pflegehilfe.org, kleinanzeigen.de,
regionale Portale, Foren, lokale Anzeigenportale, allgemeine Webtreffer

B2B — mögliche Quellen (NICHT priorisiert):
Firmenwebsites, Branchenverzeichnisse, wlw.de, LinkedIn,
lokale Firmenverzeichnisse, Google-basierte Webtreffer

Der Agent nimmt was die Suche liefert. Keine Quelle ist bevorzugt.

## URL-CHECK
ERLAUBT: konkrete URL zu einer Einzelanzeige, einem Firmenprofil oder Inserat
VERBOTEN: Suchseiten, Startseiten, Kategorieseiten, nur Domain ohne Pfad, Duplikate

## ABLAUF
1. Breite web_search ausführen
2. Ergebnisse prüfen: konkrete URLs da? → filtern + ausgeben
3. Keine konkreten URLs? → 1x web_fetch auf beste Quelle → extrahieren → filtern
4. Ergebnis liefern. STOP.
