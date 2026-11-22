# millionsfromdefault

Delat arbetsrepo för att hitta och utvärdera konkursbon som kan köpas ut och byggas om med AI.

## Idén

Vi söker på [konkurslistan.se](https://www.konkurslistan.se/) efter bolag med **god omsättning och befintlig verksamhet**, i branscher eller bolag där **AI-adoptionen idag är låg**. Tesen är att en köpare kan ta över verksamheten billigt ur konkurs och skapa värde genom AI-transformation: automatiserade processer, lägre kostnadsbas och bättre kundflöden.

Se [`docs/thesis.md`](docs/thesis.md) för kriterier och bedömningsmodell.

## Struktur

| Sökväg | Innehåll |
|---|---|
| `data/companies.json` | Pipeline: alla bolag vi har tittat på, med bedömning, uppsida, förvaltare och status |
| `data/reports.json` | VD-agentens veckorapporter |
| `data/README.md` | Fältbeskrivning för `companies.json` |
| `docs/thesis.md` | Investeringstes, sållningskriterier, poängmodell |
| `docs/sources.md` | Källor och hur vi använder dem |
| `docs/companies/` | Fördjupade bolagsanalyser, en fil per bolag (mall: `_mall.md`) |
| `docs/org.md` | Agentorganisationen: roller, rytm, beslutsgränser |
| `.claude/agents/` | Agenterna: `vd`, `researchchef`, `screening`, `analys` |
| `site/` | Dashboarden (statisk sida, publiceras på GitHub Pages) |
| `.github/workflows/pages.yml` | Publicerar dashboarden vid push till `main` |
| `CLAUDE.md` | Arbetsregler för Claude i det här repot |

## Dashboard

Live: https://oingdahl.github.io/millionsfromdefault/

Dashboarden i `site/index.html` läser `data/*.json` och visar nyckeltal, VD:ns senaste rapport och beslut, kommande buddeadlines, störst uppsida, förvaltarkontakter och en sorterbar tabell.

Publicering sker via GitHub Actions (se `.github/workflows/pages.yml`).

Lokalt: `python3 -m http.server -d . 8000` och öppna `http://localhost:8000/site/`.

## Agenter
Fyra Claude-agenter gör jobbet, se [`docs/org.md`](docs/org.md). Screening körs varje vardag och VD-rapporten varje måndag som schemalagda uppgifter. Säg till exempel "kör analys på <bolag>" eller "fråga VD om läget" i en Claude-session med repot. Kontakt med förvaltare och bud görs alltid av Oscar eller Fredrik.

## Arbetssätt

1. Hitta bolag på konkurslistan.se, lägg till en rad i `data/companies.json` (status `ny`).
2. Bedöm enligt `docs/thesis.md` och fyll i poängen.
3. Lovande bolag får en egen analys i `docs/companies/<orgnr>.md`.
4. Uppdatera `status` och `assigned_to` när något händer. Dashboarden följer med.

Kontrollera alltid uppgifter mot primärkällor (Bolagsverket, konkursförvaltaren) innan något beslut tas. Det här repot är underlag, inte juridisk eller finansiell rådgivning.
