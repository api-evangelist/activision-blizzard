# Activision Blizzard

Activision Blizzard is a global video game developer and publisher producing franchises including Call of Duty, World of Warcraft, Diablo, Overwatch, and Candy Crush across console, PC, and mobile platforms.

## APIs

### Battle.net API

Game data and profile APIs for World of Warcraft, Diablo III, Hearthstone, StarCraft II, and Battle.net account information. Requires OAuth2 authentication via develop.battle.net.

- **Portal:** https://develop.battle.net/
- **Documentation:** https://develop.battle.net/documentation
- **Base URL:** https://us.api.blizzard.com
- **OpenAPI:** [openapi/activision-blizzard-battle-net.json](openapi/activision-blizzard-battle-net.json)

## Common Properties

- [Website](https://www.activision-blizzard.com)
- [Developer Portal](https://develop.battle.net/)
- [Documentation](https://develop.battle.net/documentation)
- [Getting Started](https://develop.battle.net/documentation/guides/getting-started)
- [Authentication Guide](https://develop.battle.net/documentation/guides/using-oauth)
- [GitHub Organization](https://github.com/Blizzard)

## Artifacts

- [OpenAPI Spec](openapi/activision-blizzard-battle-net.json)
- [JSON Schema](json-schema/)
- [JSON Structure](json-structure/)
- [Examples](examples/)
- [JSON-LD Context](json-ld/activision-blizzard-context.jsonld)
- [Spectral Rules](rules/activision-blizzard-spectral-rules.yml)
- [Vocabulary](vocabulary/activision-blizzard-vocabulary.yaml)
- [Naftiko Capability](capabilities/game-data.yaml)

## Features

- **World of Warcraft Game Data** — Access WoW character profiles, realm listings, guild data, and item information via the Battle.net API.
- **Diablo III Profiles** — Retrieve Diablo III career profiles and hero data for Battle.net accounts.
- **Hearthstone Cards** — Search and retrieve Hearthstone collectible card data including class, set, and mana cost filters.
- **StarCraft II Profiles** — Access StarCraft II player profiles and ladder data.
- **Battle.net OAuth2** — OAuth2 client credentials and authorization code flows for game data and profile access.
- **Regional API Endpoints** — Battle.net APIs are available across US, EU, KR, TW, and CN regions.

## Use Cases

- **Community App Development** — Build community tools, addons, leaderboards, and companion apps powered by live game data.
- **Game Analytics** — Analyze game statistics, player performance, and progression data across Blizzard franchises.
- **Fan Websites** — Power fan websites and wikis with live character profiles, item databases, and realm status.
- **Discord Bots** — Build Discord bots that surface WoW character lookups, Hearthstone card searches, and Diablo profiles.

## Integrations

- **WoW Community Tools** — Integrate with World of Warcraft addon ecosystems and community platforms like Wowhead and Curseforge.
- **Twitch** — Surface game data in Twitch stream overlays and channel bot integrations.
- **Discord** — Enable Discord server bots to query Blizzard game data for guild and community members.
