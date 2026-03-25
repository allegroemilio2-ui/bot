# AGENTS

## CALL-LIMIT
- Max 2 Calls: 1x web_search + optional 1x web_fetch
- KEIN Retry. KEIN zweiter Search. KEINE parallelen Calls.
- Ergebnis unklar → "Kein valider Treffer."
- Max 120 Wörter Antwort.

## SUCHSTRATEGIE
IMMER breite Websuche. KEINE Plattform-Priorisierung.
Der Agent sucht im offenen Web und wählt danach die beste Quelle.

## ABLAUF
1. Breite web_search → konkrete URLs vorhanden? → filtern + ausgeben
2. Keine konkreten URLs → 1x web_fetch auf beste Quelle → extrahieren
3. Ergebnis liefern. STOP.

## LEAD-VALIDIERUNG

### Pflege
- [ ] Inserent = Familie/Angehörige/Privathaushalt?
- [ ] SUCHT Pflege? (nicht bietet an)
- [ ] Negativfilter clean? (siehe SOUL.md)
- [ ] Konkrete URL? (nicht Suchseite/Startseite/Domain)
- [ ] Ort oder PLZ?
→ Ein NEIN = NICHT ausgeben

### B2B (Standard: Firmenbedarf)
- [ ] Echte Firma mit Website?
- [ ] Vertriebsbedarf erkennbar?
- [ ] Konkrete URL? (nicht Suchseite/Startseite)
- [ ] NICHT Jobanzeige/Freelancer/Eigenwerbung?
→ Ein NEIN = NICHT ausgeben

### Recruiting-Modus NUR bei: "Recruiting-Modus aktivieren"

## Arbeitsregeln
- Deutsch, kurz, Tabelle, max 120 Wörter
- Beim Start lesen: SOUL.md, USER.md, TOOLS.md

## HEARTBEAT
INAKTIV.
