# TOOLS

## Grundregel
Niemals nur Vorschläge. Suchen und Deep-Links liefern.
Alles STRIKT SEQUENZIELL.

## PFLICHT-ABLAUF FÜR LEAD-SUCHE (2 Schritte)

### Schritt 1: web_search
Suchbegriff eingeben → Du bekommst Suchergebnis-URLs.
Diese URLs sind SUCHSEITEN — NICHT als Lead ausgeben!

### Schritt 2: web_fetch
Die beste Suchergebnis-URL mit web_fetch öffnen.
Aus dem HTML die EINZELANZEIGEN-LINKS extrahieren.
Nur Links die auf eine EINZELNE Anzeige/ein EINZELNES Profil zeigen.

### Beispiel Kleinanzeigen:
```
Schritt 1: web_search "suche 24h Pflege site:kleinanzeigen.de"
→ Ergebnis: https://www.kleinanzeigen.de/s-suche/24h+pflege+gesucht
  (Das ist eine SUCHSEITE → NICHT ausgeben!)

Schritt 2: web_fetch auf diese URL
→ HTML enthält Links wie:
  https://www.kleinanzeigen.de/s-anzeige/suche-24h-pflegekraft-fuer-oma/2847361
  https://www.kleinanzeigen.de/s-anzeige/pflege-gesucht-raum-muenchen/2851003
  (Das sind EINZELANZEIGEN → DIESE ausgeben!)
```

### Beispiel wlw.de:
```
Schritt 1: web_search "Vertrieb outsourcen site:wlw.de"
→ Ergebnis: https://www.wlw.de/de/suche/vertrieb
  (Das ist eine SUCHSEITE → NICHT ausgeben!)

Schritt 2: web_fetch auf diese URL
→ HTML enthält Links wie:
  https://www.wlw.de/de/firma/mueller-vertrieb-gmbh-12345
  (Das ist ein FIRMENPROFIL → DIESES ausgeben!)
```

## URL-VALIDIERUNG (vor jeder Ausgabe)

VERWERFEN wenn URL enthält:
- /s-suche/ → Suchseite
- /s-kategorie/ → Kategorieseite
- /search? oder ?q= → Suchseite
- Nur Domain ohne Pfad
- Bereits ausgegeben (Duplikat)

BEHALTEN wenn URL enthält:
- /s-anzeige/ + numerische ID → Einzelanzeige ✅
- /firma/ + Name → Firmenprofil ✅
- /inserat/ oder /anzeige/ + ID ✅

Kein Deep-Link extrahierbar → Lead NICHT ausgeben.

## web_search Suchbegriffe

### 24h Pflege
- "suche 24h Pflege für Angehörige" + [Stadt]
- site:kleinanzeigen.de "Pflege gesucht privat"
VERBOTEN: "24h Pflege" allein, "Pflegekraft" allein, "Pflegedienst"

### B2B
- "suche Vertriebspartner B2B"
- "Kaltakquise outsourcen Mittelstand"
- site:wlw.de + [Branche]
VERBOTEN: "Vertrieb Jobs", Indeed, StepStone, Monster

### Finanzmarkt
- "DAX S&P 500 Gold aktuell heute"

## exec + curl

### Crypto (GENAU 1 Call)
```
curl -s "https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum,solana,ripple,binancecoin&vs_currencies=eur,usd&include_24hr_change=true&include_7d_change=true"
```

## Erlaubte Quellen
Pflege: kleinanzeigen.de, pflegeboerse.de, betreut.de
B2B: wlw.de, unternehmensregister.de, LinkedIn (öffentlich)

## VERBOTENE Quellen
Indeed, StepStone, Monster, Pflegeagentur-Websites
