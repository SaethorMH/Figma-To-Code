# Refleksion – Figma til kode

**Gruppemedlemmer:** Sæþór Máni Hjálmarsson

## Første "forhindring"

### Content bredde så forkert ud

Jeg havde svært ved at få skabelonen og min egen side til at se ens ud, det var som om at 75 rem ikke var det samme i figma som det var på min pc, troede først at det var min skærms størrelse da min skærm er 2560x1600 px, men lige meget hvordan jeg justerede så det ikke rigtigt ud.

### Løsning

Jeg endte med at åbne siden i Firefox for at se om en anden feature var kompatable og i det jeg gør det overraskes jeg af den korrekte body bredde, siden åbner jeg den i Chrome og der ser det hele perfekt ud. Jeg har længe brugt Brave som min standard browser da jeg troede at den var nærmest én-til-én med Chrome (Brave kører på Chromium modellen), men det gør den åbenbart ikke.
Stadig ikke sikker på om det er fordi jeg har ændret indstillinger i browseren men fra nu af tester jeg min egen side i chrome.

---

## Eksempel 1: Indsætning af Icon'er udefra

### Hvor og hvorfor?

I `@components/Cards/ValueCard.astro` skulle der være icon'er der blev valgt udefra.

### Relevant kode

Jeg løste dette ved at lave en ENUM hvor den får et icon navn gennem en astro prop (de bliver tildelt fra api'et).

```astro
---
import Gear from "@icons/gear.svg";
import Globe from "@icons/globe.svg";

const {icon} = Astro.props;

const icons = {
  gear: Gear,
  globe: Globe,
  ...}

const Icon = icons[icon];
---
```

Siden indsætter jeg icon'et via

```astro
{Icon && <Icon />}
```

Hvor `&&` er en shorthand der sikrer at hvis `Icon` eksisterer så indsæt `<Icon />` som bliver til et af De importerede icon-components fx `<Gear />`

```astro
<div class="card" data-theme={theme}>
      <div class="iconContainer">{Icon && <Icon />}</div>
  ... Resten af kortet
</div>
```

### Afprøvning og ændringer

- **Vi testede:** Beskriv situationen, fx en smal skærm, lang tekst eller tastaturbetjening.
- **Vi observerede:** Hvad skete der konkret?
- **Vi ændrede eller mangler:** Hvad rettede I, eller hvad vil være næste skridt?

## Eksempel 2: Skriv navnet på et valgt benspænd

Brug samme struktur som i eksempel 1: Hvor og hvorfor? Relevant kode. Afprøvning og ændringer.

### Afprøvning og ændringer

- **Vi testede:** Beskriv situationen, fx en smal skærm, lang tekst eller tastaturbetjening.
- **Vi observerede:** Hvad skete der konkret?
- **Vi ændrede eller mangler:** Hvad rettede I, eller hvad vil være næste skridt?

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
