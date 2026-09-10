# Shahnameh — Tajik Cyrillic transliterated into Latin script

A Latin-script transliteration of Ferdowsi's _Shahnameh_, made from the Tajik
Cyrillic edition published in Dushanbe.

The Tajik edition was OCR'd — Cyrillic OCRs comparatively well — and the result
was transliterated by hand following the scheme in
[transliteration-guide.md](transliteration-guide.md).

## Contents

| Path                                        | What it is                                    | Words        |
| ------------------------------------------- | --------------------------------------------- | ------------ |
| `complete/shahnameh-complete.txt`           | Introduction and all six volumes in one file  | 76,469       |
| `complete/introduction.txt`                 | The editors' introduction on its own          | 4,791        |
| `volumes/shahnameh-vol-1.txt` … `vol-6.txt` | The six volumes separately                    | 71,017 total |
| `volumes/shahnameh-vols-1-6-combined.txt`   | The six volumes concatenated, no introduction | 71,017       |
| `transliteration-guide.md`                  | The full Cyrillic → Latin scheme              | —            |

**The numbered files are volumes of the Tajik edition, not divisions of the
poem.** It is not the complete _Shahnameh_, but most of it, issued
across several volumes — so this transliteration covers what those volumes
cover, and no more.

`complete/shahnameh-complete.txt` is the fullest single file. The volume files
are kept because they preserve the volume boundaries, which the combined file
does not.

`volumes/shahnameh-vols-1-6-combined.txt` is the same text as the six volume
files concatenated, word for word; it differs only in where lines are wrapped.
It is kept for convenience, not because it adds anything.

## Transliteration scheme

The full table, set against the established romanisation schemes it was checked
against, is in [transliteration-guide.md](transliteration-guide.md). In brief:

|           |       |           |       |       |       |        |        |       |
| --------- | ----- | --------- | ----- | ----- | ----- | ------ | ------ | ----- |
| а → a     | б → b | в → v     | г → g | ғ → ġ | д → d | е → e  | ё → ýā | ж → ž |
| з → z     | и → i | ӣ → ī     | й → y | к → k | қ → q | л → l  | м → m  | н → n |
| о → ā     | п → p | р → r     | с → s | т → t | у → u | ӯ → ū  | ф → f  | х → x |
| ҳ → ḥ / h | ч → č | ҷ → ĵ / j | ш → š | ъ → ' | э → ė | ю → ýu | я → ýa |       |

Two points that surprise people:

**о → ā but а → a.** Tajik о is /ɔː/, corresponding to Persian long ā; Tajik а
is /æ/, the short vowel. So `осори` becomes `āsāri`, not `osori`.

**ҳ and ҷ are written two ways.** `complete/shahnameh-complete.txt` uses `ḥ` and
`ĵ`, the settled convention. Every other file uses plain `h` and `j`. This is a
real inconsistency between two rounds of work, and the files have deliberately
not been merged — see below.

## Two conventions, not merged

| Files                             | ҳ   | ҷ   | ӣ   |
| --------------------------------- | --- | --- | --- |
| `complete/shahnameh-complete.txt` | `ḥ` | `ĵ` | `ī` |
| everything else                   | `h` | `j` | `ī` |

Note that `complete/introduction.txt` is _not_ in the same convention as
`complete/shahnameh-complete.txt`, even though the complete file contains that
introduction. They were transliterated in different rounds.

If you need one consistent convention across the whole corpus, convert in the
direction you want rather than assuming it has been done:

```bash
# plain h/j  ->  ḥ/ĵ
perl -CSD -Mutf8 -pe 'tr/hj/ḥĵ/' volumes/shahnameh-vol-1.txt
```

This is safe in both directions. Because /ʃ/ /tʃ/ /ʒ/ /χ/ are written `š` `č`
`ž` `x`, the letter `h` is never part of a digraph — every `h` in these files is
ҳ. Sequences that look like digraphs are a consonant plus the plural suffix ҳо:
`baythāi` = байтҳои, `rūzhā` = рӯзҳо.

## Encoding and known issues

All files are UTF-8 without BOM, with LF line endings and no trailing CR.

**Twenty Cyrillic characters remain** — `ы` (12), `ц` (4), `щ` (4) — inside a
Russian-language bibliographic footnote citing Nushin in _Народы Азии и Африки_
(1962). The scheme covers the Tajik alphabet only, so romanising Russian is a
separate decision that has not been made. It is the same footnote in both files:
`complete/introduction.txt` lines 89 and 95, `complete/shahnameh-complete.txt`
lines 90 and 96. Everything else is free of Cyrillic.

**Capitalisation is inconsistent.** The text is otherwise lowercase throughout,
including proper names — `rustam`, `firdavsī`, `kayqubād` — but words beginning
with а/қ/ғ carry a capital in some places and not others, because the Cyrillic
source capitalised them and the transliteration preserved that. Across the six
volumes `az` appears 1,732 times and `Az` 259 times; `andar` 209 times and
`Andar` 8. Genuine proper names in the same position, such as `Afrāsiýāb` and
`Aynī`, are capitalised consistently and correctly.

This has not been normalised, because doing it properly means separating names
from function words rather than lowercasing everything. **Fold case when
searching or matching against these files.**

## Provenance and cleanup

The files as first transliterated mixed Cyrillic and Latin characters that look
identical on screen — Cyrillic `а` beside Latin `a` — so the text read correctly
but would not search, sort or collate. That has been corrected, along with a
second defect that left stray capitals inside words (`xirAd`, `payĠAmbar`).

The correction pass ran over the whole transliteration corpus, of which the nine
files here are the Shahnameh part, and converted 226,976 characters in all. Most
were the homoglyphs — Cyrillic а, А and е — and the rest were ї, ӯ, Ӯ, ќ, Ќ, ѓ,
Ѓ, п and П, standing for Tajik ӣ, ӯ, қ, ғ and п and simply never converted.

`ќ`, `ѓ` and `ї` are not Tajik letters at all: they are Macedonian and
Ukrainian characters left by font and codepage substitution, and the
surrounding words identify each one — `xаlќ` is халқ, `bāliѓ` is болиғ, `Аynї`
is Айнӣ. The soft sign `ь`, which the scheme does not use, was dropped where
it stood before `ý`: `bisьýār` → `bisýār`.

A second pass cleared the stray capitals: `xirAd` → `xirad`, `āĠāzi` → `āġāzi`,
`payĠAmbar` → `payġambar`. Two Roman numerals that had lost the capital on their
leading X, `xV` and `xIII`, were restored.

Nothing else was touched — no spelling normalised, no reading emended, no line
re-broken. Byte counts before and after the capital fixes are identical in every
file, which is the check that only case changed. The unmodified originals are
kept outside this repository, so every change can be diffed and reversed.

---

*This work was prepared with the assistance of Claude Opus 5, run at high reasoning effort.*
