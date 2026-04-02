# Product repo contract template

## Doel van dit document
Dit document is een **canonieke template** voor lokale productrepo-contracten.

Het doel van een productrepo-contract is:
- Claude- en Codex-agents dwingen eerst de lokale productrealiteit te lezen
- shared canon en lokale productlogica scherp uit elkaar houden
- voorkomen dat lokale parser-, label- of rendererkeuzes stilzwijgend als platformwaarheid worden behandeld

Deze template canoniseert dus **de vorm en functie van een lokaal contract**, niet de inhoud van een specifiek product.

## Wanneer deze template gebruikt moet worden
Gebruik deze template in een productrepo wanneer:
- nieuwe content wordt toegevoegd
- bestaande content wordt aangepast
- feedback- of evaluatorlogica wordt gewijzigd
- adapters worden gebouwd tussen shared content en lokale productstructuren
- agents moeten bepalen welke parsing- of spellinglogica lokaal geldt

## Leeshierarchie voor agents
Bij werk in een productrepo geldt deze volgorde:
1. lees eerst `shared/grammar-core/`
2. lees daarna het lokale productrepo-contract
3. lees pas daarna de taakprompt

Zonder stap 2 mogen agents geen conclusies trekken over:
- lokale labels
- lokale annotatievormen
- lokale rendererlogica
- lokale progressionlogica
- lokale contentbronnen

## Wat een lokaal productrepo-contract wél moet vastleggen
Een lokaal contract mag expliciet vastleggen:

### 1. Label inventory
Alleen de labels die lokaal in dat product bestaan.

Doel:
- agents voorkomen dat ze nieuwe labels verzinnen
- gedeelde didactische principes correct mappen op lokale producttermen

### 2. Annotation model
Alleen de annotatievorm die lokaal in dat product geldt.

Doel:
- agents voorkomen dat ze een lokale parse- of contentvorm verkeerd veronderstellen

### 3. Supported phenomena
Welke grammaticale verschijnselen het product daadwerkelijk ondersteunt.

Doel:
- onderscheid maken tussen gedeelde didactische ambitie en lokaal ondersteunde functionaliteit

### 4. Feedback hooks
Welke lokale feedbackpunten of interventiehaakjes het product technisch of inhoudelijk kent.

Doel:
- agents voorkomen dat ze gedeelde feedbackprincipes verwarren met lokale feedbackdatastructuren

### 5. Risks / ambiguities to avoid
Welke lokale ambiguïteiten of bekende valkuilen vermeden moeten worden.

Doel:
- inhoudelijke eenduidigheid bewaken
- lokale analysecompromissen zichtbaar maken

### 6. Local adapter notes
Alleen als relevant: hoe shared content of gedeelde taxonomie lokaal wordt vertaald.

Doel:
- adapters expliciet houden
- schema-drift of verborgen mappinglogica voorkomen

## Wat een lokaal productrepo-contract níét mag doen
Een lokaal contract mag niet:
- lokale productstructuren presenteren als gedeeld canon
- `grammar-core` tegenspreken op didactisch of governance-niveau
- lokale rendererkeuzes verhullen als inhoudelijke noodzaak
- lokale annotatievormen impliciet normatief maken voor andere producten

## Wat expliciet lokaal moet blijven
De volgende soorten informatie horen in een lokaal productrepo-contract en **niet** in `grammar-core` als gedeelde canon:
- lokale labelinventaris
- lokale annotatievelden
- lokale JSON-shapes
- lokale contentopslagvormen
- lokale role quirks
- lokale subrole-systematiek
- lokale UI-stappen en rendererlogica
- lokale feedbackmatrixstructuren
- lokale niveaucodering of ID-logica

## Wat expliciet niet uit een lokaal contract mag worden afgeleid
Ook als een productrepo-contract dit beschrijft, mag daaruit **niet** worden afgeleid dat het platformbreed canoniek is:
- token-per-woord annotatie
- specifieke chunklogica
- specifieke veldnamen voor ambiguïteit of bijzinfunctie
- productspecifieke labelsets
- productspecifieke progressionniveaus

## Gebruikswijze in migratiewerk
Bij migratie van productrepo naar `grammar-core` geldt:
1. bepaal eerst of iets didactisch/gouvernance-matig portable is
2. controleer daarna of het element nog leunt op lokale contractinhoud
3. als dat zo is, blijft het lokaal of wordt het eerst geabstraheerd
4. alleen echt portable principes mogen naar `grammar-core`

## Template

Gebruik in een productrepo bij voorkeur dit format.

```md
# Repo contract (<productrepo>)

## Purpose
Beschrijf kort waarom dit lokale contract nodig is.

## Label inventory
- lokale labels die in deze repo echt bestaan
- geen gedeelde taxonomieclaims

## Annotation model
- lokale inhouds- of annotatiestructuur
- alleen beschrijven, niet canoniseren

## Supported phenomena
- welke grammaticale verschijnselen lokaal ondersteund worden
- geen speculatieve toekomstwensen

## Feedback hooks
- lokale feedbackhaakjes, foutbronnen of evaluatiepunten
- alleen wat hier echt geldt

## Risks / ambiguities to avoid
- bekende lokale ambiguïteiten
- gevallen die in deze repo afgewezen moeten worden

## Local adapter notes
- alleen indien relevant
- expliciete mapping vanaf shared canon naar lokale structuur
```

## Minimale kwaliteitsregels voor lokale contracten
Een lokaal productrepo-contract is pas bruikbaar als het:
- feitelijk klopt met de huidige repo-inhoud
- compact genoeg is om echt gelezen te worden
- expliciet maakt wat lokaal geldt
- geen gedeelde canon simuleert
- aangepast wordt zodra lokale repo-structuren inhoudelijk veranderen

## Niet toegestaan
- een lokaal contract gebruiken als verborgen vervanging van shared canon
- shared didactische principes overschrijven met lokale productgewoontes
- productlokale datastructuren verpakken als zogenaamd abstract platformmodel
