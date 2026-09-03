# Chamonix Jeopardy

Interaktiv jeopardy-quiz til vennegruppen, bygget til at blive kørt af én quizmaster fra en telefon.

- **1 fil, ingen installation.** Åbn `index.html` i browseren. Virker offline (kun skrifttyperne hentes fra nettet).
- **7 deltagere + quizmaster** som standard — kan sættes til 2–12.
- **30 spørgsmål** i seks kategorier om Chamonix, Mont Blanc, ski, lavinesikkerhed, après-ski og bjerge.

## Sådan spiller I

Der spilles om **højdemeter** i stedet for point: 500 / 1000 / 2000 / 3000 / **4810** (Mont Blancs højde).

1. Skriv deltagernes navne ind, vælg betænkningstid, og tryk **Start quizzen**.
2. Deltageren i tur vælger en kategori og en værdi. Quizmasteren trykker på feltet og læser spørgsmålet op.
3. Uret løber. Tryk **Vis svar** når nogen byder ind eller tiden er gået.
4. Tryk ✓ ud for den, der svarede rigtigt (feltet lukkes), eller ✗ ud for en forkert svarende (feltet bliver åbent, så andre kan byde).
5. **Spalten** — to tilfældige felter er skjulte daily doubles. Kun den, der valgte feltet, må svare, og vedkommende sætter selv sine højdemeter på spil.
6. **Toppen** — når alle 30 felter er taget, går spillet automatisk i finale. Alle skriver en indsats *før* spørgsmålet læses op, og der afregnes til sidst.

Menuen (☰) giver adgang til at rette højdemeter manuelt, skifte betænkningstid og lyd, hoppe direkte til finalen eller nulstille. Pilen ved siden af fortryder sidste pointtildeling.

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

Rækkefølgen i `spm` følger `VAERDIER`. Vil I have flere eller færre kategorier, så tilføj/fjern objekter i `KATEGORIER` — brættet tilpasser sig selv. `ANTAL_SPALTER` styrer hvor mange daily doubles der lægges ud (tilfældigt placeret ved hvert nyt spil, aldrig på 500-rækken).

Faktaspørgsmålene er skrevet med de tal, der gjaldt da quizzen blev lavet — tjek gerne rekorderne igennem inden I spiller.

## Kør den fra telefonen

- **Nemmest:** send `index.html` til dig selv (AirDrop, mail, Drive) og åbn den i browseren.
- **Som app:** åbn filen eller en hostet kopi i Safari/Chrome og vælg *Føj til hjemmeskærm*.
- **Hostet:** slå GitHub Pages til for repoet (Settings → Pages → Deploy from branch), så ligger quizzen på en URL, I kan åbne fra en hvilken som helst telefon.

Skærmen holdes tændt under spillet, hvis browseren tillader det.
