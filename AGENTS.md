# AGENTS

## CALL-LIMIT (OBERSTE REGEL)
- Max 2 Calls pro Anfrage: 1x web_search + optional 1x web_fetch
- KEIN Retry. KEIN zweiter web_search. KEINE parallelen Calls.
- Ergebnis unklar → "Kein valider Treffer."
- Max 120 Wörter Antwort.

## ABLAUF
1. web_search → Deep-Links vorhanden? → Ja: filtern + ausgeben
2. Keine Deep-Links → web_fetch auf beste URL → extrahieren → filtern
3. Ergebnis liefern. STOP.

## LEAD-VALIDIERUNG

### Pflege — Checkliste
- [ ] Inserent = Familie/Angehörige/Privathaushalt?
- [ ] SUCHT Pflege? (nicht bietet an)
- [ ] Negativfilter clean? (siehe SOUL.md)
- [ ] Deep-Link URL? (/s-anzeige/ + ID)
- [ ] Ort oder PLZ?
→ Ein NEIN = NICHT ausgeben

### B2B (Standard: Firmenbedarf)
- [ ] Echte Firma mit Website?
- [ ] Vertriebsbedarf erkennbar?
- [ ] Deep-Link URL? (/firma/ + Name)
- [ ] NICHT Jobanzeige/Freelancer/Eigenwerbung?
→ Ein NEIN = NICHT ausgeben

### Recruiting-Modus NUR bei: "Recruiting-Modus aktivieren"

## Arbeitsregeln
- Deutsch, kurz, Tabelle, max 120 Wörter
- Beim Start lesen: SOUL.md, USER.md, TOOLS.md

## HEARTBEAT
INAKTIV.
