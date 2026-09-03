# Chamonix Jeopardy

Interaktiv jeopardy-quiz til vennegruppen, bygget til at blive kørt af én quizmaster fra en telefon.

- **1 fil, ingen installation.** Åbn `index.html` i browseren. Virker offline (kun skrifttyperne hentes fra nettet).
- **Holdspil.** 7 deltagere fordelt på 2–5 hold, med lodtrækning indbygget. Quizmasteren står udenfor.
- **40 spørgsmål** i otte kategorier: Chamonix-dalen, geografi og natur, ekstremsport, outdoor-mærker, fransk mad, fransk historie, dansk-franske relationer — og "Danskere i Ligue 1", hvor en fransk klub og et årstal skal oversættes til en dansk spiller.

## Sådan spiller I

Der spilles om **højdemeter** i stedet for point: 500 / 1000 / 2000 / 3000 / **4810** (Mont Blancs højde).

1. Skriv deltagernes navne ind, vælg antal hold, og tryk **Træk lod om holdene**. Tryk på et navn for at flytte det til næste hold, hvis lodtrækningen skal justeres, og skriv holdnavnene om efter smag. Tre hold er standard.
2. Vælg betænkningstid og tryk **Start quizzen**.
3. Holdet i tur vælger en kategori og en værdi. Quizmasteren trykker på feltet og læser spørgsmålet op.
4. Det stiplede felt nederst er **Facit · kun dig**. Tryk på det, og det rigtige svar folder sig ud på din skærm alene — uret kører videre imens, og et nyt tryk skjuler det igen. Hvert spørgsmål starter foldet sammen, så facit ikke ligger fremme, hvis nogen kigger med.
5. Uret løber. Tryk **Vis svar og giv point**, når et hold byder ind eller tiden er gået.
6. Tryk ✓ ud for holdet, der svarede rigtigt — så lukkes feltet. Tryk ✗ ud for et hold, der svarede forkert: de mister beløbet, men feltet bliver stående åbent, så de andre hold kan byde ind. Feltet lukker først ved et ✓ eller ved **Ingen tog den**.
7. **Spalten** — to tilfældige felter er skjulte daily doubles. Kun det hold, der valgte feltet, må svare, og sætter selv sine højdemeter på spil. Her lukker feltet uanset om svaret er rigtigt eller forkert.
8. **Toppen** — når alle felter er taget, går spillet automatisk i finale. Hvert hold skriver en indsats *før* spørgsmålet læses op, og der afregnes til sidst.

Menuen (☰) rummer **facitlisten** med alle spørgsmål og svar — god at læse igennem inden I går i gang — og giver adgang til at rette holdenes højdemeter manuelt, skifte betænkningstid og lyd, springe direkte til finalen med **Spring til finalen** eller nulstille. Pilen ved siden af fortryder sidste pointtildeling.

Spillet gemmes løbende i browseren, så en utilsigtet genindlæsning ikke koster runden.

## Ret spørgsmålene

Alt indhold ligger øverst i `<script>`-blokken i `index.html`, under overskriften `▲ SPØRGSMÅLENE`:

```js
const VAERDIER = [500, 1000, 2000, 3000, 4810];

const KATEGORIER = [
  { navn: "Chamonix-dalen",
    spm: [ { q: "spørgsmål", a: "svar" }, ... ] },   // fem, fra let til svær
  ...
];

const FINALE = { kategori: "...", q: "...", a: "..." };
```

Rækkefølgen i `spm` følger `VAERDIER`. Vil I have flere eller færre kategorier, så tilføj/fjern objekter i `KATEGORIER` — brættet tilpasser sig selv. `ANTAL_SPALTER` styrer hvor mange daily doubles der lægges ud (tilfældigt placeret ved hvert nyt spil, aldrig på 500-rækken), og `HOLDNAVNE` er de forvalgte holdnavne.

Faktaspørgsmålene er skrevet med de tal, der gjaldt da quizzen blev lavet — tjek gerne rekorderne igennem inden I spiller.

## Kør den fra telefonen

- **Nemmest:** send `index.html` til dig selv (AirDrop, mail, Drive) og åbn den i browseren.
- **Som app:** åbn filen eller en hostet kopi i Safari/Chrome og vælg *Føj til hjemmeskærm*.
- **Hostet:** slå GitHub Pages til for repoet (Settings → Pages → Deploy from branch), så ligger quizzen på en URL, I kan åbne fra en hvilken som helst telefon.

Skærmen holdes tændt under spillet, hvis browseren tillader det.
