# Organisation

Projektet drivs av Oscar och Fredrik med fyra Claude-agenter. Agenterna förbereder, ägarna beslutar.

```
            Oscar & Fredrik  (beslut: kontakt, bud, köp)
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
- **Varje vardag 07:12:** screening via researchchef (schemalagd uppgift).
- **Måndagar 07:42:** VD-rapport (schemalagd uppgift).
- **Vid behov:** be Claude "kör analys på <bolag>" eller "fråga VD om läget".

## Mänskliga beslut
Kontakt med förvaltare, bud, köp och allt som kostar pengar görs av Oscar eller Fredrik. Agenterna skriver utkast men skickar aldrig något.

## Data
Allt sparas i repot (`data/*.json`, `docs/companies/`). Dashboarden läser filerna och publiceras vid varje push.
