# Activision Blizzard GraphQL Schema

## Overview

This is a conceptual GraphQL schema for the Activision Blizzard / Battle.net platform. It is derived from the publicly documented Battle.net REST API (https://develop.battle.net/documentation) and covers the full range of game data and profile services exposed across World of Warcraft, Diablo III, Hearthstone, StarCraft II, Overwatch, and Call of Duty.

The schema is intended as a reference model for how these REST resources could be represented as a unified GraphQL API surface. All field names and types follow the resource structures described in the official Battle.net API documentation and Blizzard's GitHub organization at https://github.com/Blizzard.

## Authentication

The Battle.net API uses OAuth2. Two flows are supported:

- **Client Credentials** — for game data endpoints (no user required).
- **Authorization Code** — for profile endpoints that access a specific Battle.net account's data.

Tokens are scoped to a region (US, EU, KR, TW, CN). The `OAuthToken` and `APIKey` types in this schema represent these credential objects.

## Schema Source

- REST API documentation: https://develop.battle.net/documentation
- GitHub organization: https://github.com/Blizzard
- Schema file: activision-blizzard-schema.graphql

## Type Coverage

The schema defines 80+ named GraphQL types spanning:

### Auth & Identity
- `APIKey` — developer API key metadata
- `OAuthToken` — OAuth2 access token response
- `BattleNetAccount` — top-level Battle.net user account
- `BattleTag` — Battle.net username and discriminator
- `Region` — enum for US, EU, KR, TW, CN regions

### Realms (World of Warcraft)
- `Realm` — WoW realm with type, status, and timezone
- `ConnectedRealm` — group of merged realms
- `RealmStatus` — online/offline status
- `RealmType` — enum (NORMAL, RP, PVP, RP_PVP)

### World of Warcraft – Characters
- `WoWAccount` — Battle.net sub-account containing characters
- `WoWCharacter` — full character with class, race, faction, level, guild, and links to sub-resources
- `CharacterProfile` — extended profile with quests, reputations, professions
- `CharacterRealm` — realm reference on a character
- `CharacterEquipment` — equipped items and sets
- `CharacterStats` — combat statistics (strength, agility, crit, haste, etc.)
- `StatValue` — base vs. effective stat value pair
- `CharacterAchievement` — character-level achievement completion record
- `Achievement` — achievement definition with points and criteria
- `AchievementCriteria` — individual criteria within an achievement
- `CharacterTitle` — title earned by a character

### World of Warcraft – Guilds
- `Guild` — guild with faction, realm, member count, and achievement points
- `GuildRoster` — list of guild members with ranks
- `GuildMember` — character and rank within a guild
- `GuildAchievement` — guild-level achievement completion

### World of Warcraft – Raids & Dungeons
- `Raid` — raid instance with encounters and difficulties
- `RaidEncounter` — boss encounter within a raid
- `RaidBoss` — creature data for an encounter boss
- `RaidDifficulty` — enum (NORMAL, HEROIC, MYTHIC, LFR)
- `RaidProgress` — guild or character raid completion status
- `EncounterProgress` — per-boss kill count and timestamp
- `Dungeon` — dungeon instance
- `DungeonRun` — completed dungeon run with affixes and members
- `DungeonMember` — character that participated in a dungeon run
- `HeroicDungeon` — heroic dungeon completion summary
- `MythicKey` — Mythic+ keystone profile and best runs
- `MythicRating` — numeric and color-coded Mythic+ rating
- `Keystones` — season keystone aggregate
- `AffixSet` — weekly affix combination
- `Affix` — individual Mythic+ affix

### World of Warcraft – Items & Collections
- `WoWItem` — item with quality, level, slot, and pricing
- `ItemSet` — named item set with set bonuses
- `SetBonus` — threshold-based set bonus description
- `Transmog` — transmog appearance record for an item
- `Collections` — character's mounts, pets, toys, and heirlooms
- `CollectionsMount` — mount in a character's collection
- `CollectionsPet` — battle pet with level, type, and stats
- `PetStats` — pet combat statistics
- `CollectionsToy` — toy in a character's collection
- `CollectionsHeirloom` — heirloom with upgrade level

### World of Warcraft – Talents & PvP
- `Talent` — individual talent in a row/column
- `TalentSpec` — specialization grouping role, class, and talents
- `Spell` — spell definition linked to a talent
- `PvPRecord` — character PvP honor level and bracket records
- `BracketRecord` — rating and win/loss record for a PvP bracket
- `MatchStatistics` — played, won, and lost counts

### World of Warcraft – Misc
- `Quest` — quest completion record
- `Reputation` — faction reputation standing and value
- `Profession` — crafting or gathering profession with skill points

### Call of Duty
- `CoDAccount` — CoD account tied to a platform
- `CoDProfile` — full CoD profile with stats, matches, and loadouts
- `CoDStats` — aggregate K/D, wins, score-per-minute, and level
- `CoDMatch` — individual match record with result and loadout
- `CoDLoadout` — weapon and perk configuration
- `Warzone` — Warzone map configuration
- `WarzoneMatch` — Warzone match result with placement and gulag data
- `WarzoneStats` — aggregate Warzone statistics

### Overwatch
- `Overwatch` — top-level Overwatch object with hero roster
- `OWProfile` — player profile with rank, endorsement, and career stats
- `OWHero` — hero definition with role and abilities
- `HeroAbility` — individual ability on a hero
- `OWStats` — per-hero or career stat block
- `HeroStats` — hero-specific time played and win rate
- `CareerStats` — career aggregate statistics

### Diablo III
- `DiabloProfile` — account-level Diablo profile with paragon and heroes
- `DiabloHero` — hero with class, level, hardcore flag, and items
- `DiabloKills` — monster kill counts
- `DiabloTimePlayed` — time played per class
- `DiabloItems` — equipped item slots on a hero
- `DiabloItem` — item reference within Diablo
- `DiabloSkills` — active and passive skill selections
- `DiabloSkill` — individual skill with optional rune
- `DiabloRune` — rune applied to a Diablo skill

### StarCraft II
- `SC2Profile` — player profile with ladder and match history
- `SC2Summary` — swarm level and achievement points
- `SC2Ladder` — ladder placement with MMR, wins, losses
- `SC2Match` — completed match record

### Hearthstone
- `HearthstoneCard` — collectible card with stats and imagery
- `HearthstoneCardSet` — named card set (e.g., Core, Wild)
- `HearthstoneDeck` — deck defined by a share code

## Queries

The root `Query` type provides entry points for all game data and profile resources:

- Account and token resolution
- Realm lookups (individual and list)
- WoW character, equipment, stats, achievements, titles, collections, PvP, and Mythic+
- Guild roster, achievements, and raid progress
- Raid and dungeon listings, affix sets, and keystone profiles
- Item and item set lookups
- CoD and Warzone profile and match data
- Overwatch profile and hero data
- Diablo III profile and hero data
- StarCraft II profile and ladder data
- Hearthstone card search and deck decoding

## Notes

- All write operations are absent from the public Battle.net API; the `Mutation` type contains only an `refreshOAuthToken` placeholder.
- Regional endpoints are modeled via the `Region` enum and are passed as arguments on all game-data queries.
- The schema is conceptual. An actual GraphQL layer would need to be implemented as a proxy or wrapper over the Battle.net REST API.
