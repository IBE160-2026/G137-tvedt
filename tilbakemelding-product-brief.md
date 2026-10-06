# Tilbakemelding på product brief

| | |
|---|---|
| **Gruppe** | G137 – G137-tvedt |
| **Product brief** | `product-brief-minmat.md` (commit `fad9463`) |
| **Tilbakemelding fra** | Faglærer i IBE160 (utarbeidet med KI-støtte) |
| **Dato** | 2026-10-06 |

## Samlet vurdering

- **Godt utgangspunkt med justeringer.** Gruppen kan gå videre og innarbeide punktene under.

**Det som er bra:**

1. Problemet er konkret og personlig forankret: eksempelet med mjølka som var tom midt i middagslagingen, og at det skjer «minst éin gong i månaden», gjør det lett å forstå hva MinMat skal løse. Vinklingen er tydelig – å hindre at man går tom, ikke å varsle om utløpsdato – og tabellen over alternativer (hukommelse, handleliste, NoWaste, Pantry Eagle, Fango) er ærlig og godt begrunnet.
2. Scope er stramt og godt prioritert: fem punkter i v1 (innlogging, kvitteringsskanning med godkjenning, forbruk med vanlig tekst, egne grenser med e-postvarsel, søkbar oversikt) og en tydelig «UT»-liste. Dere har også identifisert den største antakelsen – at brukerne faktisk registrerer forbruket – og hva dere gjør hvis den ikke holder.

**De viktigste endringene:**

1. Legg til funksjonelle suksesskriterier som kan testes uten en brukertest. Kriteriene i dag handler mest om adopsjon og atferd hos 5–10 testbrukere over to uker, med to uker logging i forkant. Det er tidkrevende og avhenger av andre. Behold gjerne brukertesten, men legg til kriterier som «‘brukte 2 egg’ trekker 2 fra beholdningen av egg», «‘drakk opp mjølka’ setter mjølk til 0» og «en vare under grensen utløser nøyaktig én e-post».
2. Planlegg hvordan sensor kan kjøre appen. Kvitteringslesing og tolking av forbruk krever trolig en betalt KI-modell, og e-postvarsel krever en e-posttjeneste. Lag en testmodus med lagrede KI-svar for noen eksempelkvitteringer, og la e-post vises i en lokal testinnboks eller logg i utviklingsmodus.
3. Beskriv hvordan varer og mengder skal håndteres. «Brukte 1 egg» er enkelt, men «drakk opp mjølka», «litt ost» eller en kvittering med «TINE LETTMELK 1L» krever regler for varenavn, enheter og mengder. Bestem i PRD-en hvordan kvitteringslinjer kobles til varer i lageret, og hva som skjer når KI-en er usikker.

## Vanskelighetsgrad og gjennomførbarhet

### Vurdert vanskelighetsgrad

- **Middels**

**Sammenlignbart med:** 2) AI CV- og søknadsassistent (middels). Som CV-assistenten har MinMat flere sammenhengende funksjoner, opplasting av dokumenter (her kvitteringsbilder) som KI skal tolke, og innlogging. Grunnmuren ligner 6) To-do-liste med smarte etiketter (enkel), men kvitteringslesing fra bilde, tolking av fritekst til mengder og e-postvarsel løfter prosjektet til middels.

**Begrunnelse:**

| Faktor | Nivå (lav / middels / høy) | Kommentar |
|---|---|---|
| Domenelogikk – hvor mange og hvor kompliserte regler og beregninger må stemme? | Middels | Lagerbeholdning, enheter og mengder, kobling av kvitteringslinjer til varer, og grenser som utløser varsel. |
| Datamodell – antall entiteter og relasjoner mellom dem | Middels | Bruker, vare, lagerbeholdning, kvittering med linjer, forbrukshendelse og grense/varsel. |
| Brukere, roller og innlogging | Middels | Innlogging med eget lager per bruker. Én rolle. |
| KI-funksjonalitet i appen, f.eks. kall til språkmodell, prompts i koden og håndtering av usikre svar | Middels | To avgrensede KI-oppgaver: lese kvitteringsbilder og tolke forbruk i vanlig tekst. Godt at brukeren alltid godkjenner eller retter. |
| Integrasjoner og eksterne tjenester, f.eks. API-er, betaling og e-post | Middels | KI-modell med bildestøtte og en e-posttjeneste. |
| Sanntid, samtidighet eller flere brukere som påvirker hverandre | Lav | Én bruker per lager. Delt lager er bevisst utenfor v1. |
| Filhåndtering, f.eks. opplasting, PDF-lesing og eksport | Middels | Opplasting av kvitteringsbilder tatt med mobil, ofte skrå, krøllete eller dårlig belyst. |
| Sikkerhet og personvern | Lav | Lite sensitive data, men kvitteringer kan inneholde butikk, tidspunkt og betalingsinformasjon. Ikke lagre selve bildet lenger enn nødvendig. |

**Hva vanskelighetsgraden betyr for dere:**

- _Middels:_ Et godt balansert valg. Pass på at kjerneflyten blir ferdig og stabil før dere legger til mer: skann kvittering → godkjenn varene → registrer forbruk med tekst → se oversikten → få e-post når en vare er under grensen.

### Gjennomførbarhet med BMAD og Claude Code

Dere skal planlegge med BMAD (product brief → PRD → arkitektur → epics og stories) og implementere med Claude Code. Vurderingen under tar hensyn til at det må være tid til hele denne flyten, og til testing, retting og README til slutt.

| Spørsmål | Vurdering (OK / risiko / stor risiko) | Kommentar |
|---|---|---|
| **Tid og omfang** – kan v1 realistisk bli ferdig og stabil i løpet av semesteret, med tid til flere iterasjoner? | OK | Fem tydelige v1-punkter er realistisk for en gruppe på én person. Den planlagte brukertesten over fire uker (to uker logging og to uker test) må planlegges tidlig hvis den skal gjennomføres. |
| **BMAD-flyten** – er briefen konkret nok til at PRD, arkitektur og stories kan lages uten store hull, og blir det overkommelig mange stories? | OK | Briefen er konkret og godt strukturert. Regler for varer, enheter og mengder er det største hullet og bør avklares i PRD-en. |
| **Egnet for Claude Code** – bruker løsningen en vanlig, godt dokumentert teknologistakk som Claude Code håndterer godt, eller krever den nisjeteknologi, spesialmaskinvare eller mye manuell konfigurasjon? | OK | En mobiltilpasset nettside med innlogging, database, bildeopplasting og LLM-kall er godt dokumentert. |
| **Kontroll på KI-ens arbeid** – kan gruppen selv avgjøre om koden gjør det riktige? Krever domenet kunnskap gruppen ikke har, f.eks. avanserte beregninger eller fagregler, så er det vanskelig å kvalitetssikre. | OK | Du kan selv sjekke om en kvittering er riktig lest og om lageret stemmer. Målet om 85 % riktig tolkede kvitteringslinjer på 20 ekte kvitteringer er et godt, konkret mål. |
| **Testbarhet** – finnes det tydelige regler og forventede resultater som tester kan skrives mot? | Risiko | Lagerlogikk og varsling er svært testbare, men briefen mangler funksjonelle kriterier for dem. Kvitteringstolking kan testes mot et fast sett med kvitteringer og fasit. |
| **Kjørbar for sensor** – kan appen kjøres lokalt etter README, uten gruppens nøkler, betalte kontoer eller egen infrastruktur? | Risiko | Ikke beskrevet. KI-modell og e-posttjeneste krever nøkler eller kontoer. Planlegg testmodus og lokal e-post. |
| **Avhengigheter og kostnader** – krever løsningen betalte API-er, f.eks. språkmodeller, og finnes det en plan for kostnad, testmodus eller mock-data? | Risiko | Valg av KI-modell er utsatt til arkitekturen, noe som er greit, men planlegg kostnad for bildeanalyse og en testmodus. Velg en e-posttjeneste med gratisnivå. |

**Konklusjon om gjennomførbarhet:**

- **Gjennomførbart som beskrevet.**

**Forslag til justering av omfang eller vanskelighetsgrad:**

1. Hold v1 som beskrevet, men legg inn manuell registrering av en vare som reserve når kvitteringslesingen feiler. Da fungerer kjerneflyten selv om KI-en ikke forstår en kvittering, og sensor kan prøve appen uten bilder.
2. Gjør brukertesten med 5–10 personer til et tillegg, ikke en forutsetning for at v1 er ferdig. Planlegg den gjerne, men la de funksjonelle kriteriene og testen med 20 kvitteringer være det som avgjør om kjernen virker.

## Hvorfor product brief er viktig for mappen

Product brief er utgangspunktet for PRD, arkitektur, stories og til slutt koden. Del 1 av mappen vurderes blant annet på om sensor kan følge en sporbar vei fra plan til ferdig app. Den vurderes også på om appen gjør det dere har beskrevet, om den er testet, om den er godt designet, og om den kan kjøres etter README. Et uklart, for stort eller for lite brief gjør alt dette vanskeligere senere. Det er mye enklere å rette nå enn sent i semesteret.

## 1. Gjennomgang av briefens deler

| Del av brief | Status | Kommentar |
|---|---|---|
| Executive Summary – er det klart hva appen er, og hvilket problem den løser? | OK | Klart og kort: kvitteringsskanning, forbruk med vanlig tekst og e-post før varene går tomme. |
| The Problem – er problemet konkret, med reelle situasjoner og brukere? | OK | Konkret eksempel og tydelige konsekvenser (ekstra butikkturer, dobbeltkjøp, matsvinn). |
| The Solution – beskriver løsningen brukeropplevelsen, ikke bare teknologi? | OK | Beskriver fire konkrete brukssituasjoner (etter handling, ved forbruk, før det er for sent, i butikken). Teknologi er bevisst utsatt. |
| What Makes This Different – er vurderingen ærlig og realistisk? | OK | Ærlig om at dette ikke er den første lagerappen, og at fordelen ligger i fokus og norske kvitteringer. |
| Who This Serves – er primærbrukerne tydelige, og vet vi hva de trenger? | OK | Tydelig primærbruker (student eller ung voksen som bor alene), med en konkret suksessituasjon i butikken. |
| Success Criteria – kan kriteriene faktisk sjekkes eller testes? | Juster | Gode, målbare tall, men de fleste krever en brukertest over flere uker. Legg til funksjonelle kriterier som kan bli automatiske tester. |
| Scope – er det klart hva som er med i første versjon, og hva som ikke er det? | OK | Tydelig «INN» og «UT», med en god begrunnelse for avgrensningen. |
| Vision – henger visjonen sammen med resten uten å blåse opp omfanget? | OK | Fasene bygger på hverandre, og oppskrifter og handlelister er tydelig plassert etter v1. |

## 2. Utgangspunkt for del 1 av mappen

Punktene følger kriteriene i sensorveiledningen for del 1. Vektene i parentes viser hvor mye hvert kriterium teller i del 1.

| Kriterium i del 1 | Hva briefen bør legge til rette for | Status | Kommentar |
|---|---|---|---|
| **1. Prosess og KI-styring** (30 %) | Brief som er presis nok til at PRD og stories kan bygges direkte på den, slik at krav kan spores fra brief til kode. | OK | Briefen er presis nok til PRD. Den er lastet opp som én fil i rotmappen – legg gjerne videre planleggingsdokumenter i en egen mappe (for eksempel BMAD sin struktur), og oppdater briefen der, så historikken viser utviklingen. |
| **2. Funksjonalitet og omfang** (20 %) | Realistisk omfang for gruppen og semesteret: en tydelig kjerneflyt som kan bli ferdig og stabil, og nok innhold til å vise reell funksjonalitet. | OK | Tydelig kjerneflyt med nok reell funksjonalitet, og et realistisk omfang. |
| **3. Kvalitetssikring og testing** (15 %) | Suksesskriterier og funksjoner som er konkrete nok til å bli testtilfeller. | Juster | Kvitteringsmålet er konkret. Legg til funksjonelle kriterier for lager, forbruk og varsling, og lag et fast sett med testkvitteringer. |
| **4. Design og brukeropplevelse** (10 %) | Tydelige brukere og brukssituasjoner som designet kan bygges rundt, gjerne med de viktigste skjermbildene eller flytene skissert. | OK | Tydelige situasjoner og mobil som hovedenhet. Skissér gjerne godkjenningsskjermen for kvitteringer og oversikten i butikken. |
| **5. Kodekvalitet og arkitektur** (10 %) | Teknologivalg som er begrunnet og ikke mer komplekse enn appen trenger. | OK | Teknologi er bevisst utsatt til arkitekturen. Velg en enkel stakk med én database og én KI-leverandør. |
| **6. README og kjørbarhet** (10 %) | Løsning som andre kan kjøre lokalt uten betalte kontoer, og uten tilgang til gruppens egne tjenester og nøkler. | Juster | Avhengig av KI-modell og e-posttjeneste. Planlegg testmodus, lokal e-post og eksempelkvitteringer, og beskriv dem i README. |
| **7. Ryddighet i repoet** (5 %) | En plan for hvor hemmeligheter, testdata og dokumentasjon skal ligge. | Juster | Ikke beskrevet. Bruk `.env.example` for nøkler, og fjern eller sladd personlig informasjon (for eksempel kortnummer) fra testkvitteringer før de legges i det offentlige repoet. |

## 3. Neste steg for gruppen

1. Legg til 5–8 funksjonelle, testbare suksesskriterier for lager, forbruk og varsling, ved siden av målene for brukertesten.
2. Beskriv i PRD-en hvordan varer, enheter og mengder håndteres, og hva som skjer når KI-en er usikker på en kvitteringslinje eller en forbruksmelding.
3. Velg KI-modell og e-posttjeneste i arkitekturen, og beskriv hvordan sensor kan kjøre appen med testmodus og lokal e-post.

Oppdater product brief i repoet når dere har gjort endringene, slik at historikken viser hvordan planen utviklet seg. Det er en del av prosessen sensor ser etter.
