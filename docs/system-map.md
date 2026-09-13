# Systeemkaart

_Actueel op 2026-09-13._

## Bedoeling

De twee producten zijn bedoeld als aanvullende delen van één didactische redeneerlijn:

1. Ontleedlab leert leerlingen grammaticale functies in een volledige zin vaststellen.
2. Werkwoordlab laat leerlingen die analyse gebruiken voor werkwoordspelling en transfer.
3. grammar-core bewaakt alleen de gedeelde taal, didactiek en uitwisselingsgrenzen.

Deze overdracht is nog geen gekoppelde productflow. Er is geen derde, geïntegreerde app en geen gedeelde productruntime.

## Eigenaarschap

| Onderdeel | Is bron voor | Is nadrukkelijk niet bron voor |
|---|---|---|
| `grammar-core` | gedeelde didactiek, taxonomie, schemas, kleine gedeelde content | routes, UI, opslag, scoring, leerlingprofielen |
| `ontledingstrainer` | Ontleedlab-runtime, zinsannotaties, evaluatie, ontleedfeedback | spellingruntime en platformbrede canon |
| `werkwoordlab` | spellingruntime, units, lokale misconcepties, spellingfeedback | ontleedruntime en platformbrede canon |

## Bronhiërarchie

Bij tegenstrijdigheid geldt:

1. uitvoerbare code en tests voor huidig gedrag
2. lokaal productcontract voor bewuste productkeuzes
3. gedeelde canon voor productoverstijgende regels
4. roadmap voor nog niet gerealiseerd werk

Een roadmapclaim mag nooit als bestaand gedrag worden beschreven. Handmatig bijgehouden aantallen, testtotalen en subtree-hashes horen niet in architectuurdocumenten; leid ze af wanneer ze nodig zijn.

## Gedeelde invarianten

- Ontleden en spellen blijven afzonderlijke leerhandelingen. Een toekomstige overdracht ertussen moet expliciet worden ontworpen en getest.
- Vorm en betekenis worden samen gebruikt; een grammaticale proef is een controlemiddel, geen definitie.
- Een deterministische regel bepaalt goed of fout in de kernflow.
- Feedback baseert zich op waarneembare invoer en geeft één concrete herstelhandeling. Zij verzint geen leerlingredenering.
- Een app claimt geen beoordeling, identiteit of gegevensbereik dat de runtime niet werkelijk levert.

Routes, lokale opslag, scoring, oefeningen en experimenten zijn productinvarianten. Hun gezaghebbende beschrijving staat buiten `shared/grammar-core/`: in Ontleedlab is dat `SPEC.md`, in Werkwoordlab `docs/product-spec.md`. Deze contracten worden niet naar `grammar-core` gekopieerd.

## Wijzigingsroute

1. Lokaliseer gedrag in code en tests.
2. Bepaal of de wijziging gedeeld of productlokaal is.
3. Wijzig de kleinste bron van waarheid en één regressietest.
4. Werk alleen documenten bij die door het besluit werkelijk veranderen.
5. Merge gedeelde canon eerst; synchroniseer daarna de subtrees.

Geen nieuwe adapter, service, agent of schema zonder een huidige tweede gebruiker.
