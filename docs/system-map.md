# Systeemkaart

_Actueel op 2026-09-12._

## Bedoeling

Het systeem ondersteunt één doorgaande redeneerlijn:

1. Ontleedlab leert leerlingen grammaticale functies in een volledige zin vaststellen.
2. Werkwoordlab laat leerlingen die analyse gebruiken voor werkwoordspelling en transfer.
3. grammar-core bewaakt alleen de gedeelde taal, didactiek en uitwisselingsgrenzen.

Er is nu geen derde, geïntegreerde app en geen gedeelde productruntime.

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

## Productinvarianten

### Ontleedlab

- De standaardroute laat alle toepasselijke rollen tegelijk aanwijzen.
- De Rollenladder is uitsluitend een verborgen experiment via `#/rollenladder`.
- Alleen laddervoortgang mag lokaal bewaard blijven; activatie nooit.
- Feedback baseert zich op de waarneembare keuze en geeft één concrete herstelhandeling. Zij verzint geen leerlingredenering.

### Werkwoordlab

- Grammaticale functie gaat vóór spellingregel.
- Een deterministische evaluator bepaalt goed/fout; generatieve beoordeling hoort niet in de kernflow.
- Voortgang en docentinzichten zijn lokaal op één browser zolang er geen echte gegevensgrens en identiteit bestaan.
- Een transfertaak die niet werkelijk wordt beoordeeld, wordt als zelfcontrole gepresenteerd en niet als automatische rubric.

## Wijzigingsroute

1. Lokaliseer gedrag in code en tests.
2. Bepaal of de wijziging gedeeld of productlokaal is.
3. Wijzig de kleinste bron van waarheid en één regressietest.
4. Werk alleen documenten bij die door het besluit werkelijk veranderen.
5. Merge gedeelde canon eerst; synchroniseer daarna de subtrees.

Geen nieuwe adapter, service, agent of schema zonder een huidige tweede gebruiker.
