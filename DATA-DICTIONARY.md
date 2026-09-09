# Data dictionary

Two tables. Both are UTF-8 CSV with a leading comment block; lines beginning
`#` are commentary and are not data. The column header is the first
non-comment line.

## `data/california-junctions.csv` — 4,272 rows

One row per road pairing, per city.

| Column | Type | Definition |
|---|---|---|
| `city` | text | City named on the CHP report. |
| `county` | text | County, resolved from the CCRS numeric county code — see METHODOLOGY.md. |
| `roads` | text | The two roads in the pairing. A pairing counts crashes naming the same two roads in the same city, in either order. |
| `crashes` | integer | Count of CCRS crash records for the pairing. |
| `killed` | integer | Sum of `NumberKilled` over those records. |
| `injured` | integer | Sum of `NumberInjured` over those records. |
| `latitude` | decimal | Approximate coordinate for the junction. |
| `longitude` | decimal | Approximate coordinate for the junction. |

Freeway and ramp pairings are excluded by design.

## `data/california-crash-data.csv` — 174 rows

One row per county per year.

| Column | Type | Definition |
|---|---|---|
| `county_code` | integer | CCRS numeric county code, 1-58. |
| `county` | text | County name, from the California Secretary of State's published county-code list. |
| `year` | integer | 2023, 2024 or 2025. |
| `crashes` | integer | Count of CCRS crash records. Rows flagged `IsDeleted` are excluded. |
| `people_killed` | integer | Sum of `NumberKilled`. |
| `people_injured` | integer | Sum of `NumberInjured`. |
| `pedestrian_involved_crashes` | integer | Crashes where `MotorVehicleInvolvedWith` is `B - Pedestrian`. |
| `bicycle_involved_crashes` | integer | Crashes where `MotorVehicleInvolvedWith` is `G - Bicycle`. |
| `motorcycle_involved_crashes` | integer | Crashes with at least one party whose `Vehicle1TypeDesc` is exactly `Motorcycle`. Motor-driven cycles and scooters of 15hp or less are a separate CCRS category and are **not** included. |

## Two definitions worth reading before you use the junction table

**A road pairing** is not the same as an intersection. A crash record names a
primary road and a secondary road, the latter defined by CHP as "the nearest
crossed road where the crash occurred". Spelling variants of a street type or a
compass direction are treated as the same road, so "Laguna Bl" and "Laguna
Blvd" are one pairing rather than two.

**"At the crossing"** is the subset of a pairing where `SecondaryDistance` is
exactly 0 — the crash was at the crossing rather than a stated distance from it.
A blank distance is not counted, because the CHP layout does not define what
blank means.
