# Körkortskollen 🚗

En interaktiv och tillgänglig webbapp för **teoridelen av B-körkortet**, byggd för att hjälpa elever klara Trafikverkets teoriprov (kunskapsprov).

Allt ligger i **en enda fil – `index.html`** (HTML + CSS + JavaScript + alla vägmärken som inline-SVG). Inga externa beroenden, inget byggsteg. Den fungerar offline och kan dubbelklickas direkt i en webbläsare.

## Funktioner

- **Startsida** med översikt och progress för alla 8 teoriområden.
- **Lektioner** – korta, lättlästa genomgångar med illustrationer för varje område:
  trafikregler, vägmärken, fordonskännedom, väglag & väder, riskbeteenden, samspel i trafiken, miljö och miljövänlig körning.
- **Vägmärkesbibliotek** – 25 vanliga vägmärken grupperade efter typ.
- **Övningsläge** – 150 övningsfrågor (flerval) med **direkt feedback och förklaring** efter varje svar. Öva blandat, per område, dina svaga områden eller dina bokmärken.
- **Provläge** – simulerar det riktiga provet: **65 frågor, 50 minuters nedräkning, godkänt vid 52 rätt**. Resultat per område och genomgång av svaren.
- **Progressspårning** – ser vilka områden eleven behärskar och var det behövs mer övning.
- **Bokmärken** – spara svåra frågor och öva enbart dem.
- **Ljust/mörkt läge**, responsiv design (mobil/surfplatta/dator) och tillgänglighetsanpassning (god kontrast, stora knappar, tangentbordsnavigering).

> All elevdata (progress, bokmärken, provhistorik) sparas lokalt i webbläsaren via `localStorage`. Det finns ingen server och ingen inloggning – varje enhet/webbläsare har sin egen framgång.

> **Obs om frågorna:** Trafikverkets riktiga provfrågor är skyddade. Samtliga frågor här är egna, skrivna i samma stil och enligt gällande svenska trafikregler. Använd appen som komplement till körkortsbok och körlektioner.

## Köra lokalt

Dubbelklicka på `index.html` – det är allt. Ingen installation behövs.

## Publicera på Netlify

### Alternativ A – via GitHub (rekommenderat, uppdateras automatiskt)

1. Filerna ligger i repot **`lukasbjork/ta_k-r_kort`**.
2. Gå till [netlify.com](https://www.netlify.com) → **Add new site → Import an existing project**.
3. Välj **GitHub** och repot `ta_k-r_kort`.
4. Inställningar:
   - **Build command:** *(lämna tomt)*
   - **Publish directory:** `.` (repo-roten)
5. Klicka **Deploy**. Klart – varje ny push till `main` driftsätts automatiskt.

### Alternativ B – snabbast (drag & drop, ingen GitHub)

1. Logga in på [netlify.com](https://www.netlify.com).
2. **Add new site → Deploy manually**.
3. Dra in `index.html` (eller hela mappen) i rutan. Sidan är live på sekunder.

## Anpassa innehållet

Allt innehåll ligger som data längst ner i `index.html`:

- `AREAS` – teoriområdena.
- `LESSONS` – lektionstexterna (ren HTML per lektion).
- `SIGNS` – vägmärkena (inline-SVG).
- `QUESTIONS` – frågorna: `{ id, area, fraga, alt:[4], ratt:0-3, forklaring, signId? }`.

Lägg till en fråga genom att kopiera ett `QUESTIONS`-objekt, ge det ett unikt `id`, sätt rätt `area` och ange index för rätt svar i `ratt` (0 = första alternativet).
