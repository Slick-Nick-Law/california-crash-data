# Source manifest — the raw CCRS exports

The county table in this repository is derived from eight raw CCRS exports. They
are far too large to commit (about 1.46 GB together), so this manifest records
what they are precisely enough that a copy can be **verified**, not merely
obtained.

This file now covers **two** snapshots:

| Snapshot | Builds | Section |
|---|---|---|
| **2026-09-02** | dataset v1.0.0 — the deposited, DOI-bearing version | below |
| **2026-11-10** | dataset v1.1.0 — published on the website only | [The 2026-11-10 inputs](#the-2026-11-10-inputs-dataset-v110) |

## Why this file exists

CCRS is actively updated and portal files can be revised in place. The figures
published here are pinned to the 2026-09-02 snapshot, and there is no guarantee
that re-downloading these URLs later returns the same bytes. If it does not, the
hashes below are how you find out — rather than silently recomputing different
numbers and believing they are these ones.

## The eight files

The first six build the 2023–2025 tables. `crashes_2026.csv` builds the labelled
partial-year table, and the ingest **will not run without it** — it is read
twice, once to find the newest reported month and once to build the partial
table. It was left out of the first version of this file, which said the 2026
exports "are not inputs to anything published here". That was wrong, and it was
found by restoring from the archive and watching the ingest fail, which is why
the test is a restore rather than an upload receipt. `parties_2026.csv` is not
read today; it is archived with the rest so the same snapshot stays complete.

| File | Bytes | SHA-256 |
|---|---|---|
| `crashes_2023.csv` | 193,732,146 | `2ea5e8195556e620388976a4a4b8f6a9972438e8015d473790bc946c3d56544d` |
| `parties_2023.csv` | 211,652,130 | `b47c360fc68c339b838137d926196a268cba1390f65345a88051705b646f4ff1` |
| `crashes_2024.csv` | 197,631,820 | `2106c3afc267042b9982d7dd3415c46e1a3a16d8018255c9b42e5da1d82be47c` |
| `parties_2024.csv` | 217,102,627 | `f704de9f2748e88e337670deb969d103d2ef92c646cf616e780bf48f5b0f225a` |
| `crashes_2025.csv` | 187,075,855 | `0ba9c4ec95295bf3e3abb52889834115053ea40d9bf29d09d9c64532a9e0a3c6` |
| `parties_2025.csv` | 210,730,895 | `1e8b844f9ebc196a5be6f456eb83870e95ed95c25099acda57138a66ee98536e` |
| `crashes_2026.csv` | 112,339,158 | `05ec683b3b04e3ad73e076d7ea67c3f8bb07addf09b02677eb4209d539434dbd` |
| `parties_2026.csv` | 124,778,355 | `499cd57a1af2613c341bcf503dcce239adf6c45803146754b6b2e1fb7d2d3a2e` |

Total: 1,455,042,986 bytes.

**The six 2023–2025 byte counts match those published on
<https://slicknicklaw.com/california-crash-data/methodology/>.** The 2026 exports
have no published byte count to check against; their hashes were computed on
2026-09-09 from the same retained copies. The SHA-256
values were computed on 2026-09-09 from the retained local copies; they were not
recorded at download time, so they attest that the copies used to build the
published tables are unchanged since 2026-09-09, and are corroborated back to
retrieval by the matching byte counts.

## Download URLs

Stable CKAN resource URLs, read from the portal's own API
(`/api/3/action/package_show?id=ccrs`) rather than transcribed:

- `crashes_2023.csv` — <https://data.ca.gov/dataset/80c6a49d-c6b3-40ba-86d8-379c9741b4be/resource/436642c0-cd04-4a4c-b45e-564b66437476/download/crashes_2023.csv>
- `parties_2023.csv` — <https://data.ca.gov/dataset/80c6a49d-c6b3-40ba-86d8-379c9741b4be/resource/84376be5-548b-44e3-8ebc-73e8a2ca9945/download/parties_2023.csv>
- `crashes_2024.csv` — <https://data.ca.gov/dataset/80c6a49d-c6b3-40ba-86d8-379c9741b4be/resource/f775df59-b89b-4f82-bd3d-8807fa3a22a0/download/crashes_2024.csv>
- `parties_2024.csv` — <https://data.ca.gov/dataset/80c6a49d-c6b3-40ba-86d8-379c9741b4be/resource/93892d36-017b-4a2a-bc0b-f1f385060b96/download/parties_2024.csv>
- `crashes_2025.csv` — <https://data.ca.gov/dataset/80c6a49d-c6b3-40ba-86d8-379c9741b4be/resource/9f4fc839-122d-4595-a146-43bc4ed16f46/download/crashes_2025.csv>
- `parties_2025.csv` — <https://data.ca.gov/dataset/80c6a49d-c6b3-40ba-86d8-379c9741b4be/resource/a2676918-a825-4b77-8e5c-6eadb38d6b1a/download/parties_2025.csv> — **dead. The portal withdrew this resource between 2026-09-02 and 2026-11-10** (it lists Parties files for 2016–2024 and 2026, and no 2025). The R2 object below is the only copy.
- `crashes_2026.csv` — <https://data.ca.gov/dataset/80c6a49d-c6b3-40ba-86d8-379c9741b4be/resource/b8ce0ca4-b4e9-490d-b4d1-1f4ec48cbefb/download/crashes_2026.csv>
- `parties_2026.csv` — <https://data.ca.gov/dataset/80c6a49d-c6b3-40ba-86d8-379c9741b4be/resource/348a4266-bbb6-439f-b6c7-0018cc79f0fe/download/parties_2026.csv>

Dataset landing page: <https://data.ca.gov/dataset/ccrs>

## The 2026-11-10 inputs (dataset v1.1.0)

Retrieved **2026-11-10**, after the portal re-published the whole dataset. These
build the figures the website serves as **v1.1.0**. That version is published on
the website only: the Zenodo deposit and this repository both still stand at
v1.0.0, so nothing citable rests on the table below.

Hashes computed **2026-11-11** from the retained copies, the same way the
2026-09-02 hashes were.

| File | Bytes | SHA-256 |
|---|---|---|
| `crashes_2023.csv` | 193,737,155 | `0e67a9fc04d29d9a87f57fb82824818a1223947f02dad086b22ec8166ef4712c` |
| `parties_2023.csv` | 211,657,913 | `864f973903d58724d14c4b967c262617bae6a2875e37c5120dc5a1106c122cf1` |
| `crashes_2024.csv` | 197,642,616 | `8203579b71a2e9e7c6f66456918a8f0dc3611205c6700c70095921c111882a46` |
| `parties_2024.csv` | 217,114,243 | `8239314d79bebe9c0af9c4cfadfc00203505e4e3ba923480f7fdc15df3fc5ceb` |
| `crashes_2025.csv` | 187,448,672 | `b1af8624fea1a49c64f5e706ed427871e89083306288aa7513d9a6a300aa8861` |
| `parties_2025.csv` | 210,730,895 | `1e8b844f9ebc196a5be6f456eb83870e95ed95c25099acda57138a66ee98536e` |
| `crashes_2026.csv` | 149,967,505 | `041638a87e758f90593d3519c6fc3439e77314c03e4284100863774a4faeff30` |

Total: 1,368,298,999 bytes. `parties_2026.csv` was not retrieved; it is not read.

**This is a mixed snapshot, and the mix is the important part.** Six files are
from the 2026-11-10 re-publish. `parties_2025.csv` is **not** — the portal had
withdrawn it, so it was taken from the 2026-09-02 R2 archive. Its SHA-256 above
is `1e8b844f…ee98536e`, **identical to the 2026-09-02 row**, so the file v1.1.0
was built from is byte-for-byte the file v1.0.0 was built from. That is a
verified restore of a file that no longer exists upstream, not an assumption
from matching lengths. It matters beyond bookkeeping: `motorcycle` is defined
from the Parties file (`Vehicle1TypeDesc === "Motorcycle"`), so without this
object the 2025 motorcycle counts cannot be rebuilt by anyone, including us.

### These files are not archived

**The 2026-11-10 exports exist in one place: `../slicknick-ccrs-2026-11-10/` on
one machine.** `ccrs/2026-11-10/` does not exist in R2 — checked on 2026-11-11
against a working control read of `ccrs/2026-09-02/crashes_2023.csv`, which
returned data where the 2026-11-10 key returned "The specified key does not
exist." TECH-79 created the archive precisely because "the snapshot the site's
numbers are pinned to may not survive at the source," and it did not survive:
`parties_2025` is gone and `crashes_2025` had already moved again by
2026-11-11. The same exposure now applies to v1.1.0 with no archive behind it.

### The URLs did not change

Every resource ID in the Download URLs above still matches the portal API as of
2026-11-11, and the retrieval's own `ccrs-manifest.tsv` recorded the same IDs on
2026-11-10. The API now advertises `publish.data.ca.gov` where this file records
`data.ca.gov`; both return `302` to the same R2 object, so the list is left as
written. The single exception is `parties_2025.csv`, dead because the resource
itself was withdrawn — not because its URL went stale.

## Verifying a copy

```sh
sha256sum crashes_2023.csv parties_2023.csv crashes_2024.csv \
          parties_2024.csv crashes_2025.csv parties_2025.csv \
          crashes_2026.csv parties_2026.csv
```

Compare against the table above. A mismatch means the portal file changed, not
that your download is broken — check the byte count first.

## Archive

Archived 2026-09-09 to Cloudflare R2 under the firm account. **Private bucket** —
these are large copies of files the State publishes, kept against the State
revising them, not a second public distribution. The public copies are the
portal URLs above.

| | |
|---|---|
| Bucket | `slicknick-ccrs-archive` |
| Prefix | `ccrs/2026-09-02/` |

Objects: `crashes_2023.csv`, `parties_2023.csv`, `crashes_2024.csv`,
`parties_2024.csv`, `crashes_2025.csv`, `parties_2025.csv`, `crashes_2026.csv`,
`parties_2026.csv`, and a copy of this manifest.

Every object has been downloaded from R2 and hashed. All eight match the table
above, and the ingest run from those downloaded copies reproduces
`public/data/california-crash-data.csv` byte for byte. That is a restore, not a
round trip and not an upload receipt.

Retrieve one with:

```sh
npx wrangler r2 object get slicknick-ccrs-archive/ccrs/2026-09-02/crashes_2023.csv   --remote --pipe > crashes_2023.csv
```

`--remote` is not optional. Without it wrangler reads and writes a local
simulator, which reports "Upload complete" for a file that never left the
machine — that happened once on the way to writing this line.

## A note on scope

The retained local copies also include 2021 and 2022 exports. They are not
listed above because they are not inputs to anything published here: the
complete-year tables cover 2023 to 2025.

The 2026 exports are listed, because they are. An earlier version of this
section grouped them with 2021 and 2022 and said none of the three was an input.
`crashes_2026.csv` is one, and leaving it out of the archive made the archive
unrestorable — the ingest exits on the missing file before it writes anything.
