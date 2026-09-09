# Changelog

Versions follow the scheme recorded in the project's retrieval strategy:
v1.0.0 is the current 4,272-row junction table and 174-row county table.

## v1.0.0 — unreleased

**Initial publication of the dataset repository.**

- `data/california-junctions.csv` — 4,272 rows, regenerated from source before
  publication and byte-identical to the copy served by slicknicklaw.com.
- `data/california-crash-data.csv` — 174 rows, the committed artifact copied
  unchanged. Its generator consumes the raw multi-gigabyte CCRS exports, which
  are retrieved by hand and not committed, so it was not regenerated here.
- Methodology, data dictionary and citation metadata.

### Licence: an initial grant, not a change of terms

This release grants **CC BY 4.0** over the compilation. It is the **first**
licence this dataset has carried, and it is granted here as an initial grant.

Copies of these CSVs published on slicknicklaw.com before v1.0.0 carry the
header *"Public domain source data. Citation requested, not required: Slick Nick
Law."* That statement is not withdrawn and does not apply retroactively in
either direction: **anything published before v1.0.0 stays under the terms it
was published with**, and CC BY 4.0 applies from the deposited v1.0.0 onward.

The reasoning is recorded rather than left implicit. A permissive statement is
not a licence anyone can rely on being withdrawn, so treating CC BY as a
*restriction added later* would misdescribe what happened. Nobody who already
holds an earlier copy loses anything.

CC BY 4.0 was chosen because attribution is the mechanism this dataset depends
on: it is published to be republished, and a citation that carries a link back
is the whole return. A header saying citation is not required gets a dataset
used and not linked.

### Not yet done

No release has been tagged and **no DOI exists**. The first Zenodo deposit will
mint one, and it will then be added to this changelog, `README.md`,
`CITATION.cff` and `.zenodo.json`. Until then, cite the repository and the
version.
