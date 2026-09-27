# Product Brief: MinMat

**Forfattar:** Magnus  
**Emne:** Programmering med KI  
**Dato:** 27. september 2026

## Executive Summary

For folk som bur åleine og lagar mat til seg sjølv, lagar vi MinMat: ei nettside som veit kva du har på kjøkkenet, slik at du ikkje går tom midt i matlaginga. I dag må du hugse kva som står i kjøleskapet og skapa, og det går ofte gale. Du handlar noko du alt har, eller oppdagar at mjølka er tom når middagen er halvvegs laga.

MinMat fjernar det manuelle arbeidet som gjer at folk gir opp slike oversikter. Du tek eit bilde av kvitteringa, og varene blir lagde inn automatisk. Når du brukar noko, skriv du det med vanlege ord, til dømes «brukte 1 egg». MinMat sender deg ein e-post når ei vare kjem under grensa du sjølv har sett.

Det er aktuelt no fordi KI-modellar har blitt gode nok til å lese rotete kvitteringar og forstå vanleg språk. Eksisterande appar viser at behovet finst, men dei er laga for å redusere matsvinn, ikkje for å hindre at du går tom.

## Problemet

Folk som bur åleine, har ingen andre som held oversikt over kjøkkenet, og dei handlar ofte på veg heim utan å vite kva dei har. I dag løyser dei det ved å sjå i kjøleskapet før dei går, prøve å hugse det, eller skrive ei handleliste som fort blir utdatert.

**Eit typisk døme:** Eg skulle lage middag og handla inn det eg trudde eg mangla. Eg var sikker på at eg hadde mjølk. Då eg kom heim og byrja å lage maten, var mjølka tom, og eg måtte avbryte middagslaginga for å gå tilbake til butikken. Minst éin gong i månaden går eg tom for noko eg trudde eg hadde, eller kjøper noko eg alt har.

Dette kostar tid og ekstra turar på butikken. Det fører òg til dobbeltkjøp av varer du alt har, som igjen aukar matsvinnet. Viss ingenting endrar seg, held folk fram med å stole på hukommelsen, og den sviktar nettopp når dei er travle.

## Løysinga

Med MinMat har brukaren alltid ei oppdatert oversikt over kjøkkenet i lomma, utan å måtte registrere alt for hand.

- **Etter handling:** Brukaren tek eit bilde av kvitteringa. Varene dukkar opp i oversikta, og brukaren rettar opp det MinMat ikkje forstod.
- **Når noko blir brukt:** Brukaren skriv det med vanlege ord, som «brukte 1 egg» eller «drakk opp mjølka». Oversikta blir oppdatert.
- **Før det er for seint:** Brukaren set sjølv kva som er «lite» for kvar vare, og får ein e-post når ei vare kjem under grensa.
- **I butikken:** Brukaren opnar MinMat på mobilen og ser kva som faktisk er heime, i staden for å gjette.

Resultatet er færre avbrotne middagar, færre ekstra turar på butikken og mindre dobbeltkjøp. MinMat er ei nettside som er laga for bruk på mobil. Val av teknologi og KI-modell blir tekne i arkitekturfasen.

## Kva som gjer det annleis

MinMat er ikkje den første løysinga for matlager. Fordelen er ei anna vinkling: MinMat skal hindre at du går tom, ikkje først og fremst varsle om utløpsdato. I tillegg er han laga for norske forhold.

| Alternativ i dag | Kvifor folk nøyer seg med det | Kvifor MinMat er betre |
| --- | --- | --- |
| Sjå i skapa og hugse | Gratis og krev inga oppsett | Hukommelsen sviktar i butikken, der du treng han |
| Handleliste på papir eller mobil | Enkel og kjend | Lista viser kva du vil kjøpe, ikkje kva du har |
| Lagerappar med strekkode, som [NoWaste](https://apps.apple.com/no/app/mat-liste-til-fryseboks-kj/id926211004?l=no) | Gir oversikt | Kvar vare må skannast for hand, og folk gir opp |
| KI-lagerappar med kvitteringsskanning, som [Fridge Inventory & AI Scan](https://apps.apple.com/us/app/fridge-inventory-ai-scan/id6757185053), [Pantry Eagle](https://pantryeagle.com/) og [Fango](https://fango.fi/no/blog/sjekk-utlopsdato-pa-mat-app/) | Løyser registreringa | Dei fleste er bygde rundt utløpsdato og matsvinn, og er på engelsk |

Det MinMat kan forsvare er ei tettare løysing for eitt konkret problem: å gå tom. Det inkluderer tolking av norske kvitteringar og oppdatering på norsk. Fordelen ligg i utføringa og fokuset, ikkje i ein teknologi som ingen andre har.

## Kven det er for

**Primærbrukar:** Ein person som bur åleine, handlar sjølv og lagar mat til seg sjølv. Det er typisk ein student eller ung vaksen som handlar på veg heim frå skule eller jobb.

Denne brukaren vil lage middag utan avbrot og slepp helst å planleggje handlinga i detalj. Suksess i kvardagen ser slik ut: han står i butikken, opnar MinMat og veit med ein gong om han treng mjølk. Når han kjem heim, har han det han treng.

Husstandar med fleire personar, som kollektiv og familiar, er ikkje målgruppa for første versjon. Dei krev delt lager og er ein del av visjonen.

## Suksesskriterium

MinMat fungerer når lageret på nettsida stemmer med kjøkkenet, og brukarane held det oppdatert over tid. Tala under er forslag og blir målte i ein testperiode med 5–10 testbrukarar over 2 veker. Før det simulerer KI testbrukarar og lagar testkvitteringar og forbruksmeldingar, slik at vi finn og rettar dei fleste feila. Dei ekte brukarane måler adopsjon, samsvar og om dei går sjeldnare tom. For å ha noko å samanlikne med, loggfører testbrukarane i 2 veker før testen kor ofte dei går tom for ei vare eller kjøper noko dei alt har.

| Signal | Måltal eller bevis | Mål | Når det blir målt |
| --- | --- | --- | --- |
| Resultat for brukaren | Tal på gonger brukaren går tom for ei vare eller kjøper noko han alt har | Halvert samanlikna med dei 2 vekene før testen | Etter 2 vekers test |
| Adopsjon og åtferd | Del av brukarane som registrerer forbruk minst 3 gonger i veka | 70 % | Veke 2 i testen |
| Kvalitet og tillit | Del av kvitteringslinjene som blir tolka rett utan retting | 85 % | Test med 20 ekte kvitteringar |
| Kvalitet og tillit | Samsvar mellom MinMat og kjøkkenet ved stikkprøve | 90 % av varene | Slutten av testen |
| Mål for prosjektet | Kjernen, altså skanning, oppdatering og e-postvarsel, fungerer frå start til slutt | Demonstrert live | Innlevering |

Den største antakinga er at brukarane faktisk registrerer det dei brukar. Viss adopsjonsmålet ikkje blir nådd, er det viktigare å gjere oppdateringa enklare enn å leggje til nye funksjonar.

## Scope

Første versjon skal berre bevise at éin person kan halde eit korrekt lager med lite arbeid og få varsel før varene går tomme.

**INN i versjon 1**

1. Innlogging for éin brukar med eige lager
2. Skanning av kvitteringar, der KI les varene og brukaren godkjenner eller rettar
3. Oppdatering av forbruk med vanleg tekst
4. Grense for «lite» som brukaren set sjølv per vare, og e-post når grensa blir nådd
5. Oversikt over lageret som kan søkjast i og brukast i butikken

**UT av versjon 1**

1. Fleire brukarar eller delt lager for husstanden
2. Oppskriftsforslag ut frå det som er heime
3. Sporing av utløpsdato og varsel om det
4. Automatiske grenser som MinMat lærer av brukaren sine rutinar
5. Oppdatering av forbruk med bilde, og rekning av mengder ut frå bilde av kjøleskapet
6. Eigen mobilapp og push-varsel

## Visjon

Om 2–3 år skal MinMat vere kjøkkenassistenten som veit kva du har, kva du treng og kva du kan lage.

| Fase | Innhald |
| --- | --- |
| No: versjon 1 | Bevis at éin person kan halde eit korrekt lager med kvitteringsskanning og e-postvarsel |
| Neste | Eigen mobilapp med push-varsel, oppdatering med bilde, delt lager for kollektiv og familiar, sporing av utløpsdato og grenser som MinMat lærer av rutinane dine |
| Om 2–3 år | Oppskriftsforslag ut frå det du har, handleliste som lagar seg sjølv, og mindre matsvinn i heile husstanden |

Kvar fase byggjer på den førre. Oppskrifter og automatiske handlelister er berre nyttige når lageret frå versjon 1 er til å stole på.
