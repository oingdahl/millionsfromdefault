# Data

Två JSON-filer. Dashboarden i `site/` läser dem direkt, och den publiceras om vid varje ändring här. Bara researchchef (eller Olle/Fredrik) skriver till `companies.json`; VD skriver till `reports.json`.

## companies.json

Lista (JSON-array) med ett objekt per bolag.

| Fält | Typ | Beskrivning |
|---|---|---|
| `id` | sträng | Organisationsnummer utan bindestreck, t.ex. `5561234567`. Unikt, ändras aldrig. |
| `name` | sträng | Bolagsnamn |
| `industry` | sträng | Bransch i klartext |
| `city` | sträng/null | Ort |
| `revenue_ksek` | tal/null | Omsättning senaste bokslut, tkr |
| `employees` | tal/null | Antal anställda senaste bokslut |
| `bankruptcy_date` | sträng/null | Konkursdatum, `YYYY-MM-DD` |
| `source_url` | sträng/null | Länk, normalt konkurslistan.se |
| `ai_adoption` | tal/null | 1–5, se `docs/thesis.md` (lågt är bra) |
| `ai_potential` | tal/null | 1–5, se `docs/thesis.md` |
| `ai_levers` | lista | Korta AI-hävstänger, t.ex. `["Offertautomation", "Schemaläggning"]` |
| `upside_msek` | tal/null | Grovt uppskattad uppsida, Mkr (se analysfilen) |
| `est_price_msek` | tal/null | Uppskattat köppris för inkråmet, Mkr |
| `trustee` | objekt/null | Konkursförvaltare: `{ "name", "firm", "phone", "email", "source" }`. Bara yrkeskontaktuppgifter. |
| `bid_deadline` | sträng/null | Sista dag för bud, `YYYY-MM-DD` |
| `analysis` | sträng/null | Sökväg till analysfil, t.ex. `docs/companies/5561234567.md` |
| `status` | sträng | `ny`, `granskas`, `kontaktad`, `bud`, `avslutad` |
| `outcome` | sträng/null | Endast vid `avslutad`: `köpt`, `förlorat`, `avfört` |
| `found_by` | sträng | Vem hittade bolaget (person eller agent) |
| `assigned_to` | sträng/null | Vem driver det just nu |
| `added` | sträng | `YYYY-MM-DD` |
| `updated` | sträng | `YYYY-MM-DD` |
| `updated_by` | sträng/null | Senaste person eller agent som ändrade raden |
| `notes` | sträng | Motivering, källor, uppskattningar |

Exempel:

```json
{
  "id": "5560000000",
  "name": "Exempel Städ AB",
  "industry": "Städ och facility services",
  "city": "Malmö",
  "revenue_ksek": 24000,
  "employees": 31,
  "bankruptcy_date": "2026-11-10",
  "source_url": "https://www.konkurslistan.se/",
  "ai_adoption": 1,
  "ai_potential": 4,
  "ai_levers": ["Schemaläggning", "Offertautomation", "Kundtjänst"],
  "upside_msek": 6.5,
  "est_price_msek": 1.2,
  "trustee": { "name": "Förnamn Efternamn", "firm": "Advokatbyrå AB", "phone": "08-000 00 00", "email": "namn@byra.se", "source": "Konkursbeslut" },
  "bid_deadline": "2026-12-05",
  "analysis": "docs/companies/5560000000.md",
  "status": "granskas",
  "outcome": null,
  "found_by": "screening",
  "assigned_to": "analys",
  "added": "2026-11-22",
  "updated": "2026-11-22",
  "updated_by": "researchchef",
  "notes": "Exempel. Manuell schemaläggning och offertgivning. Uppsida uppskattad."
}
```

## reports.json

Lista med VD:ns rapporter, nyaste först.

| Fält | Typ | Beskrivning |
|---|---|---|
| `date` | sträng | `YYYY-MM-DD` |
| `author` | sträng | Normalt `vd` |
| `title` | sträng | Kort rubrik |
| `decisions` | lista | Beslut Olle och Fredrik behöver fatta: `[{ "text", "company_id", "deadline" }]` |
| `body` | sträng | Rapporten i enkel markdown (rubriker `##`, punktlistor `-`, **fet**) |
