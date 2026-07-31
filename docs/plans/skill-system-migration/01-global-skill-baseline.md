# 01 — Global skill baseline

## Eindtoestand

De globale Codex-installatie bevat één algemene engineeringmethodologie, twee algemene UI-capabilities en geen actieve Superpowers- of PlanetScale-laag voor deze repos.

## Start in een verse context

- Model: `gpt-5.6-terra`, reasoning `medium`.
- Systeem: resolve `<global-codex-root>` via de werkelijke Codex-configuratie; neem geen gebruikersnaam, driveletter of vaste map aan.
- Lees eerst dit bestand en inventariseer daarna de werkelijke globale installatie.

## Afhankelijkheden

Geen repo-implementatie. Rond deze stap af voordat repo-skills worden opgeschoond.

## Procedure

1. Leg de huidige staat vast met `npx skills list -g --json` en de beschikbare pluginbeheerfunctie.
2. Behoud alleen deze algemene Matt-skills: `ask-matt`, `code-review`, `codebase-design`, `diagnosing-bugs`, `domain-modeling`, `grill-me`, `grill-with-docs`, `grilling`, `handoff`, `implement`, `improve-codebase-architecture`, `prototype`, `research`, `resolving-merge-conflicts`, `setup-matt-pocock-skills`, `tdd`, `teach`, `to-spec`, `to-tickets`, `triage`, `wayfinder`, `writing-great-skills`.
3. Installeer brongetraceerd en globaal:
   - `frontend-design` uit `anthropics/skills`;
   - `web-design-guidelines` uit `vercel-labs/agent-skills`.
4. Start een nieuwe Codex-sessie en bewijs vóór verwijdering dat beide vervangende designskills en de behouden Matt-processkills vindbaar zijn. Bewaar de discovery-output en de twee positieve routingresultaten.
5. Verwijder Superpowers pas nadat stap 4 slaagt. Gebruik de pluginbeheerfunctie en verwijder de ongebruikte marketplace-registratie pas nadat de plugin exact is geïdentificeerd.
6. Verwijder globale PlanetScale-skills en verouderde/projectvreemde skills alleen uit de geïnventariseerde `<global-codex-root>`.
7. Start opnieuw een verse Codex-sessie en controleer de finale discovery en negatieve routing.

## Niet wijzigen

- OpenAI-bundled systeemskills en connectors.
- GitHub-, Google- of andere officiële connectors.
- Repo-lokale `.agents/skills/`.
- Niet-geïdentificeerde directories of gebruikersconfiguratie.

## Deliverables

- Voor/na-JSON van globale skills.
- Bron en versie van iedere behouden of toegevoegde skill.
- Lijst van exact verwijderde plugins, marketplaces en skilldirectories.

## Validatie

- `npx skills list -g --json`
- Positief: “Ontwerp een nieuwe pagina” vindt `frontend-design`.
- Positief: “Audit deze UI op toegankelijkheid en webconventies” vindt `web-design-guidelines`.
- Negatief: geen `superpowers:*`- of PlanetScale-skill wordt aangeboden.
- Combinatie: één Matt-processkill kan samen met één designskill routeren zonder een tweede proces te starten.

## Voltooiingscriteria

Alle behouden globale skills hebben een herleidbare bron, beide designskills waren aantoonbaar vindbaar voordat Superpowers werd verwijderd, ze blijven vindbaar in de finale verse sessie en verwijderde methodologieën routeren niet meer.

## Rollback

Bewaar de voorinventaris. Herinstalleer uitsluitend een verwijderde bron/versie wanneer validatie een vereiste capability mist; herstel nooit een volledige oude skillroot blind.

## Overdracht

Geef de gevalideerde globale inventaris en exacte skillnamen door aan stap 02 en alle productrepo-stappen.
