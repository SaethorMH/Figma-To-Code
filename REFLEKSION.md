# Refleksion – Figma til kode

**Gruppemedlemmer:** Sæþór Máni Hjálmarsson

## Sådan bruger I filen

Skriv jeres fælles refleksion direkte i denne fil. Erstat hjælpeteksterne med jeres egne erfaringer, og slet Markdown-guiden og demoen inden aflevering. Skriv kort og konkret, og brug eksempler fra jeres egen kode.

Åbn forhåndsvisningen i VS Code med **Cmd + Shift + V** (Mac) eller **Ctrl + Shift + V** (Windows). Så ser I, hvordan Markdown bliver vist. På GitHub vises formateringen automatisk, når I åbner filen.

### Mini-guide til Markdown

- `# Titel` er dokumentets hovedoverskrift. Brug kun én.
- `## Afsnit` og `### Underafsnit` giver overskrifter i flere niveauer.
- `**vigtig tekst**` bliver til **vigtig tekst**.
- En bindestreg efterfulgt af et mellemrum laver en punktopstilling som denne.
- Skriv kode inde i en sætning mellem enkelte backticks, fx `getTeamMembers()`.
- Links skrives sådan: `[Astros dokumentation](https://docs.astro.build/)`.
- Lav et nyt afsnit med en tom linje. Brug også en tom linje før og efter lister og kodeblokke.

En kodeblok starter og slutter med tre backticks. Skriv sproget efter de første, fx `js`, `css`, `html` eller `astro`. Se et eksempel i filens kildekode nedenfor.

### Kort demo – sådan kan tekst, kode og link kombineres

> Dette er et opdigtet eksempel på formen, ikke en færdig refleksion eller et ekstra krav.

Vi flyttede datahentningen til en fælles funktion, så endpointet kun skal vedligeholdes ét sted.

```js
export function getServices() {
  return apiFetch("https://ftk-api.pages.dev/services");
}
```

I komponenten kalder vi `getServices()`. Vi kontrollerede, at de samme servicetitler blev vist før og efter ændringen. Næste skridt er at undersøge, hvad der sker, hvis API'et returnerer en fejl.

Reference: [Datahentning i Astro](https://docs.astro.build/en/guides/data-fetching/).

---

## Første "forhindring"

### Content bredde så forkert ud

Jeg havde svært ved at få skabelonen og min egen side til at se ens ud, det var som om at 75 rem ikke var det samme i figma som det var på min pc, troede først at det var min skærms størrelse da min skærm er 2560x1600 px, men lige meget hvordan jeg justerede så det ikke rigtigt ud.

### Løsning

Jeg endte med at åbne siden i Firefox for at se om en anden feature var kompatable og i det jeg gør det overraskes jeg af den korrekte body bredde, siden åbner jeg den i Chrome og der ser det hele perfekt ud. Jeg har længe brugt Brave som min standard browser da jeg troede at den var nærmest én-til-én med Chrome (Brave kører på Chromium modellen), men det gør den åbenbart ikke.
Stadig ikke sikker på om det er fordi jeg har ændret indstillinger i browseren men fra nu af tester jeg min egen side i chrome.

---

## Eksempel 1: Skriv navnet på et valgt benspænd

### Hvor og hvorfor?

Hvor i løsningen bruger I teknikken, og hvilket konkret problem løser den? Henvis gerne til en fil, fx `src/components/MinKomponent.astro`.

### Relevant kode

Indsæt en kort kodeblok fra jeres løsning. Vælg det passende sprog, og forklar den del, der er vigtig for jeres valg.

### Afprøvning og ændringer

- **Vi testede:** Beskriv situationen, fx en smal skærm, lang tekst eller tastaturbetjening.
- **Vi observerede:** Hvad skete der konkret?
- **Vi ændrede eller mangler:** Hvad rettede I, eller hvad vil være næste skridt?

## Eksempel 2: Skriv navnet på et valgt benspænd

Brug samme struktur som i eksempel 1: Hvor og hvorfor? Relevant kode. Afprøvning og ændringer.

## Eksempel 3: Skriv navnet på et valgt benspænd

Brug samme struktur som i eksempel 1: Hvor og hvorfor? Relevant kode. Afprøvning og ændringer.

## Fallback og robusthed

Dette må gerne indgå i de tre eksempler ovenfor. Hvis det allerede er dækket dér, kan I slette dette afsnit.

- **Fallback/progressive enhancement:** Beskriv mindst ét konkret eksempel. Hvad oplever brugeren med og uden understøttelse? Link til dokumentation for den valgte feature, og angiv de browsere og versioner, I har testet.
- **Defensive CSS:** Vis et konkret eksempel på, hvordan løsningen håndterer fx lang tekst eller lidt plads.
- **Global CSS og komponent-CSS:** Forklar kort, hvad I har placeret hvor, og hvorfor.

## Brug af AI

Hvis I har brugt AI til en væsentlig del af løsningen, så beskriv kort:

- Hvad brugte I den til?
- Hvad ændrede eller fravalgte I i svaret?
- Hvad lærte I, og hvordan kontrollerede I løsningen?

Hvis I ikke har brugt AI, kan I blot skrive det. I skal ikke indsætte en komplet chatlog.
