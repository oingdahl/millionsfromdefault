# Investeringstes

## Kärnidé
Köp upp livskraftiga verksamheter som hamnat i konkurs eller är nära det, och skapa värde med AI. Bra kunder och omsättning finns redan. Värdet kan komma på tre sätt: lägre kostnader (effektivisering), nya AI-baserade produkter och tjänster till befintliga kunder (nya intäkter), och snabbare svar, offerter och leveranser som vinner affärer (snabbhet). Det måste också gå att köpa det som bär värdet ur boet.

## Sållningskriterier (måste uppfyllas)
- **Befintlig verksamhet:** Bolaget har levererat till kunder nyligen. Inte ett tomt skal.
- **God omsättning:** Riktvärde senaste bokslut över 5 Mkr. Justeras när vi lär oss mer. Inget övre tak: större bon (t.ex. Rhenus-bolagen, 70–118 Mkr) prövas också (beslut 2026-11-23).
- **Köpbar struktur:** Tillgångar eller rörelse går att överta via konkursförvaltaren (inkråmsförvärv).
- **Hanterbar skuldbild:** Vi tar inte över skulder i inkråmsförvärv, men annan problematik (kunder, avtal, personal) ska vara överblickbar.

## Poängmodell: AI-poäng 0–20 (beslut 2026-11-23)

Fyra dimensioner, var och en 1–5, plus `ai_adoption` som bara påverkar effektiviseringen. Motivera varje poäng kort i `notes` (eller i analysfilen).

**`ai_adoption`**: hur långt verksamheten/branschen har kommit med AI idag.
- 1 = nästan inget digitalt, manuella processer, papper och telefon
- 3 = vanliga affärssystem, viss automation
- 5 = redan AI-drivet

**`ai_efficiency`** (effektivisering): hur stor del av kostnaden är informationsarbete som AI kan ta.
- 1 = fysiskt hantverk utan administrativ tyngd
- 3 = tydliga delar (offert, fakturering, kundtjänst, planering)
- 5 = kärnan är informationsarbete som kan automatiseras

**`ai_revenue`** (nya intäkter): kan bolaget sälja AI-baserade produkter eller tjänster till sina befintliga kunder?
- 1 = ingen rimlig ny produkt, eller kunderna köper bara en fysisk vara
- 3 = det finns en tydlig tilläggstjänst, men kanal eller förtroende är svagt
- 5 = befintlig kundbas, säljkanal och förtroende passar direkt för en AI-tjänst (t.ex. telefoni → AI-receptionist)

**`ai_speed`** (snabbhet): vinner snabbare svar, offerter, bokningar eller leveranser affärer i branschen?
- 1 = kunderna väljer inte på snabbhet
- 3 = snabbhet hjälper men avgör sällan
- 5 = den som svarar först vinner (offertdrivna, akuta eller bokningsdrivna tjänster)

**`buyability`** (köpbarhet): följer det som bär värdet med vid inkråmsförvärv, och hur fort kan AI införas?
- 1 = kunder, avtal eller tillstånd följer inte med eller är redan sålda
- 3 = oklart; kundregister och varumärke kan köpas men avtal och personal är osäkra
- 5 = kundregister, avtal, varumärke och nyckelpersoner kan tas över och verksamheten går att starta snabbt

**AI-poäng** = `ai_efficiency` × (6 − `ai_adoption`) / 5 + `ai_revenue` + `ai_speed` + `buyability`

Max 20. Låg adoption förstärker bara effektiviseringen; den straffar inte bolag där uppsidan är nya intäkter eller snabbhet. Omsättning är tie-breaker. **Hög prioritet = AI-poäng ≥ 12.** Saknas en del räknas poängen inte (visas som –).

Preliminära poäng från screening märks "Preliminärt:" i `notes`. Analys sätter slutliga poäng.

## Signaler på hög potential
- Kundbas och säljkanal som kan bära en AI-tjänst (telefoni, IT, bokföring, försäkring, bemanning)
- Branscher där den som svarar först får jobbet (hantverk på offert, flytt, städ, service)
- Mycket administrativt arbete per intäkt (offerter, orderhantering, bokföring, bemanning, planering)
- Standardiserade kundärenden som kan besvaras automatiskt
- Dokumenttunga processer (försäkring, juridik, redovisning, rekrytering, fastighetsförvaltning)
- Fragmenterade branscher med små aktörer och låg digital mognad

## Röda flaggor
- Beroende av en nyckelperson som lämnat
- Licenser eller tillstånd som inte följer med vid inkråmsförvärv
- Kundbasen försvann före konkursen
- Konkurs orsakad av förlorat huvudkontrakt, inte av dålig kostnadsstruktur

## Statusflöde
`ny` → `granskas` → `kontaktad` → `bud` → `avslutad` (med `utfall`: köpt / förlorat / avfört)

## Att utveckla
Bransch-heatmap över AI-adoption, standardmall för värdering av inkråm, checklista för due diligence med konkursförvaltare.
