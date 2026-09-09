# Methodology

The authoritative version of this document is published at
<https://slicknicklaw.com/california-crash-data/methodology/>. This copy travels
with the data so the dataset is self-describing; where the two differ, the
published page is canonical.

## The source

The **California Crash Reporting System (CCRS)**, published by the California
Highway Patrol on the California Open Data Portal. It is public domain, and it
needs no account, no key and no form.

- Dataset: California Crash Reporting System (CCRS)
- Publisher: California Highway Patrol
- Licence: public domain, as published on data.ca.gov
- Field definitions: CCRS Raw Data Export Layout, 9/27/2024, California Highway
  Patrol Information Technology Section
- Retrieved: 2026-09-02
- Portal: <https://data.ca.gov/dataset/ccrs>

Files used, as downloaded:

| File | Bytes |
|---|---|
| `crashes_2023.csv` | 193,732,146 |
| `parties_2023.csv` | 211,652,130 |
| `crashes_2024.csv` | 197,631,820 |
| `parties_2024.csv` | 217,102,627 |
| `crashes_2025.csv` | 187,075,855 |
| `parties_2025.csv` | 210,730,895 |

## Nothing is modelled

If a number appears in these tables it is a count of rows or a sum of a column
in the files above. No figure is estimated, imputed or interpolated.

## What each figure means

- **A crash** — one record in the CCRS Crashes file. Rows flagged `IsDeleted`
  are excluded.
- **People killed** — sum of `NumberKilled` over those records.
- **People injured** — sum of `NumberInjured` over those records.
- **Pedestrian-involved** — crashes where `MotorVehicleInvolvedWith` is
  `B - Pedestrian`, the crash-level field on the CHP report.
- **Bicycle-involved** — crashes where `MotorVehicleInvolvedWith` is
  `G - Bicycle`.
- **Motorcycle-involved** — crashes with at least one party in the CCRS Parties
  file whose `Vehicle1TypeDesc` is exactly "Motorcycle". Motor-driven cycles
  and scooters of 15hp or less are a separate CCRS category and are not
  included.

## County codes

CCRS records a county as a number. The export layout defines the field as "the
unique code of the county in which the crash occurred" but does not publish the
list, so the mapping used here is the State's own published list of California
county codes from the Secretary of State. It was checked against the data before
use: records coded 19 carry Los Angeles County city names, and records coded 37
carry San Diego County city names.

Records whose county code falls outside 1-58 are left out of the county tables
and counted separately rather than being assigned to a county — 2 records in
2023, 18 in 2024 and 39 in 2025. They remain in the statewide totals.

## SWITRS, SafeTREC and TIMS

Three names come up constantly in California crash data and they are not
interchangeable.

- **SWITRS** — the Statewide Integrated Traffic Records System, the long-running
  CHP collision database. It closed to public access and CCRS replaced it.
- **SafeTREC** — the Safe Transportation Research and Education Center at
  UC Berkeley.
- **TIMS** — the Transportation Injury Mapping System, built by SafeTREC on
  SWITRS data. It geocodes collisions and offers free query and mapping tools,
  and it is the better instrument if you want to *map* crashes rather than
  *count* them.

This dataset cites them as lineage and as a better tool for a different job. It
does not draw its numbers from them. Every figure here comes from the currently
published CCRS files, so that anything in these tables can be reproduced from a
download anyone can make without an account.

## How to read a ranking

Read it as a ranking of busy places before you read it as a ranking of dangerous
ones. Exposure is not in this data: there is no traffic volume, no pedestrian
count, no signal inventory. A junction that carries more people will tend to
record more crashes.

Counts of this size are also noisier than they look. A junction whose true rate
is ten crashes a year will record somewhere between roughly four and sixteen in
a given two-year window without anything changing on the ground. A difference of
two or three crashes between neighbouring rows is not a difference.

## Sources

- California Crash Reporting System, California Open Data Portal
- Safe Transportation Research and Education Center (SafeTREC), UC Berkeley
- Transportation Injury Mapping System (TIMS)
- California Secretary of State, California County Codes
