# Hypotheek rekentool Sander Volger - Amsterdam - Noord

Een rekentool van Hypotheek Visie Amsterdam Buikslotermeerplein.

Gratis, standalone hypotheek rekentool (één HTML-bestand, geen build-step, geen externe API's) waarmee bezoekers bruto én netto maandlasten berekenen voor annuïteiten-, lineaire en aflossingsvrije hypotheken.

## Functionaliteit

- Meerdere **leningdelen** met elk een eigen bedrag, aflosvorm, looptijd en **rentevaste periodes** (annuïteit wordt herrekend bij elke renteherziening)
- **Bruto/netto** maandlasten o.b.v. belastingschijven 2026 (tot/vanaf AOW-leeftijd), wettelijk gemaximeerd aftrektarief en de **wettelijke staffel eigenwoningforfait** op basis van de WOZ-waarde (default 90% van het hypotheekbedrag)
- Restschuldgrafiek per leningdeel + totaal, jaaroverzicht bruto/netto
- Klantgegevens, **downloaden/uploaden** van berekeningen (JSON, bestandsnaam = naam + adres + datum), knop **Nieuwe berekening**
- **Printrapport** in huisstijl met kantoorgegevens en adviseur, via `window.open()` zodat printen ook werkt in een Google Sites-iframe
- Nederlandse getalsnotatie (€ 1.234,56), geen localStorage → geschikt voor iframe-embed

## Deployen op sandervolger.nl (GitHub Pages + eigen domein)

Alle URL's (canonical, og:url, JSON-LD, robots.txt, sitemap.xml) staan al ingesteld op **https://sandervolger.nl/** en het `CNAME`-bestand is aanwezig.

1. Maak een repository, bijv. `hypotheek-rekentool`, en push deze bestanden naar de `main`-branch.
2. Ga naar **Settings → Pages → Source: Deploy from a branch → main / (root)**. Het `CNAME`-bestand koppelt automatisch het domein sandervolger.nl.
3. Stel bij je domeinregistrar de DNS in:
   - **A-records** voor `sandervolger.nl` (apex) naar GitHub Pages: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - optioneel **CNAME-record** voor `www` naar `<gebruikersnaam>.github.io` (en voeg dan www toe als redirect)
4. Zet in **Settings → Pages** het vinkje **Enforce HTTPS** aan zodra het certificaat is uitgegeven.
5. Dien `https://sandervolger.nl/sitemap.xml` in via [Google Search Console](https://search.google.com/search-console) (domein-property op sandervolger.nl).

Host je elders (bijv. eigen webhosting)? Upload dan gewoon `index.html`, `robots.txt` en `sitemap.xml` naar de webroot — het `CNAME`-bestand is dan niet nodig.

## SEO & GEO

- **On-page SEO:** title/meta description in het Nederlands, canonical, Open Graph & Twitter Cards, `robots.txt` en `sitemap.xml`, indexeerbare intro- en FAQ-content op de pagina.
- **Lokale SEO (geo):** `geo.region` / `geo.position` / `ICBM` meta-tags en schema.org **FinancialService** met adres, geo-coördinaten, openingstijden en verzorgingsgebied (Amsterdam-Noord).
- **Structured data:** JSON-LD met `FinancialService`, `WebApplication` en `FAQPage` — de FAQ staat óók zichtbaar op de pagina (vereist voor rich results).
- **GEO (generative engine optimization):** de FAQ-antwoorden en de intro zijn geschreven als zelfstandige, citeerbare alinea's met concrete feiten (staffel, tarieven, methode), zodat AI-zoekmachines de tool correct kunnen aanhalen; NAP-gegevens (naam, adres, telefoon) staan consistent in tekst én structured data.
- Valideer na livegang met de [Rich Results Test](https://search.google.com/test/rich-results).

## Onderhoud (compliance)

De fiscale parameters (schijven, aftrektarief, EWF-staffel incl. grens € 1.350.000) zijn gebaseerd op 2026 en moeten **jaarlijks** worden gecontroleerd. De berekening is indicatief en geen advies in de zin van de Wft; de disclaimer in de tool en op het printrapport moet zichtbaar blijven.

## Licentie

© Hypotheek Visie Amsterdam Buikslotermeerplein. Logo, foto en merknaam zijn eigendom van Hypotheek Visie; niet herbruikbaar zonder toestemming.
