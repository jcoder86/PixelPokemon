# Pixel Pokemon

Een vriendelijk, frustratie-vrij pixel-art vang-avontuur, gemaakt voor Julian (5 jaar, kan nog niet lezen).
Het hele spel is **echte pixel-art**, volledig in code getekend — geen externe afbeeldingsbestanden voor
de wereld, wezens of personages. Alles draait in één self-contained `index.html`.

## Wat het is

- **Point-and-click** besturing met pathfinding: tik ergens en Julian loopt er via het kortste vrije pad heen,
  netjes om bomen, rotsen en water-randen heen. Een tik geeft altijd beweging.
- **Drie even grote gebieden** in een hub-opzet: centrale map (hub), een schemerige rots/jungle (links, met
  lantaarntjes) en een dorp/boerderij (boven). Reizen gaat via duidelijke doorgangen, altijd via de hub.
- **Varen**: loop over de watergrens en Julian zit meteen op een bootje; stap eraf en hij is weer te voet.
- **~57 eigen wezens** (geïnspireerd op de eerste generatie, maar eigen ontwerp en eigen namen), elk met een
  eigen type-aanval, pixel-animatie en geluid. De standaard-starter heet Pikachu.
- **Mild gevecht om de beurt**: Julians wezen begint altijd, kan nooit echt verliezen (veert meteen weer op),
  en er is altijd een vlucht-knop. Wilde wezens hebben 1–5 hartjes; pas als ze leeg zijn verschijnt het
  vang-minispelletje met de bal (mislukken mag, opnieuw proberen zonder straf).
- **Geen tekst in het spel** (op de twee startknoppen na): alles via iconen, kleuren, pixel-animaties en geluid.
  Cijfers, sterren en hartjes mogen.
- **Verzamelboek (pokedex)** zonder tekst, met lege plekjes voor wat nog te vangen valt. Tik op een gevangen
  wezen om het als actief wezen te kiezen; dat wezen loopt op de map achter Julian aan.
- **Twee gescheiden profielen** in `localStorage`: **START** is Julians blijvende profiel, **Start as guest**
  speelt met een los gast-geheugen dat Julians collectie nooit raakt.

## Lokaal openen

Het is één statisch bestand. Open `index.html` rechtstreeks in een browser, of serveer de map even statisch,
bijvoorbeeld **in een terminal in deze projectmap**:

```bash
python -m http.server 8080
# open daarna http://localhost:8080/index.html
```

Volledig offline speelbaar in Safari op iPad (landscape). Toevoegen aan het beginscherm geeft een
standalone web-app met eigen icoon.

## Productie (Dokploy)

De repo is deploy-klaar als **statische site** via nginx.

- **Host-poort: `3011`** (poort 3010 is bezet door de oudere versie). Zie `docker-compose.yml`.
- In Dokploy: maak een nieuwe app, koppel deze Git-repository, en laat de service draaien op poort **3011**.
  Zet er een subdomein voor.

Het image is gebaseerd op `nginx:alpine` en kopieert simpelweg de statische bestanden:

```bash
docker compose up -d --build
# bereikbaar op http://<host>:3011/
```
