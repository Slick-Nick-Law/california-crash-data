# Source manifest — the raw CCRS exports

The county table in this repository is derived from six raw CCRS exports. They
are far too large to commit (about 1.22 GB together), so this manifest records
what they are precisely enough that a copy can be **verified**, not merely
obtained.

Retrieved **2026-09-02** from the California Open Data Portal.

## Why this file exists

CCRS is actively updated and portal files can be revised in place. The figures
published here are pinned to the 2026-09-02 snapshot, and there is no guarantee
that re-downloading these URLs later returns the same bytes. If it does not, the
hashes below are how you find out — rather than silently recomputing different
numbers and believing they are these ones.

## The six files

| File | Bytes | SHA-256 |
|---|---|---|
| `crashes_2023.csv` | 193,732,146 | `2ea5e8195556e620388976a4a4b8f6a9972438e8015d473790bc946c3d56544d` |
| `parties_2023.csv` | 211,652,130 | `b47c360fc68c339b838137d926196a268cba1390f65345a88051705b646f4ff1` |
| `crashes_2024.csv` | 197,631,820 | `2106c3afc267042b9982d7dd3415c46e1a3a16d8018255c9b42e5da1d82be47c` |
| `parties_2024.csv` | 217,102,627 | `f704de9f2748e88e337670deb969d103d2ef92c646cf616e780bf48f5b0f225a` |
| `crashes_2025.csv` | 187,075,855 | `0ba9c4ec95295bf3e3abb52889834115053ea40d9bf29d09d9c64532a9e0a3c6` |
| `parties_2025.csv` | 210,730,895 | `1e8b844f9ebc196a5be6f456eb83870e95ed95c25099acda57138a66ee98536e` |

Total: 1,217,925,473 bytes.

**Byte counts match those published on
<https://slicknicklaw.com/california-crash-data/methodology/>.** The SHA-256
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
- `parties_2025.csv` — <https://data.ca.gov/dataset/80c6a49d-c6b3-40ba-86d8-379c9741b4be/resource/a2676918-a825-4b77-8e5c-6eadb38d6b1a/download/parties_2025.csv>

Dataset landing page: <https://data.ca.gov/dataset/ccrs>

## Verifying a copy

```sh
sha256sum crashes_2023.csv parties_2023.csv crashes_2024.csv \
          parties_2024.csv crashes_2025.csv parties_2025.csv
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
`parties_2024.csv`, `crashes_2025.csv`, `parties_2025.csv`, and a copy of this
manifest.

Every object was read back after upload and its length compared against the
byte counts in the table above. All six match. That is a round trip, not an
upload receipt.

Retrieve one with:

```sh
npx wrangler r2 object get slicknick-ccrs-archive/ccrs/2026-09-02/crashes_2023.csv   --remote --pipe > crashes_2023.csv
```

`--remote` is not optional. Without it wrangler reads and writes a local
simulator, which reports "Upload complete" for a file that never left the
machine — that happened once on the way to writing this line.

## A note on scope

The retained local copies also include 2021, 2022 and 2026 exports. They are not
listed above because they are not inputs to anything published here: the
published tables cover 2023 to 2025. The 2026 files exist because the portal
publishes a partial current year.
