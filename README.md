# Sports Data

The common sports-data vocabulary -- leagues, the teams and players in them, and the games (fixtures) they play with their scores -- distilled from the APIs that already exist. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Sports, Sports Data, Sports Betting, Fantasy Sports, Football, Soccer, Basketball, Baseball, Esports, Odds in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| league | 21 | 17 | name 82%, id 76% | leagues 14, tournaments 8, competitions 4, tournament 2 |
| team | 26 | 21 | name 86%, id 81% | teams 19, team 4, squads 3, clubs 2 |
| player | 21 | 17 | id 94%, name 82% | players 18, player 4, athletes 1, athlete 1 |
| game | 26 | 23 | id 52% | matches 12, fixtures 7, games 6, schedule 5 |

Cohort: 64 providers with harvested OpenAPI, 38 crosswalks. Of the providers exposing a league: 29% create, 100% list, 71% fetch, 19% update, 14% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- Leagues, teams and players agree on id and name and on little else: team abbreviation reaches 33%, and player first_name, last_name and position each reach 47%.
- Games agree only on id; status is at 48% and start_at 35%. Home and away teams appear under a different name, nesting and score shape at nearly every provider -- the game is where sports data providers differ most.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- The market's word is kept per concept: league for competitions and tournaments, game for matches, fixtures and events.
- Odds and betting markets were left out of this pass; they are a sportsbook context of their own.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
