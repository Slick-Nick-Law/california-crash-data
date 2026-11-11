# Changelog

Versions follow the scheme recorded in the project's retrieval strategy.
v1.1.0 is current: a 4,272-row junction table generated 2026-09-02 and a
174-row county table rebuilt from the 2026-11-10 CCRS retrieval. A version may
rebuild one table and not the other -- check each file's own header.

## v1.1.0 — 2026-11-11

**The county table is rebuilt from a newer CCRS retrieval. The junction table
is not, and that is the thing to read before citing this version.**

### What changed

`data/california-crash-data.csv` — rebuilt from CCRS exports retrieved
**2026-11-10**. 174 rows, unchanged in shape. Against v1.0.0:

| Year | Crashes | Killed | Injured |
|---|---|---|---|
| 2023 | 409,822 → 409,834 (+12) | +2 | +4 |
| 2024 | 417,129 → 417,155 (+26) | +0 | +5 |
| 2025 | 401,550 → 402,413 (**+863**) | **+89** | **+497** |

This is late reporting, not a correction. CHP reports reach CCRS for 12 to 18
months after the crash, so the most recent complete year in any export is
incomplete however complete the file looks. 2025 moving by 863 while 2023 and
2024 moved by 12 and 26 is that effect, measured.

**Motorcycle counts did not move in any year, including 2025.** That is
expected, and the reason is below.

### What did not change

`data/california-junctions.csv` — **all 4,272 rows are byte-for-byte identical
to v1.0.0.** Not one junction was added, dropped, or re-counted. Only the
header comments differ.

The junction rankings were generated on **2026-09-02** and were not regenerated
for this version. From v1.1.0 the junction CSV states that generation date in
its own header, so the two files in this release can no longer be read as
sharing one retrieval date — they do not.

**If you are citing junction rankings, you are citing the 2026-09-02 data
whether you cite v1.0.0 or v1.1.0.** If you are citing county or statewide
totals, the version matters.

### A mixed input, disclosed

One of the seven raw exports behind this version is **not** from the 2026-11-10
retrieval. `parties_2025.csv` was **withdrawn from the state portal** between
2026-09-02 and 2026-11-10 and no longer exists upstream. It was restored from
this project's R2 archive of the September snapshot, and is byte-identical by
SHA-256 to the file v1.0.0 was built from.

`motorcycle` is defined from the Parties file, so 2025 motorcycle counts in
this version rest on September party records joined to November crash records.
The join is on Collision Id, and 2025 party records are not revised by a
re-publish of the crash file, so this is defensible — but it is a mix, and the
unchanged motorcycle counts above are its visible signature.

`SOURCE-MANIFEST.md` records bytes and SHA-256 for all seven inputs. All seven
are archived and have been restored from the archive and hash-verified, so this
version is reproducible.

### Not changed in this release

The licence (CC BY 4.0, from v1.0.0 onward), the methodology, the data
dictionary, and the column layouts.

## v1.0.0 — 2026-09-09

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

Tagged and released 2026-09-09; Zenodo mints the DOI from this release. The DOI
is added to `README.md` and `CITATION.cff` in a commit **after** this tag, so
it is not inside the archived v1.0.0 snapshot — a DOI cannot be embedded in the
artifact it identifies. Cite the concept DOI, which always resolves to the
newest version.
