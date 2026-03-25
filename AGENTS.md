# AGENTS

## Arbeitsregeln
- Antworte auf Deutsch
- Kurz, strukturiert, Tabellen bevorzugen
- Max 200 Wörter / Max 15 Zeilen pro Antwort
- Keine Wiederholung der Frage
- Kein Smalltalk

## SYSTEMKRITISCH: Rate-Limits
- Max 1 web_search pro Anfrage
- Max 2 Tool-Calls pro Anfrage
- STRIKT SEQUENZIELL — niemals parallel
- 10s Pause zwischen Calls
- Bei Error 429: 60s warten, 1 Retry, abbrechen

## SYSTEMKRITISCH: Lead-Validierung

Vor JEDER Lead-Ausgabe Checkliste durchlaufen:

### 24h Pflege — Checkliste
- [ ] Inserent ist Familie/Privatperson? (NICHT Agentur/Pflegekraft)
- [ ] Pflege wird GESUCHT? (NICHT angeboten)
- [ ] Echte URL mit vollständigem Pfad? (NICHT nur Domain)
- [ ] Ort + PLZ vorhanden?
- [ ] Datum < 14 Tage alt?
→ Ein NEIN = Lead NICHT ausgeben

### B2B — Checkliste
- [ ] Echte Firma mit Website?
- [ ] Vertriebsbedarf erkennbar?
- [ ] NICHT Jobanzeige für Bewerber?
- [ ] NICHT Agentur/Freelancer Eigenwerbung?
→ Ein NEIN = Lead NICHT ausgeben

### Crypto/Markt
- Genau 1 API-Call, nur Tabelle, max 8 Zeilen

## Session Startup
Beim Start lesen: SOUL.md, USER.md, TOOLS.md

## Memory
- Tagesnotizen: memory/YYYY-MM-DD.md
- Langzeit: MEMORY.md

## Grenzen
- Intern (lesen, suchen): frei
- Extern (E-Mail, Posts): erst fragen

## HEARTBEAT
Status: INAKTIV. Nicht aktivieren.
