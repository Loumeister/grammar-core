# Parsingdidactiek — kaders voor grammar-core

## Status van dit document
Dit document legt de **canonieke parsingdidactiek** vast voor `grammar-core`.

Het document is bedoeld voor alle productrepo’s en bridge-taken die werken met:
- grammaticale analyse
- functiebepaling
- voorbereidende denkstappen voor werkwoordspelling
- diagnostische feedback op ontleedfouten
- gedeelde contentselectie voor parseerbare zinnen

Dit document canoniseert **didactische principes**, niet de lokale implementatie van een productrepo.

Het document canoniseert dus nadrukkelijk **niet**:
- Ontleedlab-specifieke annotatievelden
- Ontleedlab-JSON-shapes
- token-per-woord annotatie als platformnorm
- lokale labelinventarissen
- renderer- of interactielogica
- lokale feedbackmatrixvormen

## Hoe dit document gebruikt moet worden
Lees dit document samen met:
- `docs/werkwoordspellingsdidactiek-kaders.md`
- `docs/grammar-platform-principles.md`
- `docs/content-authoring-rules.md`
- `docs/taxonomy-governance.md`
- `docs/repo-sync-strategy.md`

Gebruik dit document wanneer je werkt aan:
- parsinggerichte leerinhoud
- zinnenbanken met grammaticale analyse als leerdoel
- diagnostische parsingfeedback
- bridge-taken tussen ontleden en werkwoordspelling
- productrepo-governance rond lokale parseercontracten

## Wat hier canoniek is
In `grammar-core` zijn de volgende dingen canoniek:
1. parsinggerichte didactische ontwerpprincipes
2. parsinggerichte contentselectieregels
3. parsinggerichte feedbackprincipes
4. governance-afspraken over wat shared blijft en wat lokaal moet blijven

## Wat productspecifiek blijft
Productspecifieke invulling blijft lokaal, bijvoorbeeld:
- welke labels een product exact toont
- hoe een zin visueel wordt opgesplitst
- welke annotatievorm een product intern gebruikt
- welke lokale UI-stapvolgorde een product hanteert
- hoe feedback technisch wordt opgeslagen of gerenderd

---

## Leidende didactische principes

### 1. Denkstappen vóór labeluitkomsten
Parsingonderwijs mag niet worden ingericht als een kale labeloefening.

De leerling moet niet alleen leren **welk label** ergens hoort, maar vooral:
- welke vraag of proef is uitgevoerd
- welke grammaticale functie daarmee is vastgesteld
- waarom naburige alternatieven niet kloppen

Operationele regel:
- Ontwerp parsingtaken zo dat de denkstap zichtbaar, benoembaar of herstelbaar is.
- Een goede parsingtaak toetst niet alleen uitkomstherkenning, maar ook de onderliggende redeneerroute.

### 2. Eén hoofdvalkuil per zin
Een nieuwe zin mag niet tegelijk meerdere nieuwe didactische problemen introduceren als daardoor onduidelijk wordt **wat** er geoefend wordt.

Operationele regel:
- Elke nieuwe zin krijgt één centrale focus of hoofdvalkuil.
- Andere moeilijkheden mogen alleen aanwezig zijn als ze stabiel beheerst worden verondersteld of didactisch niet concurreren met de hoofdfocus.

Niet toegestaan:
- zinnen die tegelijk nieuwe inversie, een nieuw gezegdeonderscheid en een nieuwe voorwerpverwarring als hoofddoel dragen
- zinnen waarbij onduidelijk blijft welke denkstap eigenlijk centraal staat

### 3. Contrast vóór bulk
Nieuwe parsinginhoud moet niet groeien door volume alleen.

Sterkere parsingdidactiek ontstaat wanneer leerlingen betekenisvolle contrasten oefenen, bijvoorbeeld:
- onderwerp versus lijdend voorwerp
- lijdend voorwerp versus meewerkend voorwerp
- vrij voeglijke bepaling versus lexicaal gebonden complement
- handeling versus toestand/eigenschap
- parseerbare basiszin versus vorm met verstorende woordvolgorde

Operationele regel:
- Voeg liever een contrastrijk item toe dan drie quasi-gelijke voorbeelden.
- Bulk zonder nieuw denkwerk is didactisch zwak.

### 4. Natuurlijke Nederlandse zinnen met didactische scherpte
Parsinginhoud moet natuurlijk Nederlands blijven voor onderbouw VO, maar tegelijk didactisch scherp zijn.

Operationele regels:
- Kies idiomatische, geloofwaardige zinnen.
- Laat rijke woordenschat toe als die idiomatisch en leeftijdsgeschikt blijft.
- Vermijd kunstmatig steriele zinnen als die de grammaticale focus niet verbeteren.
- Herschrijf niet alleen om neutraler te klinken; herschrijf alleen wanneer grammaticale eenduidigheid, didactische focus of geschiktheid echt toeneemt.

### 5. Dubbelzinnige schoolanalyses afwijzen
Een parsingtaak is didactisch ongeschikt als twee schoolanalyses verdedigbaar blijven zonder expliciete keuze van analysemodel.

Operationele regel:
- Voeg geen zin toe aan gedeelde parsinginhoud als de bedoelde schoolanalyse niet eenduidig herstelbaar is.
- Twijfelgevallen worden afgewezen of expliciet buiten de gedeelde kern gehouden.

Praktische implicatie:
- Shared content mag niet leunen op verborgen lokale conventies om eenduidig te lijken.

### 6. Diagnostische feedback richt zich op de denkfout
Parsingfeedback moet uitleggen waarom de gemaakte keuze niet klopt.

Minimaal bruikbare parsingfeedback bevat:
- welk onderscheid gemist is
- welke vraag of proef had moeten worden gebruikt
- welke denkstap de leerling nu moet herstellen

Operationele regel:
- Feedback mag niet blijven steken in “fout label”.
- Feedback moet herstelbaar zijn vanuit een denkhandeling of functiebepaling.

### 7. Parsing als voorwaarde voor latere werkwoordspelling
Parsing is geen los eiland binnen het grammaticaonderwijs.

Voor veel werkwoordspellingsproblemen moet de leerling eerst grammaticaal bepalen:
- wat de persoonsvorm is
- wat het onderwerp is
- welke functie een werkwoordsvorm heeft
- of een vorm überhaupt als persoonsvorm, infinitief of deelwoord gelezen moet worden

Operationele regel:
- Parsinginhoud die later als brug naar werkwoordspelling kan dienen, heeft prioriteit boven parsinginhoud zonder transferwaarde.

### 8. Scaffolding van herkenning naar zelfstandig redeneren
Parsingtaken mogen ondersteuning bieden, maar die steun mag niet het leerdoel vervangen.

Operationele regel:
- Bouw ondersteuning zo op dat leerlingen eerst gerichte herkenning oefenen en daarna steeds zelfstandiger redeneren.
- Vermijd taakvormen waarbij leerlingen structureel de juiste uitkomst kunnen raden zonder de grammaticale denkstap te maken.

---

## Ontwerpregels voor parsinggerichte content

### Regel 1. Voeg alleen een nieuwe zin toe bij aantoonbare didactische winst
Een nieuwe zin moet minstens één van deze functies vervullen:
- een nieuw parsingcontrast introduceren
- een bestaande misconceptie zuiverder zichtbaar maken
- dezelfde denkstap in een betekenisvol andere context plaatsen
- parsing expliciet verbinden met latere spelling- of transfertaken

### Regel 2. De centrale denkstap moet benoembaar zijn
Bij elk parsingitem moet de auteur kunnen aangeven:
- welke hoofdvalkuil centraal staat
- welke vraag, proef of redenering de leerling idealiter gebruikt
- welk naburig foutpad waarschijnlijk is

### Regel 3. Uitkomst zonder redenering is didactisch zwak
Als een leerling het item correct kan oplossen zonder functiebepaling of relevante grammaticale redenering, is het item te zwak voor de gedeelde kern.

### Regel 4. Lokale annotatievorm is geen toelatingscriterium voor canon
Een zin is pas geschikt voor de gedeelde kern wanneer de didactische kwaliteit overeind blijft zonder beroep op één specifieke lokale annotatiestructuur.

---

## Feedbackregels voor parsinggerichte producten en bridge-taken

### Minimaal gedeeld feedbackmodel
Een parsinggerichte interventie of feedbackreactie moet kunnen aangeven:
1. welk onderscheid of welke denkstap gemist is
2. welke herstelvraag of proef passend is
3. waarom een naburige verwarring begrijpelijk maar onjuist is

### Wat hier niet canoniek is
Niet canoniek in `grammar-core` zijn:
- lokale sleutelstructuren voor feedbackmatrices
- lokale JSON-vormen voor feedbackopslag
- productspecifieke mapping van foutparen op UI-componenten
- productspecifieke veldnamen voor waarschuwingen of splitfouten

---

## Governancegrens: shared canon versus lokale productinvulling

### Canoniek in `grammar-core`
- didactische principes voor parsinginhoud
- gedeelde kwaliteitscriteria voor parsingzinnen
- gedeelde feedbackprincipes op denkfouten
- de regel dat lokale repo-contracten eerst gelezen moeten worden vóór productwijzigingen

### Lokaal in productrepo’s
- labelinventaris
- annotatiemodel
- rendererlogica
- interactiestappen
- lokale feedbackdatastructuren
- lokale progressionlogica

---

## Verplicht format bij parsinggerichte voorstellen
Bij elk voorstel voor nieuwe parsinginhoud of parsingfeedback moet expliciet worden benoemd:
1. welk didactisch probleem wordt opgelost
2. welke hoofdvalkuil of welk contrast centraal staat
3. welke denkstap de leerling moet uitvoeren
4. welk principe uit dit document de keuze ondersteunt
5. welke onderdelen lokaal productspecifiek blijven

## Niet toegestaan
- Ontleedlab-specifieke annotatievelden hernoemen tot abstracte platformtermen en alsnog canoniseren
- lokale parserstructuren presenteren als gedeelde schema-eis
- bulkmatige parsingcontent toevoegen zonder nieuw denkwerk of nieuw contrast
- dubbelzinnige schoolanalyse opnemen in de gedeelde kern
- parsinginhoud ontwerpen alsof labeluitkomst belangrijker is dan grammaticale redeneerstap
