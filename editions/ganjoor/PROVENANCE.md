# ganjoor/ — provenance

Persian text of the Shahnameh, exported from [Ganjoor](https://ganjoor.net) via the
public data repository [ganjoor/ganjoor-data](https://github.com/ganjoor/ganjoor-data).

| | |
|---|---|
| Upstream repo | `https://github.com/ganjoor/ganjoor-data` |
| Upstream path | `poets/ferdousi/shahname` (+ `poets/ferdousi/poet.json`, `_cat.json`) |
| Commit | `1afaf46d311d6c6fa953aa7b87f5c6515dc807a6` (branch `main`) |
| Upstream generated | 2026-09-01T05:06:57Z (`SchemaVersion` 1) |
| Copied | 9 September 2026 |
| Method | `git clone --filter=blob:none --sparse` — see "Re-syncing" below |

## Contents

| | |
|---|---|
| Section folders (`_cat.json`) | 62 |
| Poem files | 777 |
| Verse lines | 99,220 (~49,610 couplets) |
| Distinct metres reported | 1 — فعولن فعولن فعولن فعل (متقارب مثمن محذوف) |
| Size | 74 MB |

The single-metre result is an integrity check: every one of the 777 files is in the
Shahnameh metre, so nothing from another work was pulled in by mistake.

## Path mapping

The upstream `poets/ferdousi/` prefix is dropped; everything below it is unchanged.
So `ganjoor/shahname/aghaz/sh1.json` is upstream `poets/ferdousi/shahname/aghaz/sh1.json`,
and the path also mirrors the public URL — `ganjoor.net/ferdousi/shahname/aghaz/sh1`.
Path is provenance here, so there is no per-file manifest as there is for the
`gregorycrane` files.

## Poem JSON fields

`Id`, `CatId`, `Title`, `FullTitle`, `FullUrl`, `SourceName`, `SourceUrlSlug`,
`PoemSummary`, `Metre` (`Id`, `Rhythm`), `Sections[]`, `Verses[]`.

- `Verses[]` — `VOrder`, `Position`, `Text`, `CoupletIndex`, `SectionIndex1/2`. This is
  the text itself, hemistich per entry.
- `Sections[]` — `Index`, `Number`, `SectionType`, `VerseType`, `RhymeLetters`,
  `PlainText`, `HtmlText`, `PoemFormat`, `CoupletsCount`.
- `SourceName` is ویکی‌درج (wikidorj) throughout — Ganjoor's own wiki-edited text, not a
  named print edition. Treat it as a digital recension, not as Khaleghi-Motlagh, Moscow
  or any other critical edition. Which manuscript readings it follows is not recorded
  per-verse, so it cannot be aligned to a print edition on the strength of this metadata
  alone.
- `PoemSummary` — a modern Persian prose paraphrase, present on all 777 poems. **Not
  Ferdowsi.** See the licence note below before publishing anything derived from it.

## Licensing

`ganjoor-data` carries **no LICENSE file** (repo root holds only `README.md`, `API.md`,
`manifest.json`, `index/`, `poets/`).

- The **verse** is Ferdowsi, c. 1010 CE — public domain everywhere, no permission needed.
- The **`PoemSummary` prose** is modern, authored, and covered by no grant of rights we
  have. It is the part that needs permission before republication. If it is not needed,
  stripping the field leaves an unambiguously public-domain text.

Same posture as the `gregorycrane` files: local working copy, not published.

## Re-syncing

```
git clone --filter=blob:none --no-checkout --depth 1 \
    https://github.com/ganjoor/ganjoor-data.git /tmp/gd
cd /tmp/gd
git sparse-checkout set --no-cone poets/ferdousi/shahname \
    poets/ferdousi/poet.json poets/ferdousi/_cat.json API.md manifest.json
git checkout
```

Then replace `shahname/` from `/tmp/gd/poets/ferdousi/shahname` and update the commit SHA
above. On Git Bash, prefix `git sparse-checkout` with `MSYS_NO_PATHCONV=1` if you use
leading-slash patterns, or MSYS rewrites `/poets/...` into a `C:/Program Files/Git/...`
path and silently matches nothing.

## Also here

- `upstream-API.md`, `upstream-manifest.json` — copied from the repo root, so the schema
  and endpoint documentation stays with the data.
