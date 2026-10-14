# Cocktail Maker

Een cocktailgids voor iPhone, iPad en computer met 22 recepten uit de eigen huisbar.

- Een illustratie, een korte smaaktekst en een leuk weetje bij elke cocktail
- **Benodigdheden:** ingrediënten (om af te vinken), garnituur en materiaal
- **Stappenplan:** voorbereiding en stappen om af te tikken, met een voortgangsbalk
- Hoeveelheden die meeschalen met het aantal cocktails
- Zoeken en filteren (gin, rum, vodka, tequila, bubbels, alcoholvrij, met of zonder shaker)
- Favorieten (bewaard op het toestel zelf)
- **Cocktailkaart** via het menu (☰), te printen of als PDF te openen
- Op de iPad liggend: lijst links, recept rechts, benodigdheden en stappenplan naast elkaar
- Werkt ook offline nadat je de app één keer hebt geopend

## Online zetten met GitHub Pages (gratis)

1. Maak op [github.com](https://github.com) een nieuwe repository aan, bijvoorbeeld `cocktail-maker`. Zet hem op **Public**: GitHub Pages is gratis voor openbare repositories.
2. Klik op **Add file → Upload files** en sleep **de inhoud** van deze map erin: `index.html`, `cocktailkaart.pdf`, `manifest.webmanifest`, `sw.js`, `.nojekyll`, `README.md` en de map `icons`. Klik op **Commit changes**.
   - `.nojekyll` is een verborgen bestand. Zie je het niet? Op de Mac maak je verborgen bestanden in Finder zichtbaar met `Cmd + Shift + .`. Het bestand is niet strikt nodig, dus je mag het ook weglaten.
3. Ga naar **Settings → Pages**. Kies bij *Source* **Deploy from a branch**, dan branch **main** en map **/ (root)**, en klik op **Save**.
4. Na een minuutje staat de app op `https://<jouw-gebruikersnaam>.github.io/cocktail-maker/`.

## Op je iPhone of iPad zetten

Open het adres in **Safari**, tik op het deel-icoon en kies **Zet op beginscherm**. De app opent dan schermvullend, met een eigen icoon, net als een gewone app.

## Recepten aanpassen

Alle recepten staan bovenaan het script in `index.html`, in de lijst `const C = [ … ]`. Per cocktail:

| Veld | Betekenis |
|---|---|
| `name`, `glass`, `method` | naam, glas en werkwijze (`Shaker`, `Gebouwd` of `Schenken`) |
| `cat` | filters, bv. `["Gin"]` of `["Alcoholvrij","Bubbels"]` |
| `taste`, `fact`, `note` | smaaktekst, weetje en een eventuele opmerking |
| `ing` | ingrediënten: `[hoeveelheid, eenheid, naam, "g" voor garnituur, meervoud]` |
| `prep`, `steps` | voorbereiding en stappen; `{0}`, `{1}`… verwijzen naar de ingrediënten en schalen mee |
| `look`, `tint` | kleuren en glas van de illustratie |

De indeling van de cocktailkaart staat in `SECTIONS`. Pas je recepten aan, verhoog dan in `sw.js` het versienummer (`cocktail-maker-v1` → `v2`). Dan halen telefoons die de app offline bewaren de nieuwe versie op.

`cocktailkaart.pdf` is een vaste PDF van de kaart. Na wijzigingen kun je ook gewoon op **Printen** drukken in de cocktailkaart en daar als PDF bewaren.
