# Skill-system migration

## Doel

Dit dossier migreert `grammar-core`, `werkwoordlab`, `ontledingstrainer` en `dealership` naar één beheersbaar skillsysteem:

- Matt Pocock Skills levert het algemene engineeringproces.
- `frontend-design` en `web-design-guidelines` leveren algemene ontwerp- en auditcapaciteit.
- `.agents/skills/` is de beoogde publieke repo-discoveryroute na afronding van de migratie.
- Repo-skills bevatten alleen domeinkennis en productspecifieke kwaliteitsgates.
- `grammar-core` blijft de canonieke bron voor gedeelde grammaticacontracten.

Iedere genummerde stap is zelfstandig uitvoerbaar in een verse Codex-context.

## Status en padnotatie

Dit dossier beschrijft de doeltoestand, niet de huidige toestand. Totdat de betreffende implementatie-PR is gemerged, kunnen repos nog `.codex/skills/`, plugin-skills of andere bestaande discoveryroutes gebruiken. Inventariseer die werkelijke starttoestand in iedere stap en neem `.agents/skills/` niet voortijdig als runtimewaarheid aan.

Portable placeholders in dit dossier:

- `<workspace-root>`: de lokale map die de afzonderlijke repo-checkouts bevat;
- `<repo-root>`: de checkout van de repo waarop de actuele stap wordt uitgevoerd;
- `<global-codex-root>`: de daadwerkelijk geïnventariseerde globale Codex-root.

Resolve deze paden aan het begin van iedere stap; neem geen gebruikersnaam, driveletter of vaste checkoutlocatie aan.

## Modelcontract

- Gebruik `gpt-5.6-terra` met `medium` voor inventarisatie, verplaatsen, verwijderen en mechanische referentiewijzigingen.
- Gebruik `gpt-5.6-sol` met `xhigh` voor het ontwerpen, herschrijven en forward-testen van skills.
- Wanneer een stap beide modellen inzet, rondt Terra eerst een bewijsbundel af met basis-SHA, status, inventaris, padmapping, mechanische diff en bewaarde gebruikerswijzigingen. Sol begint pas daarna, controleert die afgebakende diff en is eigenaar van semantische skillwijzigingen en routingtests. Iedere genummerde stap specificeert deze overdracht opnieuw zodat hij zelfstandig uitvoerbaar blijft.

## Volgorde

1. [01 — Global skill baseline](01-global-skill-baseline.md)
2. [02 — grammar-core canonical skills](02-grammar-core-canonical-skills.md)
3. Merge de implementatie-PR uit stap 02 in `grammar-core`.
4. Maak voor `werkwoordlab` en `ontledingstrainer` elk een afzonderlijke sync-only PR die uitsluitend de gemergede `grammar-core`-toestand binnenhaalt; merge die PR’s.
5. Start daarna pas de productmigratiebranches uit de productbasisbranches die de sync-merge bevatten: [03 — werkwoordlab](03-werkwoordlab-skill-migration.md) en [04 — ontledingstrainer](04-ontledingstrainer-skill-migration.md).
6. Voer [05 — dealership](05-dealership-skill-migration.md) uit.
7. Voer [06 — cross-repo validation and cleanup](06-cross-repo-validation-and-cleanup.md) uit.

De sync-only PR’s voor `werkwoordlab` en `ontledingstrainer` mogen na de merge van stap 02 parallel worden uitgevoerd. Ook stappen 03 en 04 mogen parallel, maar pas nadat de eigen sync-only PR is gemerged; combineer subtree-sync en wrappermigratie niet in één branch of PR. Stap 05 is inhoudelijk onafhankelijk maar moet dezelfde globale baseline gebruiken. Stap 06 start pas als alle sync- en implementatie-PR’s gereed zijn.

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
