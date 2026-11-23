# Arbetsregler för millionsfromdefault

Projekt: hitta konkursbon (främst via konkurslistan.se) som kan köpas ut och transformeras med AI. Två användare delar repot. Claude håller repot uppdaterat och konsekvent.

## Agenter
Roller och beslutsgränser finns i `docs/org.md`, agentfilerna i `.claude/agents/`. Agenter skickar aldrig mejl och kontaktar aldrig förvaltare eller bolag; de skriver utkast.

## Språk
Svenska i all text. Kod, filnamn och JSON-nycklar på engelska eller som de redan är.

## Regler
- **Data:** `data/companies.json` är sanningskällan för dashboarden. Följ schemat i `data/README.md`. Ändra aldrig befintliga `id` och behåll fältordningen.
- **Källor:** Varje påstående om ett bolag ska gå att spåra (länk eller dokument). Skriv `null` hellre än att gissa. Markera uppskattningar med `"estimated": true` i bolagets `notes`.
- **Poäng:** Sätt `ai_adoption`, `ai_efficiency`, `ai_revenue`, `ai_speed` och `buyability` enligt skalorna i `docs/thesis.md` (AI-poäng 0–20), och motivera kort i `notes`.
- **Personuppgifter:** Håll dem minimala. Skriv bolagsuppgifter, inte privatpersoner (undantag: namngiven konkursförvaltare och VD som de står i offentliga register).
- **Skrapa inte** konkurslistan.se i bulk. Hämta enstaka sidor manuellt eller med måttlig takt och respektera deras villkor.
- **Commits:** Små, en sak per commit, svenska eller engelska meddelanden i imperativ. Pusha till `main` så länge vi är två; öppna PR om något är riskabelt.
- **Dashboarden** (`site/`) ska fungera utan bygg-steg: ren HTML/CSS/JS, inga externa beroenden.

## Vid ändringar
0. Kör `git pull --rebase origin main` först, så att vi inte skriver över varandras ändringar i `data/companies.json`.
1. Uppdatera `data/companies.json` och/eller `docs/`.
2. Kontrollera att JSON är giltig: `python3 -m json.tool data/companies.json > /dev/null`.
3. Uppdatera README om strukturen ändras.
