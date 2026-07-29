# Skill-system migration

## Doel

Dit dossier migreert `grammar-core`, `werkwoordlab`, `ontledingstrainer` en `dealership` naar één beheersbaar skillsysteem:

- Matt Pocock Skills levert het algemene engineeringproces.
- `frontend-design` en `web-design-guidelines` leveren algemene ontwerp- en auditcapaciteit.
- `.agents/skills/` is de publieke repo-discoveryroute.
- Repo-skills bevatten alleen domeinkennis en productspecifieke kwaliteitsgates.
- `grammar-core` blijft de canonieke bron voor gedeelde grammaticacontracten.

Iedere genummerde stap is zelfstandig uitvoerbaar in een verse Codex-context.

## Modelcontract

- Gebruik `gpt-5.6-terra` met `medium` voor inventarisatie, verplaatsen, verwijderen en mechanische referentiewijzigingen.
- Gebruik `gpt-5.6-sol` met `xhigh` voor het ontwerpen, herschrijven en forward-testen van skills.
- Laat Sol de inhoudelijke diff na Terra-werk controleren wanneer beide fasen in één stap voorkomen.

## Volgorde

1. [01 — Global skill baseline](01-global-skill-baseline.md)
2. [02 — grammar-core canonical skills](02-grammar-core-canonical-skills.md)
3. Merge de `grammar-core`-PR.
4. [03 — werkwoordlab](03-werkwoordlab-skill-migration.md)
5. [04 — ontledingstrainer](04-ontledingstrainer-skill-migration.md)
6. [05 — dealership](05-dealership-skill-migration.md)
7. [06 — cross-repo validation and cleanup](06-cross-repo-validation-and-cleanup.md)

Stappen 03 en 04 mogen na de merge van stap 02 parallel worden uitgevoerd. Stap 05 is inhoudelijk onafhankelijk maar moet dezelfde globale baseline gebruiken. Stap 06 start pas als alle implementatie-PR’s gereed zijn.

## Gezamenlijke regels

- Begin met `git status --short --branch`; behoud alle bestaande gebruikerswijzigingen.
- Commit, push, merge, externe labels of PR-mutaties alleen met expliciete autorisatie.
- Verwijder geen globale capability voordat de vervangende capability vindbaar en gevalideerd is.
- Laat directorynaam, frontmatter `name`, `agents/openai.yaml` en catalogusnaam exact overeenkomen.
- Geef iedere skill een precieze trigger, negatieve grenzen, geordende procedure, outputcontract, voltooiingscriteria en escalatiepad.
- Dupliceer geen algemene planning, TDD, debugging, Git, review, frontend of projectmanagement in repo-skills.
- Sluit iedere repo af met `git diff --check`, skillvalidatie, discoverycontrole en relevante productchecks.

## Bewijs per PR

Neem op:

- voor/na-inventaris;
- gewijzigde routing en verwijderde overlap;
- uitgevoerde positieve en negatieve routingtests;
- validatiecommando’s en resultaten;
- bewaarde gebruikerswijzigingen;
- resterende risico’s en rollback.
