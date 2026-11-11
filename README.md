# California crash data

Two public-domain-derived tables compiled from the California Crash Reporting
System (CCRS): surface-street junctions ranked by reported crashes, and
statewide totals by county and year.

Compiled and published by **Slick Nick Law**, San Francisco, California.

| File | Rows | Generated from | What it is |
|---|---|---|---|
| `data/california-junctions.csv` | 4,272 | CCRS retrieved 2026-09-02 | One row per road pairing, per city. Crashes, killed, injured, and a coordinate. |
| `data/california-crash-data.csv` | 174 | CCRS retrieved 2026-11-10 | One row per county per year. Crashes, killed, injured, and pedestrian, bicycle and motorcycle involvement. |

**The two tables come from different retrievals, and the version number does
not tell you which.** v1.1.0 rebuilt the county table and left the junction
table alone — all 4,272 junction rows are byte-for-byte identical to v1.0.0.
Each CSV carries its own generation date in its header; trust that over the
version number. [CHANGELOG.md](CHANGELOG.md) has the figures that moved.

Years covered: 2023, 2024 and 2025. Field-by-field definitions are in
[DATA-DICTIONARY.md](DATA-DICTIONARY.md). How the tables were built, and what
they do and do not support, is in [METHODOLOGY.md](METHODOLOGY.md).

## Nothing here is modelled

No figure is estimated, imputed or filled in. Every number is a count of rows or
a sum of a column in the CCRS files named in the methodology. You can download
those files yourself and get the same answer.

Freeway and ramp pairings are excluded from the junction table by design — it is
a surface-street dataset.

## How to cite

Cite the **concept DOI**. It always resolves to the newest version, which is
what a citation should point at unless you specifically need the version you
read.

> Slick Nick Law (2026). *California crash data: surface-street junctions and county totals, 2023-2025*. Zenodo. https://doi.org/10.5281/zenodo.22669152

To pin the exact version you used:

> Slick Nick Law (2026). *California crash data: surface-street junctions and county totals, 2023-2025*, v1.1.0. Zenodo. https://doi.org/10.5281/zenodo.24145891

| | DOI |
|---|---|
| Concept — all versions, always the newest | [10.5281/zenodo.22669152](https://doi.org/10.5281/zenodo.22669152) |
| v1.0.0 | [10.5281/zenodo.22669154](https://doi.org/10.5281/zenodo.22669154) |
| v1.1.0 | [10.5281/zenodo.24145891](https://doi.org/10.5281/zenodo.24145891) |

Machine-readable citation metadata is in [CITATION.cff](CITATION.cff).

## Licence

**CC BY 4.0** — [LICENSE](LICENSE), full legal code, retrieved from
creativecommons.org.

Attribution is required, and attribution is the point: this dataset exists to be
republished with a link back. Credit *Slick Nick Law* and link to this
repository or to the DOI once one exists.

The underlying CCRS source data is public domain as published by the State of
California. CC BY 4.0 applies to this compilation — the pairing logic, the
county-code mapping, the verification and the assembled tables — not to the
State's raw records.

**Earlier copies carry different terms, deliberately.** Versions of these CSVs
published on slicknicklaw.com before v1.0.0 carry the header *"Public domain
source data. Citation requested, not required"*. CC BY 4.0 is granted **at
v1.0.0 as an initial grant**, not as a change of terms; anything published
before it stays under the terms it was published with. See
[CHANGELOG.md](CHANGELOG.md).

## Where this comes from, and what is canonical

The website repository holds the source and the generator. This repository is
the **canonical citable copy** — it is what a DOI resolves to, and what a
citation should point at. Publication runs one way: generated there, released
here. The site never reads from this repository.

The human-facing pages built from the same data are at
<https://slicknicklaw.com/california-crash-data/>.

## Provenance of this copy

`data/california-junctions.csv` was regenerated from its source before
publication and is byte-identical to the copy the website serves.

`data/california-crash-data.csv` is the committed artifact, copied as-is. Its
generator takes the raw multi-gigabyte CCRS exports as input, and those are
retrieved by hand rather than committed, so it could not be regenerated as part
of this publication. It is unchanged from the file the website serves.
