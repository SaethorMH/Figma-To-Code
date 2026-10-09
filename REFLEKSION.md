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

## Eksempel 2: Details transition i forskellige bruvser.

### Hvor og hvorfor

På siden `@pages/about.astro` skulle der være en accordion FAQ, denne skulle helst have en lille animation på sig så den ikke bare "snap"ede fra lukket til åben. Sådanne animtioner er ikke fuldt supportet i alle browsere, så det skal være et fallback hvis den ikke er. I praksis har jeg dog gjort det omvendt med **Progressive Enchancement**, således at grunden er den samme, men dem der understøtter får mere.

### Relavant kode

Jeg difinerer først details'ne uden animationenerne, siden laver jeg en:
`css  @supports (interpolate-size: allow-keywords) {...}`
Denne `@supports` sikrer at koden inden i sig kun kører hvis browseren understøtter `interpolate-size: allow-keywords`, hvis ikke, ignorerer den den indlejrede kode.

### Afprøvning og ændringer

- **Vi testede:** Jeg testede i Chrome der uderstøtter, og siden i Firefox der ikke understøtter
- **Vi observerede:** At det som forventet virkede i Chrome men ikke Firefox men begge havde den samme "grund" funktionalitet.
- **Documentation:** [Interprolate-Size](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/interpolate-size)

## Eksempel 3: Team Member responsivitet

Kæmpede længe med at få team medlemmer kortene til at være resposive. Endte med at lave en container querie ud fra det de blev sat i.

### Relevant kode

Jeg skrev
`   @container card (width <=50rem) {...}` ind i `@components/Cards/MemberCard.astro`, den laver querie'en på forældre elementet der har container navnet card, `container: card / inline-size`.

- **Global CSS og komponent-CSS:**
  Global CSS har jeg defineret nogle store træk som bliver genbrugt flere steder i forskellige komponenter. Dér har jeg også brugt tokens til at definere generelle ting.
  I komponenterne har jeg lavet den CSS, jeg vil have til at ramme det enkelte komponent (eller dens nærmeste elementer fx børn i `<slot />` via `:global()`)

## Brug af AI

Jeg har ikke brugt AI til meget andet end en mere fejlfinding med forklaringer, da den ofte ville komme med bud på andre måder at gøre tingene på som vi ikke havde lært det i timerne, som ikke gav mening i den fulde kontekst.
Dette bestod oftest af at smide hele komponentet ind i Claude.ai og spørge om noget specifikt fx. "Hvorfor flugter denne component ikke med content-start".
