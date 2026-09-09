# A Shahnameh multitext — prototype

A parallel-text reader for one passage of the *Shahnameh*, built to test whether six
printed editions, a transliteration and three nineteenth-century translations can be put
in one table without flattening the differences between them.

The passage is **Pizzi's reading 1 — Hushang**, 68 couplets in Pizzi's count, from
`خجسته سیامک یکی پور داشت` to `نه نیز آشکارا نمایدت چهر`. It covers the death of
Kayumars, the killing of the Black Div, the discovery of iron and fire, and the founding
of the Sadeh festival.

Open `index.html` in a browser. No build step, no server, no dependencies beyond two
webfonts.

---

## Contents

- [What is in the table](#what-is-in-the-table)
- [Using it](#using-it)
- [Orthography is not a variant](#orthography-is-not-a-variant)
- [The treebank](#the-treebank)
- [How the translations are placed](#how-the-translations-are-placed)
- [Where the editions disagree](#where-the-editions-disagree)
- [How far to trust the text](#how-far-to-trust-the-text)
- [Manuscript witnesses](#manuscript-witnesses)
- [How the alignment was made](#how-the-alignment-was-made)
- [Files](#files)
- [Sources, rights and reuse](#sources-rights-and-reuse)

---

## What is in the table

Each row is **one couplet**. Where an edition does not have that couplet the cell is
hatched and empty, so an absence reads as loudly as a text does. The editions genuinely
**do not contain the same poem**: they disagree on which couplets exist, in what order,
and in what words.

| Column | Witness | How the text was got | Pages |
|---|---|---|---|
| **Pizzi** | *Manuale della lingua persiana*, 1883 | existing digital transcription | pp. 58–63 |
| **Vullers** | *Liber regum*, Leiden 1877–84 | model vision OCR from scan | vol. 1, pp. 16–20 |
| **Mohl** | *Le Livre des Rois*, Persian text | model vision OCR from scan | vol. 1, pp. 17–21 |
| **Macan** | Calcutta, 1829 | model vision OCR from scan | vol. 1, pp. 13–16 |
| **Khaleghi** | Khaleghi-Motlagh | model vision OCR from scan | vol. 1, pp. 24–25, 29–31 |
| **Moscow** | Moscow ed., via Ganjoor | born-digital | vol. 1, pp. 31–35 |
| **Transliteration** | Tajik edition, Latin, vocalised | from this repository's text | — |
| **Pizzi (It.)** | Italian, 1883 | running prose | — |
| **Warner (En.)** | English, 1905 | blank verse | — |
| **Mohl (Fr.)** | French, 1876 | running prose | — |

**76 distinct couplets** across the six editions. **38 rows** have at least one gap,
**45 rows** differ in wording, **8 couplets** are in one edition only.

Reading the colours:

| | |
|---|---|
| hatched cell | that edition does not have this couplet |
| highlighted word | this edition's wording differs from the others in the row |
| gold row number | only one edition has this couplet |
| ⇅ | a transposed block — the same couplets, in a different place |
| blue cell | a translation |
| gold-edged band | a dependency tree |

## Using it

**Choose your columns.** Every witness above can be switched on and off independently —
that is the point of the chooser under the toolbar. Ten columns at once is unreadable;
two or three side by side is the working view. *All* and *None* clear or fill the row, and
the choice is remembered in that browser between visits. Translations are columns like any
other, off by default, because the space for them only exists once you have narrowed the
editions.

**The toolbar and the column headings stay put** as you scroll, so you never lose track of
which edition you are looking at. When enough columns are on to need scrolling sideways,
the couplet number stays pinned to the left edge.

**Filters.** *Only rows with a gap* and *only rows that differ* narrow the table to the
rows that carry information; both hide the section headings and the dependency trees.
*Show all* restores everything.

**Treebank** shows or hides the dependency trees under couplets 1–5.

**Whole section in translation**, in each section heading, opens the three translations of
that whole section as continuous prose, unsplit.

## Orthography is not a variant

The older printings join what the modern editions separate (`وجنگ‌را`, `چوبنهاد`, `بنزد`),
write the classic contractions (`ترا` for `تو را`, `مرو را` for `مر او را`), and mark
ezafe three different ways (`چارهٔ`, `چارهء`, `چاره‌ی`). None of that is a variant reading.

Comparison folds all of it away — spacing, ZWNJ, tatweel, harakat, ezafe, letterforms and
the be-/az-/pronoun contractions — which takes the marks from 627 to **193**. What is left
is real.

**The text on screen is normalised**, and only normalised: each column is rewritten into
one spelling, always one that another edition **in the same row** actually prints, never
one invented here. 31 of the 76 rows then read identically across every edition that has
them — which is the point, since those 31 rows are where the editions agree and the old
display made them look as though they did not.

The diplomatic text, exactly as each edition prints it, is not lost. It is in the
transcriptions one directory up (`01-pizzi.txt` … `06-ganjoor-moscow.txt`) and in
`_parsed.json`, and it is still carried in this page's markup, hidden. Anyone wanting the
as-printed reading should go to those files rather than to the screen.

## The treebank

Couplets 1–5 carry a Universal Dependencies annotation — 60 words with lemma, POS,
morphological features, head and relation. It is drawn as arcs above the line, read right
to left like the verse: each arc runs from head to dependent, the root is marked in gold,
and the dashed rule divides the two hemistichs.

The annotation records things a parallel text alone cannot show: `نیایش` in couplet 4 is
one written word but two syntactic ones (*niyā* + *-yaš*), and couplet 3 is a verbless
clause whose copula is elided. Only these five couplets are annotated so far; the
remaining 71 rows have no tree yet.

## How the translations are placed

Pizzi's Italian and Mohl's French are continuous prose and Warner's English is blank
verse, so none of them divides into couplets. Each is split into sentences and anchored
inside its own section, whose boundaries are firm: all three translators break exactly
where the Persian does.

Within a section a sentence is placed by proportion of length, refined for Pizzi by two
verified anchors (*quaranta giri annui di sole* at the accession, *Sadeh* at the
festival). So the section boundaries are exact and the placement inside a section is
**approximate** — close enough to read side by side, not a couplet-level claim. Do not
cite a translation cell as the rendering of the couplet beside it.

A faint, empty translation cell means the prose did not break at that couplet, not that
the translator omitted anything. For the unsplit prose, open *Whole section in
translation* in the section heading.

## Where the editions disagree

### Why Pizzi has 68 couplets and Vullers 67

At row 72 Pizzi prints a couplet Vullers keeps only in a footnote as an addition of the
Calcutta text: `چهل سال با شادکامی و ناز / بداد و دهش بود آن سرفراز`. It is in Macan and
nowhere else here — the whole difference between the two counts.

### Khaleghi expels the Sadeh festival

Rows 43–58, the entire `گفتار اندر نهادن جشن سده`, stand in the main text of every edition
here except Khaleghi-Motlagh, who prints all of it in the apparatus of vol. 1 p. 30 as a
rejected recension. Hence his 45 couplets. It is the largest single block difference in
the passage.

### Moscow moves the ironworking passage

Rows 32–36 and 59–63 are the same five couplets in two places: Pizzi, Vullers, Mohl and
Macan put ironworking and irrigation *before* the Sadeh story, Moscow and Ganjoor *after*,
as their own section ۳.

The Tajik transliteration is Moscow-family but does **not** follow Moscow here: it keeps
the block in the vulgate position and carries the vulgate wording *kujā z-ū tabar* against
Moscow's `از آهنگری اره و تیشه کرد`. Rows 59–63 are therefore blank in its column.

## How far to trust the text

Pizzi and Moscow/Ganjoor are existing digital transcriptions; the transliteration is from
this repository. **Vullers, Mohl, Macan and Khaleghi were read off the scans by model
vision OCR and are not yet verified.** Treat them as a working text, not as a citable
edition.

One strong check passed. Vullers prints his own apparatus recording what Mohl (P.) and
Macan (C.) read. Mohl and Macan were transcribed here from their own scans *without*
consulting that apparatus, and every one of Vullers' roughly twenty notes for these five
pages is reproduced by the independent transcriptions — about twenty independent points of
agreement.

Four readings first transcribed as uncertain have since been checked against the scans by
Farnoosh and corrected: Mohl `نیایش` (twice, not `نمایش`) and `کَیی` (not `کنی`), and
Macan `باج`, confirmed as printed. No uncertain readings are left flagged.

Confidence, file by file, is set out in `00-README.md` one directory up, along with the
printed-page ↔ PDF-page concordances and the evidence that Ganjoor's text for this passage
is the Moscow edition.

## Manuscript witnesses

Below the table are the twelve images Ganjoor attaches to this passage
([ganjoor.net/ferdousi/shahname/qmars/sh2](https://ganjoor.net/ferdousi/shahname/qmars/sh2)).
The first is not a manuscript but the Moscow printed page underlying the Ganjoor text —
Moscow vol. 1, pdf page 32 = printed p. 31, exactly where this reading begins. The rest
are manuscript leaves, several illustrating the moment Hushang kills the Black Div.

## How the alignment was made

A progressive Needleman–Wunsch over normalised couplets — Pizzi first, then Vullers, Mohl,
Macan, Khaleghi, Ganjoor. A couplet shares a row only where the editions genuinely
correspond; absences become hatched cells; transposed blocks keep separate rows,
cross-linked with ⇅. The transliteration is aligned to the Persian hemistich by hemistich
on a consonant skeleton.

## Files

    index.html      the viewer — one self-contained page
    images/         12 gallery images from Ganjoor
    README.md       this file

The working data behind the page — the per-edition couplets, the 76 aligned slots, the
transposition pairs, the transliteration alignment and the treebank — is not in this
repository. It sits with the transcriptions in the project's own archive, documented by
`00-README.md` there.

## Sources, rights and reuse

**The verse** is Ferdowsi's, and is in the public domain.

**The printed editions** transcribed here — Pizzi 1883, Vullers 1877–84, Mohl, Macan 1829
— are nineteenth-century and in the public domain. The Khaleghi-Motlagh text is modern and
is quoted here only in the short extent of this one passage, for comparison.

**The translations** — Pizzi's Italian 1883, Warner's English 1905, Mohl's French 1876 —
are all in the public domain.

**The transliteration** of the Tajik Cyrillic is original to this project and is the same
text as `Shahnameh part 1.txt` in this repository.

**The manuscript images** are © their holding institutions and are served by
[Ganjoor](https://museum.ganjoor.net/); each caption names its source and links to the
item. They are included here for scholarly comparison. If you reuse this page, check the
rights on those images with the holding institutions rather than relying on their presence
here.

**The OCR transcriptions** of Vullers, Mohl, Macan and Khaleghi are unverified. Please do
not quote them as evidence of what those editions print without checking the scan.
