# data/companies.json

Lista (JSON-array) med ett objekt per bolag. Dashboarden i `site/` läser filen direkt, och den publiceras om vid varje ändring här.

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
| `status` | sträng | `ny`, `granskas`, `kontaktad`, `bud`, `avslutad` |
| `outcome` | sträng/null | Endast vid `avslutad`: `köpt`, `förlorat`, `avfört` |
| `found_by` | sträng | Vem hittade bolaget |
| `assigned_to` | sträng/null | Vem driver det just nu |
| `added` | sträng | `YYYY-MM-DD` |
| `updated` | sträng | `YYYY-MM-DD` |
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
  "status": "ny",
  "outcome": null,
  "found_by": "Namn",
  "assigned_to": null,
  "added": "2026-11-22",
  "updated": "2026-11-22",
  "notes": "Exempel. Manuell schemaläggning och offertgivning."
}
```
