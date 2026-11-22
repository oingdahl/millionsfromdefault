# Källor

| Källa | Använd till | Anmärkning |
|---|---|---|
| [konkurslistan.se](https://www.konkurslistan.se/) | Hitta nya konkursbon, bransch, ort, datum | Primär upptäcktskälla. Frekvent använd. Ingen bulk-skrapning. |
| Bolagsverket | Bekräfta organisationsnummer, status, styrelse | Primärkälla |
| Konkursförvaltaren (kontaktuppgift via konkursbeslut) | Köpbarhet, inkråm, tidplan | Avgörande för att kunna lägga bud |
| Allabolag / Ratsit / Retriever | Omsättning, resultat, anställda över tid | Kontrollera mot årsredovisning |
| Branschrapporter (SCB, Tillväxtverket, branschorgan) | Bedöma AI-adoption i bransch | Anteckna datum och källa i bolagets `notes` |

## Regel
Skriv alltid källa och datum för en uppgift i bolagets `notes` eller i dess analysfil. Obekräftade uppgifter markeras som uppskattningar.
