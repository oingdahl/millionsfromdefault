# Organisation

Projektet drivs av OI och FW med fyra Claude-agenter. Agenterna förbereder, ägarna beslutar.

```
            OI & FW  (beslut: kontakt, bud, köp)
                   │
                  VD          prioriterar, väljer fördjupningar, veckorapport
                   │
              Researchchef    fördelar, granskar, enda som skriver companies.json
              ┌────┴────┐
         Screening    Analys
         (bredd)      (djup)
```

| Agent | Fil | Modell | Gör | Skriver |
|---|---|---|---|---|
| VD | `.claude/agents/vd.md` | opus | Prioriterar, väljer max 3 fördjupningar/vecka, bevakar buddeadlines, veckorapport | `data/reports.json`, status/ansvar i `companies.json` |
| Researchchef | `.claude/agents/researchchef.md` | opus | Delegerar, kvalitetsgranskar, kalibrerar poäng, förhindrar dubbletter | `data/companies.json` |
| Screening | `.claude/agents/screening.md` | sonnet | Går igenom nya konkurser på konkurslistan.se, sållar, preliminär AI-poäng | Inget (returnerar kandidater) |
| Analys | `.claude/agents/analys.md` | opus | Fördjupning: fakta, förvaltare, deadline, AI-hävstänger, uppsida, röda flaggor | `docs/companies/<orgnr>.md` |

## Rytm
- **Varje vardag 07:12:** screening via researchchef (schemalagd uppgift). Nya bolag (minst 50 Mkr) med preliminär AI-poäng ≥ 11 analyseras direkt i samma körning, högst 3 per körning (beslut OI 2026-11-27).
- **Måndagar 07:42:** VD-rapport (schemalagd uppgift). VD prioriterar och fördjupar de bolag som screeningen inte hann analysera.
- **Vid behov:** be Claude "kör analys på <bolag>" eller "fråga VD om läget".

## Mänskliga beslut
Kontakt med förvaltare, bud, köp och allt som kostar pengar görs av OI eller FW. Agenterna skriver utkast men skickar aldrig något.

## Data
Allt sparas i repot (`data/*.json`, `docs/companies/`). Dashboarden läser filerna och publiceras vid varje push.
