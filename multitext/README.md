# A Shahnameh multitext — prototype

A parallel-text reader for one passage of the *Shahnameh*: six printed editions, a Tajik
transliteration in Latin script, and four translations in one table.

The passage is **Pizzi's reading 1 — Hushang**, 68 couplets in Pizzi's count, from
`خجسته سیامک یکی پور داشت` to `نه نیز آشکارا نمایدت چهر` — the death of Kayumars, the
killing of the Black Div, the discovery of iron and fire, and the founding of Sadeh.

Each row is one couplet. Where an edition lacks that couplet the cell is hatched and
empty, so an absence reads as loudly as a text does: **76 distinct couplets** across the
six editions, **38 rows** with a gap, **43 rows** differing in wording, **8 couplets** in
one edition only. A hatched cell that names another row is a transposition, not an
absence — the couplet is there, a few rows away.

## The pages

    shahnameh-reader-sample.html    translations as columns, beside the Persian
    shahnameh-reader-sample2.html   translations as bands, between the couplet rows
    images/                         11 manuscript leaves from Ganjoor, shared by both
    texts/                          the transcriptions, Rückert's German, and the
                                    treebank annotation

The two pages are generated from one source and are identical except in how the
translations are presented. Open either in a browser: no build step, no server, no
dependencies beyond three webfonts (Noto Naskh Arabic, Spectral, IBM Plex Sans).

## Orthography

The older printings join what the modern editions separate (`وجنگ‌را`, `بنزد`), write the
classic contractions (`ترا` for `تو را`), and mark ezafe three different ways. None of
that is a variant reading, so comparison folds all of it away — spacing, ZWNJ, tatweel,
harakat, ezafe, letterforms, contractions — which takes the marks from 627 to **193**.

**The text on screen is normalised**: each column is rewritten into one spelling, always
one that another edition *in the same row* actually prints, never one invented here. 33 of
the 76 rows then show no variation at all — 25 of them attested in more than one edition,
the other 8 being the couplets only one edition carries.

The diplomatic text, exactly as each edition prints it, is in `texts/01-pizzi.txt` …
`texts/06-ganjoor-moscow.txt`. It is also still carried in the pages' markup, hidden.
Cite the transcriptions, not the screen.

## A caution on the text

Pizzi and Moscow/Ganjoor are existing digital transcriptions and the transliteration is
from this repository. **Vullers, Mohl, Macan and Khaleghi were read off the scans by model
vision OCR and are not yet verified** — a working text, not a citable edition. One strong
check has passed: Vullers prints his own apparatus of what Mohl and Macan read, and every
one of those twenty-seven notes is reproduced by transcriptions made independently from
the scans.

The three prose translations are placed by section, and within a section by proportion of
length. Section boundaries are exact; placement inside a section is approximate. Do not
cite a Pizzi, Warner or Mohl cell as the rendering of the couplet beside it.

**Rückert is different.** His German is verse, one couplet for one couplet, and his
marginal numbers are Vullers' numbers — Sage I 54–74 and Sage II 1–46, exactly the range
`texts/02-vullers.txt` carries. Every German couplet was therefore matched to its row
through the Vullers column, and the German cell *is* the rendering of the couplet beside
it. Nine rows carry no German (r10, r21, r40, r59–r63, r72): those are couplets Vullers,
and so Rückert, does not have — five of them transpositions that appear elsewhere in the
table. Only 67 of the 76 rows are Rückert's to fill.

Only couplets 1–5 carry a Universal Dependencies tree, over Pizzi's text
(`texts/07-ud-pizzi-c1-5.csv`); the remaining 63 have none yet.

## Sources, rights and reuse

**The verse** is Ferdowsi's, and is in the public domain.

**The editions transcribed here:**

| Column | Edition | Pages |
|---|---|---|
| Pizzi | *Manuale della lingua persiana*, 1883 | pp. 58–63 |
| Vullers | *Liber regum*, Leiden 1877–84 | vol. 1, pp. 16–20 |
| Mohl | *Le Livre des Rois*, Persian text | vol. 1, pp. 17–21 |
| Macan | Calcutta, 1829 | vol. 1, pp. 13–16 |
| Khaleghi | Khaleghi-Motlagh | vol. 1, pp. 24–25, 29–31 |
| Moscow | Moscow edition, via [Ganjoor](https://ganjoor.net/) | vol. 1, pp. 31–35 |

Pizzi 1883, Vullers 1877–84, Mohl 1838–78 and Macan 1829 are nineteenth-century and in
the public domain. The Khaleghi-Motlagh text is modern and is quoted here only in the
short extent of this one passage, for comparison.

**The translations** — Pizzi's Italian 1883, Mohl's French 1876 and Rückert's German
(made in the 1830s–40s, printed 1890), all nineteenth-century, and Warner's English 1905 —
are all in the public domain. The Rückert is *Firdosi's Königsbuch (Schahname)*, übersetzt
von Friedrich Rückert, hrsg. von E. A. Bayer, Sage I–XIII (Berlin: Reimer, 1890),
pp. 6–7 and 9–11, from the scan at Universitäts- und Landesbibliothek Sachsen-Anhalt
(urn:nbn:de:gbv:3:5-10886). It is the one translation also held here as a text file,
`texts/08-rueckert-german.txt`, because it collates line by line.

**The transliteration** of the Tajik Cyrillic is original to this project, the same passage
as `shahnameh-transliteration/volumes/shahnameh-vol-1.txt` in this repository. Note that
the text embedded in these pages is the *pre-correction* draft: it still carries the
Cyrillic а/e homoglyphs that have since been cleaned out of the transliteration files.
Take the corrected reading from `shahnameh-transliteration/`, not from these pages.

**The manuscript images** are © their holding institutions. The eleven leaves were taken
from [Ganjoor](https://museum.ganjoor.net/)'s museum pages for
[ganjoor.net/ferdousi/shahname/qmars/sh2](https://ganjoor.net/ferdousi/shahname/qmars/sh2)
and are copied into `images/` and served from this repository, not hotlinked; each caption
names its source and links back to the item. They are included for scholarly
comparison. If you reuse these pages, check the rights with the holding institutions
rather than relying on their presence here.

**The OCR transcriptions** of Vullers, Mohl, Macan and Khaleghi are unverified, and so is
the Rückert, read off a Fraktur scan the same way. Please do not quote any of them as
evidence of what those books print without checking the scan.

---

*This work was prepared with the assistance of Claude Opus 5, run at high reasoning effort.*
