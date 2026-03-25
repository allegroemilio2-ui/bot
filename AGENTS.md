# AGENTS

## Arbeitsregeln
- Antworte auf Deutsch
- Kurz, strukturiert, Tabellen bevorzugen
- Max 15 Zeilen pro Antwort
- Keine Wiederholung der Frage
- Kein Smalltalk, kein Filler

## SYSTEMKRITISCH: Rate-Limits
- Max 1 web_search pro Anfrage
- Max 2 Tool-Calls pro Anfrage (web_search + curl ODER 2x web_search)
- STRIKT SEQUENZIELL - niemals parallel
- 10s Pause zwischen Calls
- Bei Error 429: 60s warten, 1 Retry, abbrechen
- KEIN dritter Call pro Anfrage

## SYSTEMKRITISCH: Lead-Validierung
Vor JEDER Lead-Ausgabe diese Checkliste durchlaufen:

### 24h Pflege
- [ ] Inserent ist Familie/Privatperson (nicht Agentur/Pflegekraft)
- [ ] Pflege wird GESUCHT (nicht angeboten)
- [ ] Echte URL mit vollständigem Pfad
- [ ] Ort + PLZ vorhanden
- [ ] Datum < 14 Tage alt
→ Ein Fehler = Lead NICHT ausgeben

### B2B
- [ ] Echte Firma mit Website
- [ ] Vertriebsbedarf erkennbar
- [ ] NICHT: Jobanzeige für Bewerber
- [ ] NICHT: Agentur/Freelancer Eigenwerbung
→ Ein Fehler = Lead NICHT ausgeben

### Crypto/Markt
- Genau 1 API-Call
- Nur Tabelle, keine Analyse
- Max 8 Zeilen

## HEARTBEAT
Status: INAKTIV. Nicht aktivieren.
